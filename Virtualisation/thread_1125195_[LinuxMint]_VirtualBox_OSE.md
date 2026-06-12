---
title: "[LinuxMint] VirtualBox OSE"
date: 2009-04-14
forum: Virtualisation
---

### Post by drapsjap on 2009-04-14
I've recently switched from WindowsXP to LinuxMint, and I've never been disappointed. However, I found that some software needs WindowsXP to function properly. Running Windows in a virtualbox seemed like a perfect solution to me. I've tried both, the OSE version and the SUN version, which both gave me the same error. 

Some information about my release:
```
Release 6 (felicia)
Kernel Linux 2.6.27-7-generic
GNOME 2.24.1
```

So, I followed VirtualBox's wizard to create a new vb image. Checked every section of the settings and after enabling the cd-drive and inserting the WindowsXP cd I pressed 'start'. Two error screens pop up:

```
VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```


```
Virtual machine 'Windows XP' has terminated unexpectedly during startup.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}
```

My machine has two hard disks, the image file was saved on the second one. Thinking this might be the problem I've changed to location of the image file to the primary hard disk, and later to an external hard disk. Both resulted in the same error message. Executing the 'vboxdrv setup' file, as suggested in the first error message, didn't help.

I'm not that experienced in using Linux so some fool-proof advice would be greatly appreciated. Thanks in advance! ;)

*I've been using ubuntu 8.10 before, gave me the same errors.*

---

### Post by Seventh Reign on 2009-04-14
Your answer is in your error.

Open a terminal and enter

/etc/init.d/vboxdrv setup

Wait for it to finish and run VB again.

---

### Post by drapsjap on 2009-04-14
As I said in the original post- executing the file didn't help.

---

### Post by pvdvyve on 2009-09-06
> **drapsjap said:**
> As I said in the original post- executing the file didn't help.

You need the sources of your distro. They must be installed. 
if you use a debian based distro as ubuntu or mepis as root do
apt-get install linux-headers-$(uname -r)
and run again
/etc/init.d/vboxdrv setup
Be sure to be listed as vboxuser also.
Than it works, I just had to do it myself and I`m runnin` Simply Mepis.
BTW if you can read, there was a log and it was mentioned. In that log it is clearly noticed that you had to install the kernel sources.
This is where the log should have been:
/var/log/vbox-install.log
Greetings
pvdvyve

---

