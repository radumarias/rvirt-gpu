# rvirt-gpu

Virtualization for `GPU` that allows you to run local `GPU` apps and the code is actually ran in the cloud, keeping your data local, without changing your app, at least not much.

> [!WARNING]  
> **This is still under development. Please do not use it with sensitive data for now, please wait for a
stable release.  
> It's mostly ideal for experimental and learning projects.**

# Functionality

- `vGPU` is a `virtualization` layer for a `GPU`
- your local app "runs" on local `vGPU`
- local app decrypts the actual local data and sends the (`CUDA`) instructions to the remote `GPU-Coordinator`
- `GPU-Coordinator` distribute the instructions to multiple real `GPU`s
- then it sends the results back to `vGPU` which sends them to the local app

Three advantages emerge:

- You can execute `AI` models without having a local `GPU`
- Execute on multiple `GPUs`, in the end, for some use cases, it could be faster than running on a local `GPU`
- Execute `ML` models without storing your data on `untrusted` providers. It will keep some blocks in `memory` which are needed for executing current `instructions`. But at least they are `obfuscated` and `protected` by OS not to be easily copied by other `processes` from memory. `Data in transit` is `secured` by `TLS`

# Cons

- I know it will be slow, but in cases where the data flow is small compared to processing time it could be a reasonable compromise for the security it gives you
- Also because the instructions are distributed to multiple `GPUs`, when possible, it could offer a better performance, in some cases, than locally

# Schema

[![schema](website/resources/schema2.png)](website/resources/schema2.png)

# Wiki

[Wiki](https://github.com/radumarias/rgpu/wiki)

# Credits

The main idea is of [Andrei Mărcuţ](https://github.com/andreimarcut).
