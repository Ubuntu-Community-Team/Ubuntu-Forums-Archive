---
title: "Ubuntu Locking Up"
date: 2008-03-28
forum: Virtualisation
---

### Post by bluewhale on 2008-03-28
I've been trying Ubuntu for the past month here and at home. I find this work system is locking up once in a while: perhaps 2-3 times a week. It FEELS like it occurs because of VMWare Workstation for Linux having a problem, but I'm not sure. 



Mar 28 12:07:36 PaulT kernel: [366608.298167] /dev/vmmon[27333]: host clock rate change request 1043 -> 83
Mar 28 12:23:05 PaulT kernel: [367536.936479] /dev/vmnet: open called by PID 27319 (vmware-vmx)
Mar 28 12:23:05 PaulT kernel: [367536.936504] /dev/vmnet: port on hub 0 successfully opened
Mar 28 12:23:06 PaulT kernel: [367537.742319] vmmon: Had to deallocate locked 53120 pages from vm driver ffff81010b8fe000
Mar 28 12:23:06 PaulT kernel: [367537.752567] vmmon: Had to deallocate AWE 5429 pages from vm driver ffff81010b8fe000
Mar 28 12:30:03 PaulT kernel: Inspecting /boot/System.map-2.6.22-14-generic
Mar 28 12:30:03 PaulT kernel: Loaded 26085 symbols from /boot/System.map-2.6.22-14-generic.
Mar 28 12:30:03 PaulT kernel: Symbols match kernel version 2.6.22.
Mar 28 12:30:03 PaulT kernel: No module symbols loaded - kernel modules not enabled. 
Mar 28 12:30:03 PaulT kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 02:46:46 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Mar 28 12:30:03 PaulT kernel: [    0.000000] Command line: root=UUID=5529d58a-1840-4f8c-baf8-e7a30fdb7683 ro quiet splash
Mar 28 12:30:03 PaulT kernel: [    0.000000] BIOS-provided physical RAM map:


The entry above is from the kernal log just now. The unit locked hard again at about 12:25. Might this info point a finger at the culprit? 


Thanks


Paul

---

### Post by mvan83 on 2008-03-28
If it's a trend that vmmon has a log entry before it locks up, it's probably the culprit. You might try rebuilding those drivers again using:
```
sudo /usr/bin/vmware-config.pl
```

---

### Post by bluewhale on 2008-03-29
Thanks! 

Ran it and will have to see. I'm curious about the questions it asked ( which it asked when first installed ). I didn't grab the exact syntax however it seemed to indicate that the proper files were not present for my kernel, and did I wish to let it try building drivers automatically. 

Is this fairly normal or should a wannabe power user be digging in there myself? 

Second Q If I may: did rebuilding the VMWare drivers possibly affect other software I've installed? Envy comes immediately to mind.

---

### Post by fjgaude on 2008-03-29
Auto building the kernel drivers is normal and doesn't effect anything else, at least it didn't with the many times I have installed and configed vmware server on several machines.

---

### Post by mvan83 on 2008-03-29
> **bluewhale said:**
> Thanks! 

Ran it and will have to see. I'm curious about the questions it asked ( which it asked when first installed ). I didn't grab the exact syntax however it seemed to indicate that the proper files were not present for my kernel, and did I wish to let it try building drivers automatically. 

Is this fairly normal or should a wannabe power user be digging in there myself? 

Second Q If I may: did rebuilding the VMWare drivers possibly affect other software I've installed? Envy comes immediately to mind.

It shouldn't affect anything else (caveat: I also don't think it should've made your system lock up, so there's always a chance something will go wrong ;) ).

I think what you're recalling is that it didn't have any of those kernel modules that could be loaded into the current kernel and it was asking if you would like to build them. This is normal and just sort of a confirmation that you would like that command to build them for you.

Since it said it didn't have loadable modules for the current kernel, that's probably what was causing the lockup. It seems from the kernel log messages that it was using them in some capacity. Whenever you update your kernel (or apt updates it for you), the vmware kernel modules (vmmon and vmnet) must be rebuilt for the current kernel (by running the command I posted previously). It's strange that it apparently was loading the modules into the kernel although they weren't built for that version of the kernel. I'll have to investigate this the next time apt updates my kernel. The vmware program itself is smart enough to know when the modules aren't up to date (and when you attempt to run it, will die and indicate you must run that command to rebuild them), but it appears that the kernel just goes ahead and loads them on boot anyway. This would appear to be vmware's fault. They should build in some sort of check so that outdated modules aren't loaded.

---

### Post by bjdooks on 2011-01-21
I'm finding problems with vmware 7.1.3 on ubuntu 10.10 locking up on an Dell XPS M1530.

Three lockups in the last week, and even worse is that it will not start if the system has both monitors plugged in.

---

