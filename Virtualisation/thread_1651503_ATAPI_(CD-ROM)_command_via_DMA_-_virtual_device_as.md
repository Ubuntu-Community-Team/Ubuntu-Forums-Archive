---
title: "ATAPI (CD-ROM) command via DMA - virtual device as a SCSI device - Guest OS WinXP SP2"
date: 2010-12-23
forum: Virtualisation
---

### Post by Tiff_Needle on 2010-12-23
Hi there,

I've been searching a lot before I decided posting here but so far I've been unable to find out a solution for my issue.

My host OS is Ubuntu 10.10 and my guest OS is Windows XP SP2 running via VMware's player.

The thing is that sometimes whenever I'm using EAC on the virtual Machine, I get the following message:

"
Your  virtual machine has send an ATAPI (CD-ROM) command that is supported  only when programming the drive via DMA. You will need to configure your  guest operating system to use DMA when communicating with DVD/CD-ROM  devices.
Note that some operating systems will report DMA is available without  actually using it. In those cases, normal CD-ROM operations will still  be available, but special features will only be available if you  reconfigure the virtual device as a SCSI device.                         "


I have been reading up on this and  it seems like I have to edit my linux os. Then I read up some on that  and I know I am supposed to go into my kernel source directory and type:
  Code:
 make menuconfig 
Then I am in there, but I am not sure where to edit and I do not want to fool around unless I am 100% sure.
 
Can anyone help me step through this?

Cheers,

Tiff

---

### Post by dcstar on 2010-12-25
> **Tiff_Needle said:**
> 
.........
Then I am in there, but I am not sure where to edit and I do not want to fool around unless I am 100% sure.
 
Can anyone help me step through this?


Go into the VMware Player VM Advanced setting for the CD/DVD and try the "Legacy" option.

AFAIK Linux kernels have been using DMA for years, there is nothing to change at that level.

---

