---
title: "Ubuntu Server 16.04 LTS No boot device invalid mbr signature found"
date: 2017-05-19
forum: Server Platforms
---

### Post by obstruktion on 2017-05-19
Hi All,

Disclaimer: I am new to the linux platform.

Notes: Ubuntu is the only OS on the server, the boot mode is set to bios and not UEFI, the OS was installed straight after the RAID array was initialized, don't judge me for using RAID-5 this is a test box in a home lab.

I built an Ubuntu Server using 16.04 LTS and installed KVM, Webvirtmgr and some other packages. Everything was running great for a few weeks. One night I safely powered off the server, unplugged it, relocated it and powered it on and received the following error:

[IMG][IMG]http://i.imgur.com/lrI7uWM.jpg[/IMG][/IMG]


After testing all the hardware I then turned my attention to the OS. I booted via a live boot disc, ran boot-repair and was not presented with a recommended repair. The boot-repair summary can be found here [https://paste2.org/Gn2tyNX3](https://paste2.org/Gn2tyNX3)

Could anyone please point me in the right direction as to where I could find the information that will help me resolve this issue?

Thanks in advance!

---

### Post by slickymaster on 2017-05-19
*Thread moved to **Server Platforms*** for a better fit

---

### Post by oldfred on 2017-05-19
Please attach screen shots, not everyone has high speed Internet.
You can easily attach with Forum's advanced editor and paperclip icon.

Do not know RAID.

But script did not see any drives other than disk label error on 1.2TiB sda?
That is often related to corrupted partition table or conflicts between gpt & MBR.

It says UEFI secure boot may be on. That has to be off for BIOS boot configuration to work.

Are drives gpt partitioned or 35 year old MBR(msdos) partitioned?

LVM inside partitions in addition to RAID?

---

### Post by obstruktion on 2017-05-19
Hi Oldfred,

Thank you for your reply. My apologies for inserting the screenshot.

The 1.2TiB sda is the RAID-5 array, it is comprised of 4x 450GB SAS drives.

I have attached some screenshots of the BIOS config. I am unsure if the virtual disk is partitioned as gpt or mbr. I just followed the defaults when installing the OS as my goal was to start learning linux as is the same reason I was playing around with LVM.

---

### Post by oldfred on 2017-05-19
Someone that knows & understands hardware RAID can help.

---

### Post by TheFu on 2017-05-19
HW-RAID sorta "just works."  FakeRAID (motherboard RAID) is a completely different animal.

One of my 14.04 servers locked up last night and the boot was screwed.  I booted off a live CD, at the boot menu, told it to boot off the first disk, then ran **sudo update-grub**.  Then backed out cleanly and rebooted.  All was fine.

Using LVM over RAID is still a good idea.  LVM is about flexibility. HW-RAID is about performance and HA. Those 2 together ARE a good thing.

Looked at the boot-info.
Doesn't look like things are working.  No partitions or LVs shown on sda?  Not good.  This is the time when you want to have backups of everything, including the partition layout.  You need to restore that, restore any LVM PEs, VGs, and LVs, then restore all the data.  You've always heard that backups are a good thing.  Here's your chance to use them.

Without looking at the logs, it is impossible to guess what may have happened.  I'd be paranoid about everything in the disk subsystem on the machine for the next few weeks.  PERC, cables, drives - everything.  If you don't already have backup religion, I'd get it.  LVM is a great thing for that, thanks to LVM snapshots. Use snapshots as part of your backup procedures.

---

### Post by darkod on 2017-05-19
Yes, I also agree that it doesn't look good when no partitions can be detected on your disk. It might have been an issue with the raid card, after you disconnected the power. Is this the first time you are unplugging the power cord lately? Could it be that your raid card is losing the config of the virtual disk when unplugged?

If you want to, you can try detecting the partitions with something like testdisk. That tool is quite good detecting partitions, assuming they still exist and there are no major failures on the disk. If the partitions are detected correctly, testdisk can write them into new partition table.

---

