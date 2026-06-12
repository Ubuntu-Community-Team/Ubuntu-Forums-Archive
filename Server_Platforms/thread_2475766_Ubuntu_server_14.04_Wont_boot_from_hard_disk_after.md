---
title: "Ubuntu server 14.04 Wont boot from hard disk after install from USB INITRAMFS error"
date: 2022-06-07
forum: Server Platforms
---

### Post by netrix-g on 2022-06-07
Hello all,

Linux newbie here - actually been "here" for a long time but stepped away from Linux when it got too frustrating, so still a newbie !
Trying to install Ubuntu server on an HP N54l Microserver.
Current hardware is a 500GB sata drive installed in the bay where the CDROM would sit [4 x 4TB HP drives waiting to go in for Raid setup]

So I've spent almost all day trying to get an install of the OS via a USB stick and finally got it nailed around 17:00 this evening. 
At the reboot prompt post install I removed the USB stick and went for it - but the sever just sits at a flashing cursor at the top left of the screen after the BIOS messages.

Google got me to the stage I am at now but I am struggling to get past this: intitramfs reports:[INDENT][B]gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -check root delay= (did the system wait long enough?)
 -check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdb1 does not exist. Dropping to a shell

[/B][/INDENT]
When I do blkid I can see the 500GB sata disk is showing as /dev/sd[COLOR=#ff0000]**c**[/COLOR]1 (the disk has three partitions: I used the wizard to setup 100GB boot, 283GB ?? and 17GB swap (I just accepted the default after setting the Primary partition to 100GB

I found a video showing some info on this mis-match, when booting into the USB drive again and selecting advanced options for Ubuntu server 14.04 etc
I press E and get to some parameters - the similarities in the video ended there so I copied the UUID from the previous blkid output to the Linux entry where the UUID was, I think, for SDB1.

After doing that I get different results .
The first time it just went in a loop and I got back to the initramfs prompt
The second time I get to error: no such device (then the UUID I entered)
I am currently sitting at the grub rescue> prompt and am losing the plot, hence my cry for help !!

many thanks in advance for any pointers - please be gentle as I have been away from Linux for a long time and my newbie status is more newbie than before !!

Regards

Netrix-g

---

### Post by guiverc on 2022-06-07
I'd not use Ubuntu 14.04 LTS or the 2014-April release - it's *end of standard support*.

[https://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/](https://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/)

> This is a follow-up to the Extended Support warning sent a month ago to  confirm that as of April 25, 2019, Ubuntu 14.04 LTS basic support has  ended.  No more package updates[1] will be accepted to the 14.04 primary  archive, and any subsequent support will be done via Extended Security  Maintenance

Sure if your system is **off-line** & connected only to other **off-line **boxes it's not a concern, but don't forget with an EOL release you'll get less project related support.

I'd suggest trying to use a *supported* release, such as Ubuntu 18.04 LTS from four years later in 2018-April, though don't forget even that release is approaching the end of it's *five* years of supported life, so if your system is intended to be used awhile, consider modern releases.  I'm unsure why you'd go for an EOL/EOSS release; as I use devices as old as from 2005 for QA (*Quality Assurance*) testing current releases.

Note:  you also tagged Lubuntu; Lubuntu is now LXQt and the oldest supported release is Lubuntu 20.04 LTS (*2020-April release*) with regards *full support*.

---

### Post by netrix-g on 2022-06-08
Thanks for the info - I have now downloaded v18.06.6 LTS
And apologies for the wrong tag - should have been UBUNTU - aging eyes !!

I am now in a loop with the screen flashing from[INDENT][COLOR=#0000ff]Generating crash report
to
ubuntu 18.04.6 LTS ubuntu-server tty1
to
a screen half filled with text that flashes off before I can read any of it[/COLOR][/INDENT]

Any ideas ?

Kind regards

netrix-g

---

### Post by yancek on 2022-06-08
Just to clarify, you now have Ubuntu 18.04 installed but are still unable to boot it, correct?  Is there a specific reason you want the server version without a GUI rather than the Desktoop version?  Coould you post some specifics on your hardware, how old and what manufacturer for example?

A flashing cursor on boot is an indication that the Grub bootloader was not installed properly.  Do you have any other OS installed on the machine or is Ubuntu the only OS?

The system can't find the boot files on the proper partition so you need to post the output of lsblk or blkid as well as the fstab file.  Or you could compare them yourself to see if whatever your root (filesystem) partition is shows the same from blkid and fstab.  Based on the info you posted, it doesn't seem to be correct.

Is this an EFI install or an older Legacy install?  100GB boot partition is a little extreme and there is no need for a separate boot partition except in certain circumstances  sdc1 is not a hard drive but a partition on the hard drive, one of 3 partitions you say you have and probably the boot partition.  The hard drive would be sdc.  Since you have multiple drives, it might be simpler to disconnect or disable the other drives and only have the drive on which you wish to install Ubuntu attached if that is not too big a ;problem.

The first step is to compare the UUID in fstab to the output of lsblk or blkid for that partition, the / filesystem partition.

---

### Post by netrix-g on 2022-06-08
Thank you for the reply - I dont think v 18.04.6 has installed - I never got to any of the setup prompts, just the loop I mentioned above.
My hardware is an old HP Microserver N54L - 16GB ram and an AMD Turon CPU. 4 x 4TB HP drives to be setup in raid of some sort and a 500GB WD Blue stat drive sitting on the sata bus that was originally meant for a CD or DVD.

I have a Qnap NAS and this server will be just to back up the Qnap (Qnap, at present, has 4 x 3TB WD Red drives but I have SMART issues so they will be replaced with 4TB drives soon)

As in my first post - v14 did install but after the reboot/remove USB there was an issue where initramfs was reporting a different drive to that of blkid, for the bootup HDD. But I have now overwritten, or trying to overwrite, that install with a later version of Ubuntu server.

I am now trying v22.04, writing the install iso to a different USB in case my USB has issues - LiLi USB creator is doing its thing as I type this reply

I originally chose the early versions as the hardware is pretty old now, but as I say - I do not want anything fancy yet, just to be able to Raid the storage disks and backup my Qnap (that has SMART warnings)

After that I will probably want top user the HP Microserver to better understand Linux commands and procedures especially to harden it against hackers etc (initially, when used for backup it will not have access to the web)

Any tips/pointers for the best Ubuntu flavour to install - or indeed any other OS that will be easy for a newbie to play with ?

Kind regards

netrix-g

---

### Post by netrix-g on 2022-06-08
So, installing Ubuntu 22.04 from a different USB drive...almost immediately after POST I am sitting at grub>

Whatever I type here I get Error xx unrecognized command

---

### Post by netrix-g on 2022-06-08
I dont think I have ever come across anything as frustrating as Linux installation :D

Installing v 22.04 server from a different USB stick using a different app to create the bootable USB - and the installation is going fine, except the install now doesn't recognise my HDD
If I plug the four data drives in, it will recognise those.

The other installs, that failed after the last reboot, all recognised the 500GB sata HDD to install the files on.

My thoughts are to remove the HDD and reformat it - I'm assuming NTFS will do but will Google before I commence

---

### Post by slickymaster on 2022-06-08
*Thread moved to **Server Platforms**.*

---

### Post by netrix-g on 2022-06-08
> **slickymaster said:**
> *Thread moved to **Server Platforms**.*

Thank you, and yes - I will mark as Solved when I manage to get Ubuntu server successfully installed

Regards

netrix-g

---

### Post by LHammonds on 2022-06-08
If your 4TB disks are going to be configured for RAID and not part of the OS, I'd leave them out / unconfigured until I got the 500GB drive installed with the OS.  Once the OS is working, I'd then configure the 4 disks for RAID (assuming you have a real RAID card and not fakeraid).

When installing Ubuntu, make sure you do not leave the old HDD formatted by some other operating system (such as NTFS).  I'd re-format it during the installation and configure the system to use LVM with EXT4 file systems.  I give the /boot partition 1GB of space.  100GB is a bit much for /boot.

I've been working on documenting how I configure 22.04 servers and I'm almost done.   You might not want to follow how I setup a server since mine are all done inside a virtual environment (not bare-metal installs like yours) but I do specify every step and setting which is the basis for all my professionally-managed servers.  I also use a bunch of partitions since this is a template for potentially 100 different servers so it remains very configurable...you might just one 2 or 3 partitions.  They tend to run themselves and I only have to manage them by exception rather than having to do daily, weekly, monthly maintenance on them.

Looking through it to see how someone else sets up their server may or may not be helpful to you so here's [the link]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=301") if interested.

LHammonds

---

### Post by netrix-g on 2022-06-08
> **LHammonds said:**
> If your 4TB disks are going to be configured for RAID and not part of the OS, I'd leave them out / unconfigured until I got the 500GB drive installed with the OS.  Once the OS is working, I'd then configure the 4 disks for RAID (assuming you have a real RAID card and not fakeraid).

When installing Ubuntu, make sure you do not leave the old HDD formatted by some other operating system (such as NTFS).  I'd re-format it during the installation and configure the system to use LVM with EXT4 file systems.  I give the /boot partition 1GB of space.  100GB is a bit much for /boot.

I've been working on documenting how I configure 22.04 servers and I'm almost done.   You might not want to follow how I setup a server since mine are all done inside a virtual environment (not bare-metal installs like yours) but I do specify every step and setting which is the basis for all my professionally-managed servers.  I also use a bunch of partitions since this is a template for potentially 100 different servers so it remains very configurable...you might just one 2 or 3 partitions.  They tend to run themselves and I only have to manage them by exception rather than having to do daily, weekly, monthly maintenance on them.

Looking through it to see how someone else sets up their server may or may not be helpful to you so here's [the link]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=301") if interested.

LHammonds

Thanks for this info - I will have a read through.
My data drives are removed, the only connected drives are the Live USB and the 500GB sata boot drive. But I cannot get the install to recognise the hardrive,
It did once, but still didn't install.

I am currently at the "Block probing did not discover any disks" stage. From here I can get to a shell - but know too little to be able to see where things might be going awry

Thanks again for the pointers

Regards

Netrix-g

---

### Post by LHammonds on 2022-06-08
Is the boot BIOS process legacy or UEFI?

---

### Post by netrix-g on 2022-06-08
> **LHammonds said:**
> Is the boot BIOS process legacy or UEFI?

I'm afraid I do not know - how would I check ?

---

### Post by LHammonds on 2022-06-08
[Differences between UEFI and legacy boot](https://pediaa.com/difference-between-uefi-and-legacy-boot/)

On a system that does not have an OS running yet, you can go into your BIOS (by pressing the whatever key is needed during boot...which varies from system to system...such as F2 or F10 or F12 or DEL, etc.)

Look around under boot options to see if you can discern legacy bios boot mode or UEFI.  Legacy-only systems won't have any mention of EFI/UEFI anywhere.  Many systems since 2012 (circa Windows 8) were common to support legacy or UEFI.

LHammonds

---

### Post by netrix-g on 2022-06-08
> **LHammonds said:**
> [Differences between UEFI and legacy boot]("https://pediaa.com/difference-between-uefi-and-legacy-boot/")

On a system that does not have an OS running yet, you can go into your BIOS (by pressing the whatever key is needed during boot...which varies from system to system...such as F2 or F10 or F12 or DEL, etc.)

Look around under boot options to see if you can discern legacy bios boot mode or UEFI.  Legacy-only systems won't have any mention of EFI/UEFI anywhere.  Many systems since 2012 (circa Windows 8) were common to support legacy or UEFI.

LHammonds

I do not see any ref to EFI/UEFI.

Good news is I am now have an installed Ubuntu server v22.04 LTS

Thank you for your pointers, I will have a look through your site at some stage.

For now, this server will be solely for backup of my Qnap 4 bay nas. So my next job is to set up the Raid.

Happy days !!

netrix-g

---

### Post by calle-2007 on 2022-12-29
Hello netrix-g


Nice that you were able to solve your problem with the installation of Ubuntu. Would it be possible for you to share your solution here with everyone?
I have the same problem.

I have an N40L and an N54L with 4x 3TB hard drives. I used the fakeriad controller from the microserver in a Raid 10. Unfortunately, all 4 HDDs are still displayed during the installation. The same behavior was also with the TrueNAS installation.
So I googled this problem and found the following entries:

- [https://serverfault.com/questions/622300/configuring-raid1-on-hp-proliant-microserver-n54l-ubuntu-14-04-1-lts](https://serverfault.com/questions/622300/configuring-raid1-on-hp-proliant-microserver-n54l-ubuntu-14-04-1-lts)
- [http://stefanfeilmeier.de/2012/12/25/hardware-raid-unter-linux-mit-dem-hp-proliant-microserver/](http://stefanfeilmeier.de/2012/12/25/hardware-raid-unter-linux-mit-dem-hp-proliant-microserver/)
- [https://forum.ubuntuusers.de/topic/verstaendnisfrage-zu-installation-auf-raid-hp-/](https://forum.ubuntuusers.de/topic/verstaendnisfrage-zu-installation-auf-raid-hp-/)

Can I install Ubuntu Server at a RAID array of 4 HDDs via a fake raid or do I always need an additional HDD for the operating system?

With best regards
Calle

---

