# ENS

A minimal Solidity smart contract that maps Ethereum addresses to usernames, a simplified take on how the Ethereum Name Service (ENS) works.

## What it does

Each wallet address can register one username and look it up later.

| Function | Type | Description |
|----------|------|-------------|
| `signUp(string userName)` | write | Saves `userName` for the calling address (`msg.sender`). Calling it again overwrites the previous name. |
| `getUser()` | view | Returns the username stored for the calling address. Returns an empty string if none is set. |

## How it works

- Storage is a single `mapping(address => string) users`.
- The key is always `msg.sender`, so you can only set and read your own entry.
- `getUser()` is a `view` function, so reading costs no gas when called externally.

## Details

- Solidity version: `0.8.26`
- License: MIT
- No constructor logic, no owner, no access control

## Try it in Remix

1. Open [Remix IDE](https://remix.ethereum.org) and create `ENS.sol` with the contract code.
2. Compile with Solidity `0.8.26`.
3. In **Deploy & Run Transactions**, deploy `ENS`.
4. Enter a name next to `signUp` (for example `raman`) and click it.
5. Click `getUser`. It returns `0: string: raman`.

## Limitations

This is a learning example, not a real ENS implementation:

- Names are not unique, so multiple addresses can share the same name.
- There is no reverse lookup (name to address).
- Names can't be transferred or deleted, only overwritten.
- There is no validation on name length or content.
