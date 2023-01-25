# Ruby Internals Glossary

Just a list of acronyms I've run across in the Ruby source code and their meanings.

| Term | Definition |
| ---  | -----------|
| `cc` | Call Cache.  An inline cache structure for the call site. Stored in the `cd` |
| `cd` | Call Data. A data structure that points at the `ci` and the `cc`.  `iseq` objects points at the `cd`, and access call information and call caches via this structure |
| `cfp`| Control Frame Pointer. Represents a Ruby stack frame.  Calling a method pushes a new frame (cfp), returning pops a frame. Points at  the `pc`, `sp`, `ep`, and the corresponding `iseq`|
| `ci` | Call Information.  Refers to an `rb_callinfo` struct. Contains call information about the call site, including number of parameters to be passed, whether it they are keyword arguments or not, etc. Used in conjunction with the `cc` and `cd`. |
| `ec` | Execution Context. The top level VM context, points at the current `cfp` |
| `ep` | Environment Pointer. Local variables, including method parameters are stored in the `ep` array. The `ep` is pointed to by the `cfp` |
| `iseq` | Instruction Sequence.  Usually "iseq" in the C code will refer to an `rb_iseq_t` object that holds a reference to the actual instruction sequences which are executed by the VM. The object also holds information about the code, like the method name associated with the code. |
| `pc` | Program Counter. Usually the instruction that will be executed _next_ by the VM. Pointed to by the `cfp` and incremented by the VM |
| `sp` | Stack Pointer. The top of the stack. The VM executes instructions in the `iseq` and instructions will push and pop values on the stack. The VM updates the `sp` on the `cfp` to point at the top of the stack|
| `VALUE` | VALUE is a pointer to a ruby object from the Ruby C code. |
| VM   | Virtual Machine. In MRI's case YARV (Yet Another Ruby VM)
| WB | Write Barrier.  To do with GC write barriers |
| WC | Wild Card. As seen in instructions like `getlocal_WC_0`.  It means this instruction takes a "wild card" for the parameter (in this case an index for a local) |
