---
title: "Sun scsi external drive not recognised"
date: 2016-01-23
forum: Server Platforms
---

### Post by David_Cropley on 2016-01-23
Hi I have a dell sc1425 server running a recent version of Ubuntu server with a Sun A1000 multi-disc drive bay attached but only seem to get error dumps on start up without any extra drives being available. I am fairly new to the Ubuntu system but does anyone know if there should be a driver for this device already in Ubuntu?

---

### Post by MAFoElffen on 2016-01-25
Before startup... check out your Sun StorEdge A1000. Make sure the SCSI-Utra cable from your computer is connected to one of the outboard ports on your device (has 4 ports). A short able is connected from one inboard port to the other in The opposite outboard port should be your terminator. The SCSI is usually set (default setting) to ID #7, but you can adjust if needed.

Your PCI card in your Server should be differential ultra wide SCSI capable card. (like an Adaptec AHA-3944UWD, AHA-4944UW, etc)...

On post, ensure that your host BIOS messages include the HBA BIOS extension from the SCSI card and that you can use the hotkey to get into the BIOS of the SCSI card. When in the BIOS setup of the SCSI card, look at the SCSI channels (A or B) and have it look for the SCSI devices. Ensure that it sees the A1000 and that it is online.

If on boot, you do a lspci, you should see it.

Functionally, that is about as far as I think you can get with that... The device has to be set up with Sun's software RAID Manager to configure the drives on the device. The last version for it was Sun StorEdge RAID Manager Software 6.22.1. Problem is that it was not written for Linux. It was written for Solaris versions 6, 7 & 8.

From the Oracle StorEdge A1000 Manual:
> 
The RAID Manager software is shipped with your system and runs on the host system. It allows you to configure the system for RAID functionality.

[https://docs.oracle.com/cd/E19696-01/805-2624-12/805-2624-12.pdf](https://docs.oracle.com/cd/E19696-01/805-2624-12/805-2624-12.pdf)
[https://docs.oracle.com/cd/E19782-01/805-7756-10/805-7756-10.pdf](https://docs.oracle.com/cd/E19782-01/805-7756-10/805-7756-10.pdf)

---

### Post by David_Cropley on 2016-01-27
Thanks for your quick reply MAF. Lspci does not seem to recognise the drives and there is no sign of them in the bios. The server has a ultra wide scsi out from an adapter in the pci - I believe this is an adaptec model from the boot info. The server has two ultra wide ports one for input and the second for Daisy chaining which is null terminated at the moment. As you say the indication is that this was for Solaris so may have the drivers in UNIX but will be no good for Ubuntu. The server does act differently when boot up with the A1000 plugged in but usually with a series on forever ongoing dump cards. I suspect it would be a driver issue and would really maybe need to pass the A1000 on to someone with a UNIX setup (if anyone still has that!). Thanks for your help though- it has given some clarity to my confusion!

---

