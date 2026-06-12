---
title: "Large (&gt;2TB) volume partitioning problems"
date: 2008-09-04
forum: Server Platforms
---

### Post by midgetspy on 2008-09-04
Hey all,

I've created a file server using a hardware RAID card which supports up to 32 drives per array. I'm running Ubuntu server 8.04. I currently have got it working properly with 3 1TiB drives in RAID5 for 2TiB of usable space, formatted to ext3 with 4k blocks to allow eventual volume size of 16TiB. I had originally planned to add another 1TiB drive to the array every time I ran out of space, growing the partition & file system after each addition.

Recently I filled up the original 2TiB, so I added another 1TiB disk to the array. fdisk shows:

Disk /dev/sdf: 3000.3 GB, 3000370200576 bytes
255 heads, 63 sectors/track, 364774 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      243182  1953359383+  83  Linux

As you can see, the partition /dev/sdf1 is 2TiB and the array size is 3TiB. I want to resize (grow) the partition without losing any data. This is crucial - I don't have the resources to back up 2TIB of data. And though I *could* go buy 2TB backup storage, backing up my data isn't going to be an option every time I add a drive to this array. I understand there's an inherant risk dealing with this but that's unavoidable.

So far I've been unable to resize the partition. I started by trying parted since it has partition & file system resize built in. It complained about an incompatible feature enabled and wouldn't do anything. I tried parted again after removing the journal from the file system (making it ext2) and got the same error. Since ext2 file systems seem better supported than ext3 I just left the file system with no journal for the next few attempts.

Next I tried using fdisk to delete the partition and create a larger one in its place and then using resize2fs. This would work, probably, except that fdisk can't make partitions larger than 2TB, so that was a dead end.

I gave cfdisk a shot next since it seems to support partitions larger than 2TB (though I can't find any documentation claiming either way). I deleted the old partition and created a new 3TiB one, double-checked that the table looked correct, and wrote it to the disk. It looked like it worked, with cfdisk showing a single 3TiB partition and no free space. Something went wrong, though, and I was getting errors with the filesystem:

midgetspy@MidgetNAS:~$ sudo e2fsck -f /dev/sdf1
[sudo] password for midgetspy:
e2fsck 1.40.8 (13-Mar-2008)
The filesystem size (according to the superblock) is 488339845 blocks
The physical size of the device is 195640868 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

I checked with fdisk and cfdisk and they both claimed that there was an 800GB partition on the disk and the rest was free space. parted, like usual, was totally useless and wouldn't even print me a partition table. I tried rebooting which changed nothing. Not wanting to wreck the file system and lose my data, I used fdisk to reverse the changes and restore the old partition. After re-adding the journal and re-mounting it I'm back to square one, with a 2TiB partition on a 3TiB volume and no way to expand it. I've run out of partitioning utilities to try... is there another utility I can use to resize this partition?

If I can't resize it, the only other thing I can think of is to keep creating new 2TB partitions as I expand the array. From what I've read, though, I can only have 4 primary partitions per volume which means 4x2TB = 8TB max volume size. This means I'd lose 1 drive per 8 because of RAID5 parity, which is considerably more wasteful than 1 drive per 31. I'd also end up with tons of partitions which would be a pain in the ***, heh.

So I'm stuck. Any help would be greatly appreciated. If you want any further info about my volume/filesystem just ask and I'll be happy to paste it for you.

Thanks,

Nic

---

### Post by crachel on 2008-09-04
i have no experience with what you're asking, however it appears as though you could give  [Gparted]("http://gparted.sourceforge.net/") a try

---

### Post by midgetspy on 2008-09-04
> **crachel said:**
> i have no experience with what you're asking, however it appears as though you could give  [Gparted]("http://gparted.sourceforge.net/") a try

I don't have X installed (server install) and I believe gparted is GUI only. Thanks for the suggestion, though.

Nic

---

### Post by crachel on 2008-09-04
You may be right, I got the Gparted GUI to load when I booted from the LiveCD (I also have a server install), but I had no mouse for clicking.  you may be able to use 100% keyboard shortcuts, if you were desperate enough

---

### Post by erwall on 2008-09-04
Could try a gparted live cd, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by skmanji on 2010-03-26
Use parted from command line instead:

[http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html](http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html)

---

### Post by KB1JWQ on 2010-03-26
IIRC ext4 may support larger filesystems?

---

### Post by psusi on 2010-03-26
The MSDOS partition table can not handle more than 2TB disks.  You have to use GPT instead.  Parted supports GPT, but can not perform an in place conversion; it wants you to start fresh.  You could in theory have it make a new GPT partition table, then put it in sector mode and recreate your partitions EXACTLY like they were before and not loose your data, but that's a bit risky.  I think there was a program called "gdisk" I found googling once that said it can convert from msdos to gpt.

---

### Post by fang0654 on 2010-03-26
Another problem you may run into is booting off a GPT drive.  A lot of BIOSes won't do it.  Many hardware raid controllers will give you the option of partitioning off a little bit of the raid to use as a boot drive.  On 3ware controllers, for example, it is called a bootable drive.

Most likely, you are going to have to rebuild your partition/drive structure no matter what to make use of the >2TB space and boot from the controller.  The most painless solution is probably pick up another 1TB drive, take the other new drive, and make a 2TB Raid 0.  Copy all the data over to the Raid 0, then rebuilt the original Raid 5 with a small (I usually use 20GB) boot drive, reinstall the OS to it, use parted to set up the rest of the space as GPT, copy back the data, then kill the Raid 1, add the drives in, and expand the partition.

I ran into this building a LinuxMCE box with 8 1TB drives in a raid 6.

---

### Post by psusi on 2010-03-26
The BIOS should not know or care that it is using GPT since the first sector of the GPT is also an MBR, though you may need a small /boot partition at the start of the disk.

---

### Post by fang0654 on 2010-03-26
I guess not having a small partition in the beginning of the drive was why it failed for me then.  Either way still requires a rebuild /rework of the filesystem layout on the disk.

---

