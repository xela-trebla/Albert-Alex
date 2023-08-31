### COMMANDS
*Command to run the xfs-interface*
```
cd $HOME/myexpos/xfs-interface/
./xfs-interface
```
*Load Data file (.dat) to Disk*
```
load --data $HOME/myexpos/sample.dat
```
*Copy Disk Block to UNIX*
```
copy 3 4 $HOME/myexpos/inode_table.txt
```
*Copy Inode table and User table to*` cd $HOME/myexpos/xfs-interface/inodeusertable.txt`
```dump --inodeusertable```

*Copy Loaded Files*
 ```
 copy 69 69 $HOME/myexpos/data.txt
 ```
 ```
 export sample.dat $HOME/myexpos/data.txt
 ```
*Load OS Startup Code*
```
load --os $HOME/myexpos/spl/spl_progs/helloworld.xsm
```
**RUN THE MACHINE**
```cd $HOME/myexpos/xsm/
./xsm
```
*Compiling SPL Programs*
```
cd $HOME/myexpos/spl
./spl $HOME/myexpos/spl/spl_progs/oddnos.spl
```
**RUN XSM IN DEBUG MODE**
```
cd $HOME/myexpos/xsm
./xsm --debug
```
##### DEBUG COMMANDS
*View the contents of registers*
```
reg
```
*Write* the contents of mem page 1 to file mem in xsm dir
```
mem 1
```
*Next Step*
```
s
```
*Continue Execution till next BRKP*
```
c
```
**RUNNING A USER PROGRAM**

*Load a program to init/Login code disk block (7-8)*
```
cd $HOME/myexpos/xfs-interface
./xfs-interface
```
```
load --init $HOME/myexpos/expl/expl_progs/squares.xsm
```
Int 10 is responsible for the graceful termination of program
*Load int10 code to disk*
```
load --int=10 ../spl/spl_progs/haltprog.xsm
```
*Load the exception handler code*
```
load --exhandler ../spl/spl_progs/haltprog.xsm
```
*Compile OS startup code*
```
 cd $HOME/myexpos/spl
./spl $HOME/myexpos/spl/spl_progs/os_startup.spl
```
*Loading OS code to disk*
```
cd ../xfs-interface
./xfs-interface
```
```
load --os $HOME/myexpos/spl/spl_progs/os_startup.xsm
```
**RUNNING MACHINE**
```
cd ../xsm
./xsm --debug --timer 0
```
**Incuding ABI and XEXE**
*Library code must be loaded to block 13 and 14  of the disk*
```
load --library ../expl/library.lib
```
*Loading timer to disk. Block 17,18*
```
load --int=timer $HOME/myexpos/spl/spl_progs/sample_timer.xsm
```
*Loading int 7 program to disk*
```
load --int=7 ../spl/spl_progs/sample_int7.xsm
```
*Compiling expl*
```
cd $HOME/myexpos/expl
./expl expl_progs/numbers.expl
```
*Loading idle program*
```
load --idle ../expl/expl_progs/idle_process.xsm
```
*compiling module 7 and loading*
```
 cd $HOME/myexpos/spl
./spl $HOME/myexpos/spl/spl_progs/Boot_module_13.spl
```
```
cd ../xfs-interface
./xfs-interface
```
```
load --module 7 ../spl/spl_progs/Boot_module_13.xsm
```
***Stage 14***

*Load exec file to Disk*
```
load --exec ../expl/expl_progs/even.xsm
```
* even.xsm is in black 69


### Data Structure
[Disk Organisation and Memory Organisation](https://exposnitc.github.io/os_implementation.html)
[Process Table](https://exposnitc.github.io/os_design-files/process_table.html)
[System Status Table](https://exposnitc.github.io/os_design-files/mem_ds.html#ss_table)

**META DATA**
[Node Table , Dist free List, User Table , Root File](https://exposnitc.github.io/os_design-files/disk_ds.html)

[[Page Table]]
[XSM VM MODEL](https://exposnitc.github.io/virtual_machine_spec.html)

[Unprivileged Mode Execution and Address Translation](https://exposnitc.github.io/Tutorials/xsm_unprivileged_tutorial.html)

[ABI](https://exposnitc.github.io/abi.html#xexe)
[OS startup code](https://exposnitc.github.io/os_design-files/misc.html#os_startup)
[Kernal Stack managements during Interrupts](https://exposnitc.github.io/os_design-files/stack_interrupt.html)
[Low level Runtime Library interface](https://exposnitc.github.io/abi.html#collapse5)

[Process States](https://exposnitc.github.io/os_design-files/process_table.html#state)
**Level 13**
[Kernal stack in kernal module calls](https://exposnitc.github.io/os_design-files/stack_module.html)
[Kernal stack during context switching](https://exposnitc.github.io/os_design-files/timer_stack_management.html)
[SPL module calling convetions](https://exposnitc.github.io/support_tools-files/spl.html)



**LANGUAGES**
[XFS](https://exposnitc.github.io/support_tools-files/xfs-interface.html)
[[XSM]]
[SPL](https://exposnitc.github.io/support_tools-files/spl.html)
[[EXPL]]


