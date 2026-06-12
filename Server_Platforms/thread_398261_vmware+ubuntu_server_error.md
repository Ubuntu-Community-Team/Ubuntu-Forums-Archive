---
title: "vmware+ubuntu server error"
date: 2007-03-31
forum: Server Platforms
---

### Post by jmvidalvia on 2007-03-31
I just installed Ubuntu Server 6.1 in my Vmware Server under Xubuntu 6.1.
Everything worked fine, I mean, no error messagges while instalation.
But when I try to start, my cpu reaches 99% and following message appears:
Look at first png, please.
Details of grub are in second png.

Vmware server works fine for XP guest.
Thanks for your help!

---

### Post by elst on 2007-04-01
My first guess is that it is related to the VMware emulated hardware - there may be some incompatibility between a virtual device and the Ubuntu 6.10 drivers. You could try experimenting with the virtual hardware settings, if there aren't any currently known issues. I haven't had any issues myself running Edgy under VMware Workstation, so that is just a guess.

The VMware forums are excellent, so it's well worth doing a search there to see if there has been any discussion of similar issues.

---

### Post by jmvidalvia on 2007-04-01
I googled and found it is not an issue of VMware, but a kernel installer problem.
I just copy-paste from another forum (I am not skilled enough to write this):

"This is because the 2.6.17-10-server kernel is compiled with HIGHMEM64G support, which requires PAE, but the Via C3 processor used on most Epias does not support PAE. You will have to use a kernel without HIGHMEM64G support (HIGHMEM4G will work, as will NOHIGHMEM)." from [here]("https://launchpad.net/ubuntu/+bug/71594").
Ther is also a post on this problem in [unbuntuforums]("http://www.ubuntuforums.org/showthread.php?t=294712").
I tried to add to boot aptions:
linux acpi=off, 
but all keeps the same:
unknown interrupt or fault at EIP  bla bla bla

It seems I won't be able to try Ubuntu Server 6,10
:( 
It is a pitty: I have Ubuntu 6,1 and Xubuntu 6,1 running in the same machine, with no problems...

¿anyone has an idea?

---

### Post by elst on 2007-04-01
IIRC, the only difference between Server and Desktop is the kernel and the initial package set, so you can install regular Ubuntu and just remove the desktop.

There's probably a boot parameter for the installer that lets you specify a different kernel, although I couldn't see it in the documentation:

[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/boot-parms.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/boot-parms.html)

---

### Post by jmvidalvia on 2007-04-01
I think I went a step behind.
I took te CD and re-start.
I selected "rescue a broken system"
After some screens I got the prompt and typed:
sudo apt-get install linux-386.
Reboot and the system is working.
Now I have two questions:

1- I have two kernels: 2.6.17-10-386 (the one that works), and 2- 2.6.17-10-server (it hangs at startup). Will I notice any differences? What am I missing using 386 version instead of the server one? are LAMP aplications I chossed while first instalation still available?

2- Now I have some messages: please take a look at enclosed png.
 ACPI: getting cpu index for acpiid 0x1
 sda: assuming drive cache: write through
 piix4_smbus 0000:00:07.3: host SMBus controller not enabled

¿should I ammend anything?
Thanks a lot!

---

### Post by elst on 2007-04-01
That's a neat solution! All that you've done is installed a new kernel alongside the existing (non-functional) one, so the rest of the system will be completely intact, and the  applications will be fine.

I doubt that you need any of the features of the "server" kernel - IIRC it just provides support for larger machines (> 4GB RAM etc.). You can remove it with apt-get at your convenience.

To get rid of the errors, try running the system with ACPI disabled. You may have to change a couple of the VMware settings for the virtual device that provides /dev/sda for the guest system.

---

### Post by jmvidalvia on 2007-04-01
Thank you!
I solved the acpi error by adding:
acpi=off noacpi
at the end of the kernel line, in grub.

But for other 2 errors..

sda: assuming drive cache: write through
piix4_smbus 0000:00:07.3: host SMBus controller not enabled

..I have no idea how to solve them
I will post this issue.
Thank you for your help!

---

