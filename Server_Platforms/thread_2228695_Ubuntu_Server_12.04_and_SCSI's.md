---
title: "Ubuntu Server 12.04 and SCSI's"
date: 2014-06-08
forum: Server Platforms
---

### Post by Joshua_Reeves on 2014-06-08
Hi, this is my first post of this forum and I'm honestly not sure whether it's more appropriate here or in the hardware section, so please let me know if I've got it wrong. I recently acquired an old Dell PowerEdge 1750 rack server. I've been trying to install Ubuntu Server 12.04 on it, with the eventual goal of moving my Plex installation (which is currently on my domain controller) over to the new machine. I've run into a bit of an issue though.

The server uses hot swappable SCSI drives and has a RAID controller. If I don't build a RAID with the SCSI drives before attempting to install the OS, none of the drives will appear regardless of which drive I use or which bay I place it in. This happens regardless of whether or not I enable the RAID controller in the BIOS. If I do place the drives in a RAID, then the logical disk appears, but no matter which drive I specify as the boot drive in the RAID controller, or how I arrange the boot devices in the BIOS, the OS simply won't boot. I don't get a failed boot device warning, the system just seems to hang where it should normally boot into the OS.

This is my first time working with SCSI's, but my understanding is that I'm supposed to set the SCSI ID via jumpers or switches on the drive itself. I have a drive with jumper pins on it, but the interface on this drive does not line up with the interface in the drive bays. The two drives I have where the interface does line up do not seem to have any jumper pins or switches. I have looked over both drives multiple times to confirm this.

All that being said, I guess my questions are this:

1. Is this sort of behavior caused by inappropriately set SCSI ID's?

2. If so then how do I go about setting the ID's on the drives?

3. If not then what's causing this? Has anyone seen this before? I would imagine so.

Apologies if this is a stupid question. It's only recently that I've had the resources to play around extensively with networks and this is my first experience with Ubuntu server.

---

### Post by SeijiSensei on 2014-06-09
I'd start by looking in the BIOS.  Does it see all the drives and assign them IDs?  Is there a separate BIOS for the SCSI controller card?  If so, look there as well.

You can only use the onboard RAID card if the OS has a driver for it.  The Linux kernel in Ubuntu does come with a driver for some of the RAID controllers Dell uses, but you'd need to check for your specific controller.  If it works correctly, you'll see only one interface presented to the operating system by the controller.  For instance, on a Dell PowerEdge R410 I maintain, we have two (SATA) drives in a RAID-1 array using the SAS1068E controller on the motherboard and the driver for that device in the kernel.  To Linux, it appears simply as /dev/sda.

---

### Post by Joshua_Reeves on 2014-06-10
I went back after reading your post and took another look over the BIOS. There was a third option for the RAID controller there, SCSI only, that put everything straight. Needless to say I should have looked around a bit more beforehand. Thanks for the help!

---

