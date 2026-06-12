---
title: "MD Raid or Grub alarming?"
date: 2007-03-23
forum: Server Platforms
---

### Post by CounterStrike on 2007-03-23
I am trying to finish my personal testing of software raid (md) in dapper. I have setup raid and got it to work as expected, along with monitoring and notification via the mdadm process. The raid setup I have is a Raid 1 (mirror) array with two mirrored partitions on it. using mdadm I have failed, had the hot spare pickup and rebuild, along with restoring to it's full original configuration (placing the hot spare back in hot spare role). My problem is this. when I fail the first partition (on sda1) using mdadm it works as expected, but if I fail the drive (sda) by configuring the bios to say there is no drive installed or physically unplug the first drive while it is down and power it on without that first disk, it starts beeping. I don't know if this beeping of the system speaker is coming from grub or from mdadm, but either way it just beeps continuously and will not load. More specifically, the board posts, but when the grub dialog should come up, it is blank and the beeping starts at that time. I installed grub to the second hard drive as suggested in case of the first disk failing in raid 1 configuration and ,like I said, it works fine and comes back up with no problem after failing the first partition using mdadm. 

  Of course as I am typing and trying to be accurate as possible, it just occurred to me that the boot record is outside of the raid ability. However, I did check in the bios and when pulling the first disk, it did mark the second disk as the first boot device, so I don't know what's missing. Anyway, if someone could shed some light on this for me I would be very grateful.

Thanks,

Brian

---

### Post by djf_jeff on 2007-03-23
I'm not an expert with hardware but as I know, IDE disk cannot boot if it is in the slave mode. So, if you unplug the first drive or disable it in the BIOS, You cannot boot the computer anymore. Maybe someone can confirm this?

---

### Post by WesRatcliff on 2007-03-24
Also check that you have copied over the bootloader to the second drive.

Here are some notes I had from the last time I had to do this (lost a secondary drive a few weeks ago)

To install the bootloader onto the second drive: (replace /dev/sdb)

server:~# grub
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

Also see: [http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID#Installing_Grub_onto_both_MBRs](http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID#Installing_Grub_onto_both_MBRs)

Wes Ratcliff

---

### Post by CounterStrike on 2007-03-24
Thanks for the reply Jeff. These are sata drives operating in ahci mode and I realized that I have never tested losing a disk in my past life using windows software raid.  I do need to understand the capabilities/limitations of using linux software raid before I put a server into a production role, and part of that would also be understanding what the cause of the audible alarm was.

Thanks,

Brian

---

### Post by djf_jeff on 2007-03-24
Oh, excuse me, I just see the sda1 in your first post, so it's not IDE...

Does it says something on your screen (like two line of text in the top) or is it completely blank?

I have successfully setup software raid in the past with the howto that Wes Ratcliff has provide. So, maybe double check all the steps to be sure you have performed everything?

---

