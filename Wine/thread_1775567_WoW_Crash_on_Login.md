---
title: "WoW Crash on Login"
date: 2011-06-04
forum: Wine
---

### Post by jbaerboc on 2011-06-04
Hi I have Ubuntu 11.04 and am attempting to run WoW. I am trying to run it the exact same way I did on Linux Mint (latest) and it worked there. I have WoW installed on my windows partition and I run it from there using wine in opengl of course. I have Nvidia 9600GT graphics and GLX rendering reports yes. I get to the WoW login screen and as soon as I type my password and click login it crashes.

Here's the terminal error:
When running with command: wine /media/HP/Documents\ and\ Settings/Public/Games/World\ of\ Warcraft/wow.exe -opengl

wine: Unhandled page fault on read access to 0xffffffff at address 0x7bc64e7e (thread 0009), starting debugger...
Can't attach process 0008: error 5
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x601e25c6
wine client error:9: write: Bad file descriptor


When running with (per another thread's advice) command: LD_PRELOAD=/usr/lib32/nvidia-current/libGL.so wine /media/HP/Documents\ and\ Settings/Public/Games/World\ of\ Warcraft/wow.exe -opengl

fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugObjectHandle
wine: Unhandled page fault on read access to 0xffffffff at address 0x7bc64e7e (thread 0009), starting debugger...
ERROR: ld.so: object '/usr/lib32/nvidia-current/libGL.so' from LD_PRELOAD cannot be preloaded: ignored.
Can't attach process 0008: error 5
Segmentation fault

Never have had this error before so no clue what's up...anyone? Thanks!

[B][COLOR=Red]SOLVED:
[/COLOR][/B][COLOR=Red]Found out that the reason it crashes with this setup (running from windows partition) is that the current version of wine and most Kernels below 2.6.35 have problems with this function. To fix install the latest available kernel for your distro (in my case with PCLOS it was 2.6.38.XX).
[/COLOR]

---

### Post by jbaerboc on 2011-06-10
I ended up moving wow folders to .wine directory and it suddenly worked. Bizzare I had to do this with Ubuntu when in Mint it worked...

---

