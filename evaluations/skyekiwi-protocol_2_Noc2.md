# Evaluation

- **Status:** In Progress
- **Application Document:** https://github.com/w3f/Grants-Program/blob/master/applications/skyekiwi-protocol.md
- **Milestone:** 2
* **Kusama Identity:** [HFG4FvoJv8uanizzetS1tPA6wigNAiKuEHKcm1NaKNNDwve](https://polkascan.io/pre/kusama/account/HFG4FvoJv8uanizzetS1tPA6wigNAiKuEHKcm1NaKNNDwve)
* **Previously successfully merged evaluation:** All evaluations by Noc2

| Number | Deliverable | Accepted | Link | Evaluation Notes |
| ------ | ----------- | :------: | ---- |----------------- |
| 0a. | License | <ul><li>[x] </li></ul> | [GPLv3.0](https://github.com/skyekiwi/skyekiwi-network/blob/master/LICENSE) | GPLv3.0 instead of Apache 2.0, which is fine  |
| 0b. | Documentation       | <ul><li>[ ] </li></ul> | [skw-blockchain-pallets](https://github.com/skyekiwi/skyekiwi-network/tree/master/crates/skw-blockchain-pallets/pallet-secrets) | Code has inline documentation, but no "basic tutorial that explains how a user can integrate the SkyeKiwi Protocol into their project." or any other tutorial |
| 0c. | Testing Guide       | <ul><li>[ ] </li></ul> | [testing-guide](https://github.com/skyekiwi/skyekiwi-network#descriptions--build--testing-guide) | Only describes how to run all tests. It would be nice to also have docs/readmes in the subfolders of some of the projects. yarn main:build fails for me because of near-test-contracts v0.0.0  |
| 1. | `pallet-secrets`    | <ul><li>[x] </li></ul> | [skw-blockchain-pallets](https://github.com/skyekiwi/skyekiwi-network/tree/master/crates/skw-blockchain-pallets/pallet-secrets) | Tests work, The implementation changed quite a bit compared to the [contract](https://github.com/skyekiwi/contract-demo/blob/c1118b218b4e597c8373a649f52b131081e09b4a/simple-storage/contracts/lib.rs), but that is fine and in general it looks good |
| 2. | Rust Implementation | <ul><li>[ ] </li></ul> | [enclave](https://github.com/skyekiwi/skyekiwi-network/tree/master/enclave), [skw-sgx-protocol](https://github.com/skyekiwi/skyekiwi-network/tree/master/crates/skw-sgx-protocol) | See error below |


## General Notes


**15.02.22 near-test-contracts v0.0.0 Error using commit d8e84553f924be1ddd5497e252cbea108fb0443a**

<pre><font color="#12488B"><b>skyekiwi-network</b></font>$ yarn main:build
<b>yarn run v1.22.5</b>
<font color="#AAAAAA">$ node ./skw-tools-scripts/main-build.cjs</font>
$ yarn blockchain:build 
$ cargo build --release
<font color="#26A269"><b>    Updating</b></font> git repository `https://github.com/near/nearcore`
<font color="#26A269"><b>   Compiling</b></font> proc-macro2 v1.0.36
<font color="#26A269"><b>   Compiling</b></font> value-bag v1.0.0-alpha.8
<font color="#26A269"><b>   Compiling</b></font> ahash v0.7.6
<font color="#26A269"><b>   Compiling</b></font> indexmap v1.8.0
<font color="#26A269"><b>   Compiling</b></font> near-test-contracts v0.0.0 (/home/david/source/web3/evaluation/skyekiwi/skyekiwi-network/crates/near-test-contracts)
<font color="#26A269"><b>   Compiling</b></font> typenum v1.15.0
<font color="#26A269"><b>   Compiling</b></font> num-traits v0.2.14
<font color="#26A269"><b>   Compiling</b></font> generic-array v0.14.5
<font color="#26A269"><b>   Compiling</b></font> num-integer v0.1.44
<font color="#26A269"><b>   Compiling</b></font> miniz_oxide v0.4.4
<font color="#26A269"><b>   Compiling</b></font> num-bigint v0.2.6
<font color="#26A269"><b>   Compiling</b></font> num-rational v0.2.4
<font color="#26A269"><b>   Compiling</b></font> proc-macro-error-attr v1.0.4
<font color="#26A269"><b>   Compiling</b></font> proc-macro-error v1.0.4
<font color="#26A269"><b>   Compiling</b></font> memoffset v0.6.5
<font color="#26A269"><b>   Compiling</b></font> futures-task v0.3.19
<font color="#26A269"><b>   Compiling</b></font> crunchy v0.2.2
<font color="#C01C28"><b>error</b></font><b>:</b> failed to run custom build command for `near-test-contracts v0.0.0 (/home/david/source/web3/evaluation/skyekiwi/skyekiwi-network/crates/near-test-contracts)`

Caused by:
  process didn&apos;t exit successfully: `/home/david/source/web3/evaluation/skyekiwi/skyekiwi-network/target/release/build/near-test-contracts-ca3efae7a4829362/build-script-build` (exit status: 1)
  --- stderr
     Compiling cfg-if v0.1.9
  error[E0463]: can&apos;t find crate for `core`
    |
    = note: the `wasm32-unknown-unknown` target may not be installed
    = help: consider downloading the target with `rustup target add wasm32-unknown-unknown`
    = help: consider building the standard library from source with `cargo build -Zbuild-std`

  For more information about this error, try `rustc --explain E0463`.
  error: could not compile `cfg-if` due to previous error
  command `&quot;cargo&quot; &quot;build&quot; &quot;--target=wasm32-unknown-unknown&quot; &quot;--release&quot;` exited with non-zero status: ExitStatus(unix_wait_status(25856))
<font color="#A2734C"><b>warning</b></font><b>:</b> build failed, waiting for other jobs to finish...
<font color="#C01C28"><b>error</b></font><b>:</b> build failed
<font color="#C01C28">error</font> Command failed with exit code 255.
<font color="#12488B">info</font> Visit <b>https://yarnpkg.com/en/docs/cli/run</b> for documentation about this command.
<font color="#26A269"><b>david@noc2</b></font>:<font color="#12488B"><b>~/source/web3/evaluation/skyekiwi/skyekiwi-network</b></font>$ 
</pre>
