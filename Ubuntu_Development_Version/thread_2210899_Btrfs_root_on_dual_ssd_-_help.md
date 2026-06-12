---
title: "Btrfs root on dual ssd - help"
date: 2014-03-13
forum: Ubuntu Development Version
---

### Post by kenzu on 2014-03-13
Hey

I have an Asus Zenbook U500VZ with dual 128GB ssd's.
I would like to test btrfs and ubuntu 14.04 with uefi/grub2.
How should i partition my ssd's if I what snapshot support via snapper?

Do I need a efi boot partition?
Do I need a swap partition? (maybe for hibernation?)
Can I use raid 0 / stripping for root?

I'am comfortable in terminal and with sfdisk/gpt

Thanks

---

### Post by grahammechanical on 2014-03-13
How confident are you that Snapper will work on Ubuntu? I tried it when running 13.10 on btrfs and I found that it was not much use. I found it more useful to run the btrfs commands directly from a terminal. We can also install apt-btrfs-snapshot and that will take a snapshot every time we run apt-get update/upgrade whether we use the terminal or Update Manager.

If we have apt-btrfs-snapshot installed then we can go into Recovery mode and if we put the file system into read/write mode by running the Network option (for instance) we will get in the Recovery menu an apt-snapshot - revert to old snapshot and reboot option.

I gave up looking for a GUI snapshot manager. The Recovery mode apt-snapshot script is found here: /lib/recovery-mode/options. It will run from a terminal. It can be modified to include other apt-snapshot commands. I know this to be true because I have done it.

You should also know that because of the way that apt-get works or due to the repository structure or even something else you will get four apt-snapshots for every apt-get update done.

You may find that trying to install Ubuntu on btrfs will fail at the point of installing Grub without a 1MB of unallocated space at the start of the disk. This happened to me.

> [COLOR=#333333][FONT=Ubuntu]When installing Ubuntu in one large btrfs-Partition without an extra boot-partition, take care to keep about 1 Mib space free at the beginning of the disk. This is possible using the partition manager in the Ubuntu installer. When there is not this space, the installer fails at the end when trying to install Grub![/FONT][/COLOR]

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)


Regards.

---

### Post by kenzu on 2014-03-13
> **grahammechanical said:**
> How confident are you that Snapper will work on Ubuntu? I tried it when running 13.10 on btrfs and I found that it was not much use. I found it more useful to run the btrfs commands directly from a terminal. We can also install apt-btrfs-snapshot and that will take a snapshot every time we run apt-get update/upgrade whether we use the terminal or Update Manager.

I have not tried it, but have found to sources with info:

[http://linuxg.net/how-to-install-snapper-on-ubuntu-13-04-12-04-linux-mint-15-13-and-elementary-os-0-2-luna/](http://linuxg.net/how-to-install-snapper-on-ubuntu-13-04-12-04-linux-mint-15-13-and-elementary-os-0-2-luna/)
[http://wiki.1tux.org/wiki/Btrfs/Snapper](http://wiki.1tux.org/wiki/Btrfs/Snapper)


Will have in mind to leave 1mb free space.

edit: Do you use uefi? And do I need an efi boot partition?

raid 0 and swap will be a trial and error thing I guess :-)

---

### Post by oldfred on 2014-03-13
I do not know BTRFS, but the space at beginning of drive is with a BIOS install and some users were finding that core.img which is in the space right after MBR becomes very large for some reason.
With gpt and BIOS install you normally need a 1MB unformatted partition with the bios_grub flag for core.img as with gpt there is no space after MBR. They you may need something larger than the  normal 1MB??

If booting in UEFI mode you have to use gpt partitioning and must have efi partition.
Ubuntu will boot from gpt partitioned drive with UEFI or BIOS, but Windows only works from gpt drives with UEFI.

Why RAID 0?
       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by kenzu on 2014-03-13
Okay so my plan is now to make the following partition scheme:

ssd 1 (128GB):
1mb free space
300mb /boot/efi
120GB btrfs root/data
~7-8GB rest for garbage collection

ssd 2 (128GB):
16GB swap
100GB btrfs root/data
~12 garbage collection

Setup the btrfs filesystem as per [https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)

# Use full capacity of multiple drives with different sizes (metadata mirrored, data not mirrored and not striped)
mkfs.btrfs -d single /dev/sda2 /dev/sdb2

So it will all look like this in fstab:

/dev/sda1 /boot/efi
/dev/sdb1 swap
/dev/sda2 /dev/sdb2 btrfs root/data

Hope it works. See you all on the other side :-)

---

### Post by kenzu on 2014-03-14
And I'am back :-)

My plan worked. Used the installer to partition it all, but could only select on btrfs partition as root. Install went well and booted up first time.
Then I added the second btrfs partition with:
#sudo btrfs device add /dev/sdb2 /
and ran
#sudo btrfs balance start -dconvert=single -mconvert=raid1 /
added "compress=lzo" to fstab
and rebooted, after reboot I ran
#sudo btrfs filesystem defragment -r -v -clzo /

rebooted and all worked with a total size off 220GB root :-)

edit: dropped to install snapper and just use apt-btrfs-snapshot. I works well. :-)

---

