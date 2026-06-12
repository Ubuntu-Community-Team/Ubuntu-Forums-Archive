---
title: "Raid 1 + LVM Failed to install grub on 15.04"
date: 2015-05-15
forum: Server Platforms
---

### Post by overmind2 on 2015-05-15
I guys. Please I need help partitioning my laptop Asus Zenbook Prime (nvidia + 2 hdd 250GB + can boot in UEFi) in raid 1 with + LVM.
I can't boot and the server installer amd64 of the 15.04 is failing writing boot.
I spent he last 3 days full time reading guides on internet of people in the same situation.
I also tried Boot-Repair.
Here my summary: [http://paste2.org/ajN7Fe4v](http://paste2.org/ajN7Fe4v)
What is the best practice?
I only want Linux on my Laptop and I tried installing different times with different partition scheme, with no success.
You are my last chance.

---

### Post by meinsen2 on 2015-05-25
Can confirm the error.
New install aof 15.4 server
install / on raid 1 -> can´ t write grub boot loader
repartition to have / and /boot
install on / raid 6 and /boot  raid 1 -> can´ t write grub boot loader

---

### Post by David_Booher on 2015-06-14
I can confirm, installing 15.04 from USB with software raid 1 setup will not allow me to install either GRUB or Lilo. They fail every time. I have downloaded the iso twice thinking something was wrong with the image and used a different USB. Nothing has helped.

---

### Post by oldfred on 2015-06-15
Moved to server sub-forum where those who know it better may be able to help.

If you want UEFI boot, you have to have an efi partition. I have seen encrypted LVM installs with both the efi partition and then a /boot partition. RAID then complicates it. And it looks like your sda is MBR and sdb is gpt? I did not think you could mix them, but best not to even if you can.

If booting in BIOS mode you must have a bios_grub partition of 1 or 2MB unformatted. You have a mixed efi/bios_grub partition which will not work for either. And the FAT32 formatted efi partition must have boot flag if using gparted or if gdisk the code ef00. And bios_grub is unformatted. You have a FAT32 partition with the bios_grub flag.

I do not really know RAID, but normally you install grub to the root of the RAID not the MBR of the hard drive if in BIOS boot mode.

At this point I think you need to start over. Make sure both drives are gpt. If you want UEFI make sure both drives have the efi partition. I believe grub2 does boot directly into RAID and/or LVM, but maybe easier to have a separate /boot before the RAID.

I normally install desktop version that has gparted. You can use it (is that what you used for running Boot-Repair?) or download a separate gparted live installer. Or use gdisk which is now included in newest Ubuntu versions or can be downloaded from repository. You must select gpt first before partitioning.
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

### Post by darkod on 2015-06-15
My personal opinion:
1. For a serious server (even for only playing around), don't bother with non-LTS releases. Use only LTS. The latest one is of course 14.04 LTS. That should not matter for this grub issue though.

2. For a linux only machine, forget about UEFI (in which case make sure you boot your install media in legacy boot, not UEFI boot). UEFI is needed for windows if you want to use gpt partition tables. Linux has no such requirement. If you DO decide to use UEFI, make sure you understand it and how to create the needed partition(s) and boot the media. In most cases bootloader install issues are related to this.

3. Again, for a linux only machine, use SW raid as opposed to fakeraid. If you do have a solid HW raid card, the decision is yours. But between BIOS raid and SW raid, don't even bother with fakeraid.

In most cases grub installs perfectly fine with SW raid and legacy boot. If anything else, try as a test this setup and see if grub will install good or not. Note that even with legacy boot on gpt disks you need a small 1MB unformatted partition usually at front with the bios_grub flag set, so that grub2 can install correctly.

---

