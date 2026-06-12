---
title: "GRUB Alternative"
date: 2015-07-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2015-07-08
I guess I play too much (dual boot 14.04 and win7) and seem to 'break' my system more often than not.  The boot rescue CD worked wonders for me but since buying a new pc it does not work and I have to rebuild GRUB manually  - this is not frequent enough for this process to be simple and quick so restoring GRUB is a bit of a pain (again).  I use 14.04 90% of the time but I do need a front end 'boot loader'.  Is there any recommendation for an alternative to GRUB?  (I have been using GRUB since 8.04).

---

### Post by ajgreeny on 2015-07-08
What are you doing to keep breaking grub?  Normally, once you have it set up how you want it, it just keeps working, so I wonder if you are doing something unusual or inappropriate.

What do you mean exactly by "front end 'boot loader'"?  The bootloader is always front end and invoked before anything else that is added during installation of Ubuntu and follows on from the BIOS or UEFI.

What hardware do you have and is the boot managed with BIOS/MBR or UEFI?

---

### Post by Quarkrad on 2015-07-08
On the ubuntu side nothing - grub never breaks.  It always happens when I do things on my win side.  I have a new UEFI motherboard but as far as I can tell I have configured it to behave in legacy/BIOS mode.  I have just tried re-installing grub via a live CD and it didn't work (been here before) - but lost physical access to my pc temporarily.  I will try reinstalling again when I'm able to access my pc.  In theory installing grub is great/simple but in practice I've experienced trouble with grub and again with grub2.  Is there a bootloader I can load via my windows environment that will do the same job as grub?  I find reinstalling grub frustrating and overly time consuming - done it many times - sometimes one method works, then it doesn't, so one hunts around for another method. And on it goes.

---

### Post by oldfred on 2015-07-08
If Windows is UEFI and Ubuntu is BIOS boot then you have to boot from UEFI menu and two systems will never see each other for booting.
But with UEFI Windows has been known to change UEFI boot parameters. Many times just booting Windows resets Windows as default boot loader.

Depending on vendor & model of system various work arounds may solve that issue.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Quarkrad on 2015-07-08
I'm going to need some help on this one - run a number of slightly different methods, both manually and using the boot-repair utility.  My boot-info is **paste.ubuntu.com/11842467**.   / is sda5 on this pc

---

### Post by oldfred on 2015-07-08
Clickable link for others who may want to quickly look at it:
[http://paste.ubuntu.com/11842467/](http://paste.ubuntu.com/11842467/)

You have BIOS based system, with 3 drives all MBR(msdos) partitioned.

I am not sure why you have issues? What exactly breaks?
Are you booting Windows thru sda1, sda3 or sdb1? Each has bootmgr & BCD, but could be different or a recovery/repair version.

With multiple drives you can install grub to one drive & Windows boot loader to the Windows drive.
Boot-Repair's default is to install one grub to all MBRs. Best not to use auto fix and in advanced mode you can choose an install and which drive to install grub into. But with Boot-Repair's auto fix you could have 3 copies of grub to boot from.
But I prefer to have all of Windows on one drive, and all of Ubuntu on another drive. Or configured so each drive can boot without any other drive. You can do that during install, but some suggest disconnecting other drive to make it simple.

I do not have Windows anymore, but my XP was on its own drive back when I did. And then I liked this logic, so I have a main working Ubuntu on one drive and at least one bootable, often test install on every other drive.

 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

---

### Post by Quarkrad on 2015-07-08
Of the three drives, HD1 is my dual boot OS main drive (sda) that includes a partition for win 7 (well two really because win7 does that), a partition for /, another for /home and another for storage. HD2 is purely for storage and HD3 is a backup  hd - so in terms of booting (to my understanding) the mbr is on sda (I could take out the other two drives and still boot to either os).  So ....  / being on sda5 - I have followed a number of grub reinstall models/instructions where in the various parameters I use is sda5 and sda.  Using either advanced mode in the grub repair app or manual input via the terminal I restart and boot to win7.

---

### Post by oldfred on 2015-07-08
Every drive and even partitioned flash drives have MBR for BIOS boot. And the MBR used to boot is set in BIOS. So you can boot from any hard drive, or external device. (CD/DVDs are different).

When you reinstall grub, you always need to reinstall to the MBR, by specifying a drive like sda. If you install to a partition like sda5, that is not bootable, except perhaps by another copy of grub.

Is issue that you cannot boot Windows from grub menu, and you restore a Windows boot loader to MBR? If so then you may have Windows issues, or leave Windows hibernated.

---

### Post by Quarkrad on 2015-07-08
I must have done something wrong some steps ago - or have a mis understanding of how grub/boot works.  My main HD is sda (as above) and / is on sda5 - when I type sudo fdisk -l in live cd mode I have a star for the boot partition on sda3 (which is my win7), sdb1 (HD2) and sdc1 (HD3).  I guess I need to remove these boot markers but not sure how.

---

### Post by oldfred on 2015-07-08
Grub does not use boot flag (shown by the asterisk). 

Windows must have boot flag (or in Windows the active partition)) on the primary NTFS formatted partition with the boot files. And in BIOS that drive must be default drive.
Windows needs boot flag to boot, to repair and to install to a primary NTFS partition.

Do not move boot flag from Windows.

But a few BIOS, require the boot flag on a primary partition to even let anything boot. So we often still suggest boot flag on systems without Windows, just to BIOS will let you boot. BIOS design on those systems seems to assume you only have Windows.

So every drive should have one primary partition with boot flag. And it should be on a NTFS primary partition if using Windows. Otherwise it does not really matter.

---

