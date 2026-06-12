---
title: "VMware Server - can't power on windows"
date: 2008-04-25
forum: Virtualisation
---

### Post by BLo on 2008-04-25
I haven't really mucked around with virtualisation before and decided to give it a go. I've just installed Hardy and got VMware server running after a couple of attempts. 

The problem is when I try to install a windows VM and 'power on this virtual machine' it goes to a black screen for a couple of seconds then goes the closes.

Anyone have any ideas? 

thanks

---

### Post by BLo on 2008-04-25
With a bit more searching i found out that it was because I kept my virtual machine on a ntfs partition which doesnt work so well unless you add the following to the .vmx file:

Set "mainMem.useNamedFile=FALSE" in the .vmx file


So the VM now starts loading but now it doesn't detect any bootable CD, floppy or hard disk drives even though I have my windows cd in the drive. Im guessing this is because my laptop uses a scsi DVD and HDD? Will I have to install drivers? How?

Any advice is appreciated

---

### Post by fjgaude on 2008-04-25
The only time I experienced what you point to is when I typed in CTRL-C and the install disk started working.

I remember putting the install disk in after I had powered on the VM as it was waiting to do something.

Good luck.

---

### Post by The_Big_D_GFK on 2008-05-02
Hi BLo,

I am having a problem similar to yours. I create my virtual machine as an 8 GB IDE drive. The I power it on, with my Windows XP Professional CD in the CD drive. Windows setup begins, as I would expect. However, aftger all the drivers and other files have loaded, and tghe actual installation wants to begin, the system tells me there are no haerd drives insalled. Have you or anyone else ever encountered this problem? Thanks in advance for your help.




Warm regards

---

