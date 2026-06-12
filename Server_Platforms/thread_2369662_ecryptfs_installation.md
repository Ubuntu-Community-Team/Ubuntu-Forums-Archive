---
title: "ecryptfs installation"
date: 2017-08-25
forum: Server Platforms
---

### Post by spectrumknight on 2017-08-25
Hello all,

I have a fresh install of Ubuntu Server 16.04: Linux [myhostname] 4.9.33-mod-std-ipv6-64 #1 SMP Tue Jun 20 11:36:21 CEST 2017 x86_64 x86_64 x86_64 GNU/Linux

I want to install ecryptfs and I have checked the official tutorial here: [https://help.ubuntu.com/lts/serverguide/ecryptfs.html](https://help.ubuntu.com/lts/serverguide/ecryptfs.html)

However I succeed in installing the package "ecryptfs-utils", but I cant use it because the module doesn't seems to be loaded in the kernel: "ERROR:  Cannot get ecryptfs version, ecryptfs kernel module not loaded?" by invoking "ecryptfs-setup-private" 

> user@myhostname:~$ sudo modprobe ecryptfs
modprobe: ERROR: ../libkmod/libkmod.c:586 kmod_search_moddep() could not open moddep file '/lib/modules/4.9.33-mod-std-ipv6-64/modules.dep.bin'
modprobe: FATAL: Module ecryptfs not found in directory /lib/modules/4.9.33-mod-std-ipv6-64


What's wrong? I though that ecryptfs was already included in the kernel, and the tutorial seems to consider that granted. 

I can throw myself in kernel compilation, but honestly I choose Ubuntu server to deploy quickly my server, ans I suppose i am missing something (maybe the installation template from my provider has a special tailored kernel without ecryptfs, lsmod output nothing...)
Any guess ? Thanks.

---

### Post by deadflowr on 2017-08-26
That doesn't seem to be An Ubuntu kernel.
Is this running a Debian kernel?

---

