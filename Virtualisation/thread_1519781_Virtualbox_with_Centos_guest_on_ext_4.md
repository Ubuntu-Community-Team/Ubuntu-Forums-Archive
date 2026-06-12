---
title: "Virtualbox with Centos guest on ext 4"
date: 2010-06-28
forum: Virtualisation
---

### Post by forbzie22 on 2010-06-28
Just installed CentOS 5.5 on ubuntu 10.04 with virtualbox 3.2.6

When booting the VM i get the following error:
It doesnt seem to like the image being on ext4 filesystem. I have enabled host I/O cache but no joy. 

Any ideas ? 


0:00:00.434 Log opened 2010-06-28T21:02:05.500233000Z
00:00:00.434 OS Product: Linux
00:00:00.434 OS Release: 2.6.32-22-generic
00:00:00.434 OS Version: #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010
00:00:00.434 DMI Product Name: Studio 1535                     
00:00:00.434 DMI Product Version: 
00:00:00.435 Host RAM: 3528MB RAM, available: 2882MB
00:00:00.435 Executable: /usr/lib/virtualbox/VirtualBox
00:00:00.435 Process ID: 2456
00:00:00.435 Package type: LINUX_32BITS_UBUNTU_10_04
00:00:00.513 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xfa9bb020 - ModuleInit at 00000000fa9cf5f0 and ModuleTerm at 00000000fa9cf5d0
00:00:00.513 SUP: VMMR0EntryEx located at 00000000fa9cf4b0, VMMR0EntryFast at 00000000fa9ce670 and VMMR0EntryInt at 00000000fa9ce4c0
00:00:00.598 File system of '/home/.VirtualBox/HardDisks/CentOS v5.5.vdi' is ext4
00:00:00.638 VBoxSharedClipboard mode: Bidirectional
00:00:00.644 ************************* CFGM dump *************************

---

### Post by cfhowlett on 2010-08-08
I ignored that message and it loaded and runs fine.

---

