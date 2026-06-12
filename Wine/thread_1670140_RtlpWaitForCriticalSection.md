---
title: "RtlpWaitForCriticalSection"
date: 2011-01-18
forum: Wine
---

### Post by sportfreak2020 on 2011-01-18
Hey guys

Having some issues in running a expert advisor on the metatrader program.

It works awesome in everyway, but after attaching an EA to a trading pair chart, the terminal throws this error:


err:ntddl:RtlpWaitForCriticalSection section 0x7bcb3e04 "loader.c: loader_section" wait timed out in thread 0009, blocked by 0020, retrying (60 sec)


tried googling for "RtlpWaitForCriticalSection" and many other keywork combs. but dint succeed. Could anyone throw some light on that error??

---

### Post by sportfreak2020 on 2011-01-18
Also the details are as follows:

OS: FC13 and/ Ubuntu 10.04

Wine Version:1.3.7 

Tried the clean .wine folder technique as well ;)

---

### Post by sportfreak2020 on 2011-01-19
actually .. i stumbled upon this link via the wine mail lists .. thought it could prove usefull at some point

[http://www.winehq.org/pipermail/wine-users/2007-March/026546.html](http://www.winehq.org/pipermail/wine-users/2007-March/026546.html)

also, i ran a WINEDEBUG command, to see whats going on, it created a file close to 30MB..

some it included this code: lemme know if anyone would want the whole log file ...


> 

3:Ret  ntdll.RtlFreeHeap() retval=00000001 ret=20041827
0013:Call ntdll.RtlFreeHeap(00110000,00000000,0011a238) ret=20041827
0013:Ret  ntdll.RtlFreeHeap() retval=00000001 ret=20041827
0013:Call ntdll.RtlFreeHeap(00110000,00000000,0011a220) ret=20041827
0013:Ret  ntdll.RtlFreeHeap() retval=00000001 ret=20041827
0013:Call ntdll.RtlFreeHeap(00110000,00000000,00000000) ret=2004245d
0013:Ret  ntdll.RtlFreeHeap() retval=00000001 ret=2004245d
0013:Call ntdll.RtlFreeHeap(00110000,00000000,00119018) ret=2004249b
0013:Ret  ntdll.RtlFreeHeap() retval=00000001 ret=2004249b
0013:Ret  rpcrt4.RpcBindingFree() retval=00000000 ret=6825892e
000f:Ret  KERNEL32.ConnectNamedPipe() retval=00000001 ret=68216b8c
000f:Call ntdll.RtlAllocateHeap(00110000,00000000,00000036) ret=68216ca7
000f:Ret  ntdll.RtlAllocateHeap() retval=00118110 ret=68216ca7
000f:Call KERNEL32.WriteFile(00000040,00118110,00000036,0033fd90,00000000) ret=68216da2
000f:Ret  KERNEL32.WriteFile() retval=00000001 ret=68216da2
000f:Call KERNEL32.ReadFile(00000040,0033fd8c,00000004,0033fd90,00000000) ret=68216fda
0013:Call rpcrt4.NdrClientInitializeNew(0043e884,0043e7a4,68274680,00000010) ret=68260d98
0013:Ret  rpcrt4.NdrClientInitializeNew() retval=68256680 ret=68260d98
0013:Call rpcrt4.NDRCContextBinding(00119098) ret=68260db1
0013:Ret  rpcrt4.NDRCContextBinding() retval=0011a368 ret=68260db1
0013:Call rpcrt4.NdrConformantStringBufferSize(0043e7a4,0011a220,6826a3b8) ret=68260ddd
0013:Ret  rpcrt4.NdrConformantStringBufferSize() retval=00000012 ret=68260ddd
0013:Call rpcrt4.NdrGetBuffer(0043e7a4,0000003e,0011a368) ret=68260dfa
0013:Call ntdll.RtlAllocateHeap(00110000,00000000,0000003e) ret=20057637
0013:Ret  ntdll.RtlAllocateHeap() retval=00119018 ret=20057637
0013:Ret  rpcrt4.NdrGetBuffer() retval=00119018 ret=68260dfa
0013:Call rpcrt4.NdrClientContextMarshall(0043e7a4,00119098,00000000) ret=68260e15
0013:Ret  rpcrt4.NdrClientContextMarshall() retval=00000000 ret=68260e15
0013:Call rpcrt4.NdrConformantStringMarshall(0043e7a4,0011a220,6826a3b8) ret=68260e2f
0013:Ret  rpcrt4.NdrConformantStringMarshall() retval=00000000 ret=68260e2f
0013:Call rpcrt4.NdrSendReceive(0043e7a4,00119050) ret=68260e85
0013:Call ntdll.RtlAllocateHeap(00110000,00000008,00000018) ret=20048e3c


---

### Post by sportfreak2020 on 2011-01-19
Just found this. Looks like this issue was fixed with the latest version of Kernel upgrade

[http://bugs.winehq.org/show_bug.cgi?id=19025](http://bugs.winehq.org/show_bug.cgi?id=19025)

Will test it out for ubuntu if updating the distro works :popcorn:

---

### Post by sportfreak2020 on 2011-01-19
Just found this. Looks like this issue was fixed with the latest version of Kernel upgrade

[http://bugs.winehq.org/show_bug.cgi?id=19025](http://bugs.winehq.org/show_bug.cgi?id=19025)

Will test it out for ubuntu if updating the distro works :popcorn:

---

### Post by sportfreak2020 on 2011-01-19
Just found this. Looks like this issue was fixed with the latest version of Kernel upgrade

[http://bugs.winehq.org/show_bug.cgi?id=19025](http://bugs.winehq.org/show_bug.cgi?id=19025)

Will test it out for ubuntu if updating the distro works :popcorn:

---

