# About

This repository contains a simple **dead man's switch** smart contract.

The contract includes:

- A **payable beneficiary address**  
  Stores the address that will receive the funds if the owner is considered “dead”.

- A **`still_alive` function**  
  Updates a state variable with the current block number whenever the owner calls it.

- A **`releaseFunds` function**  
  Checks whether a certain number of blocks have passed since the last `still_alive` call.  
  If enough blocks have passed, it allows the beneficiary to withdraw the funds.

## Possible automation

Currently, the beneficiary must call `releaseFunds` to trigger the transfer once the condition is met.

This could be automated using **Chainlink Keepers** (now Chainlink Automation), which enable event‑driven transactions on-chain.  
With Keepers, the contract could automatically trigger `releaseFunds` when the required number of blocks has passed without a `still_alive` call from the owner.
