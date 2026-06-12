---
title: "Partitioning &gt;2TB RAID Array"
date: 2011-03-26
forum: Server Platforms
---

### Post by iissmart on 2011-03-26
Hi, I have an Areca hardware RAID array that I'm trying to format & partition on a fresh Ubuntu 10.04 LTS installation. The OS drive is not on the RAID card, it's entirely separate. The RAID is a 6TB volume so I realize I have to use parted to format it, not fdisk (which I've always relied on).

My problem is that I can't figure out how to get parted to like my settings. It seems like everything I try gives me the warning "Warning: The resulting partition is not properly aligned for best performance."

Here's what I'm doing:

```
(parted) p
Model: Areca ARC-1280-VOL#00 (scsi)
Disk /dev/sda: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted) mklabel gpt
Warning: The existing disk label on /dev/sda will be destroyed and all data on this disk will be lost. Do you want to continue?
Yes/No? y
(parted) mkpart primary xfs 0 100%
Warning: The resulting partition is not properly aligned for best performance.
Ignore/Cancel? c
(parted)
```What start/end settings should I use to get a properly aligned partition? How do I know?

I have tried a mix and match of 0, 0s, 1, 1s, -0, -0s, -1, -1s, 100% for my start/end with no success.

---

### Post by srs5694 on 2011-03-26
First, if you prefer fdisk to parted, you may want to use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) on GPT disks. I recommend you download the latest version from the [SourceForge download page](https://sourceforge.net/projects/gptfdisk/files/gptfdisk/) rather than use the version in the Ubuntu repositories, since the latter is extremely out of date.

Second, parted is griping because many new disk technologies have special alignment requirements. I wrote [an article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for IBM developerWorks about this, although my article focuses on Advanced Format disks. As the sidebar in the article describes, though, there are similar issues with some types of RAID arrays (and also SSD devices). Generally speaking, starting all partitions on 1 MiB multiples (2048 sectors) is the best approach. In parted, you'd need to specify a starting point of 2048s (or multiples thereof). GPT fdisk defaults to settings that round the starting sector you specify up or down to match the modern recommendations, although you can adjust the alignment settings if you like.

---

### Post by Vegan on 2011-03-27
Given a hardware array, you will definitely need a GPT partition for that large of storage.

Using a boot disk is fine as this gets around the BIOS limitations.

Now given the setup, the disk will be best off using GTP and ext4 for a file system

Then you can mount it and use it.

Hope you have a good backup solution as 6TB is a lot of stuff to lose.

---

### Post by iissmart on 2011-03-27
So I run parted with the -a flag and create a partition using 2048s for START:

```
# parted -a optimal
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p
Model: Areca ARC-1280-VOL#00 (scsi)
Disk /dev/sda: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted) mkpart primary xfs 2048s 100%
(parted) p
Model: Areca ARC-1280-VOL#00 (scsi)
Disk /dev/sda: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  6001GB  6001GB               primary

(parted) align-check optimal 1
(parted)
```No warning this time, which is great, but align-check still fails? If it passed, it would have said "1 aligned".

Is 1MiB the smallest 'optimal' offset? Does my 128k RAID stripe size affect this?

---

### Post by disabledaccount on 2011-03-27
In case of Raid array's partitions should be alligned with stripes/strides, but You should refer to controller documentation, as there are different definitions used for Stripe. In most cases Stripe is defined as minimal block of data transfered from/to array, but sometimes (md for example) this is minimal block of data for each array member. This makes *huge* difference for partition aligment, as in second case partition offset should be equal to Stride (set of stripes).
This also mean that 1MiB is optimal/safe offset only for 1st definition of stripe, because in second version stride can be much greater than 1MiB (eg. 4 hdd x 512k stripe = 2MiB Stride).

Stripe can't affect parted, because it's invisible from block device layer.
You shoud have disebled auto-alignment and set partition offset manually (eg. by setting unit option to "s" - sectors)

why xfs? Ext4 works best with raid after you provide raid geometry information during formatting (stripe and stride size)

---

### Post by srs5694 on 2011-03-27
The only way to be sure if the warning you're seeing is real or bogus is to find out on what sectors the partition(s) begin and do the math yourself. You can do this by using the "unit s" command in parted or by using gdisk to display your partitions. If your partitions all begin on multiples of your stripe size, you should be fine. If not, you should redo it by using "unit s" in parted or by using gdisk to create the partitions.

---

### Post by disabledaccount on 2011-03-27
> **srs5694 said:**
> If your partitions all begin on multiples of your stripe size, you should be fine.It depends on Stripe definition. In case when Stripe is defined as per-array-member chunk of data, then partition must be aligned to stride - in other case array will suffer from unneccessary additional reads and write amplification - especially Raid5/6/0 and derivatives. This is similar situation as if You would set partition offset to value lower than stripe size (first definition)

---

### Post by iissmart on 2011-03-27
From the Areca manual:

> Stripe Size - This parameter sets the size of segment written to each disk in a RAID 0, 1, 10, 5, or 6 logical drive. You can set the stripe size to 4 KB, 8 KB, 16 KB, 32 KB, 64 KB, or 128 KB.

I set it to 128KB for my RAID 6.

```

(parted) unit s
(parted) p
Model: Areca ARC-1280-VOL#00 (scsi)
Disk /dev/sda: 11721064448s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End           Size          File system  Name     Flags
 1      2048s  11721062399s  11721060352s               primary

(parted)
```

The End isn't aligned to 128 KB boundaries...what should I specify for the end of the partition? Looks like the very last sector is a multiple of 128, can I just use that or do I need an offset from the end as well?

[Edit] I might need an offset:

```
(parted) unit s
(parted) p
Model: Areca ARC-1280-VOL#00 (scsi)
Disk /dev/sda: 11721064448s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted) mkpart primary xfs 2048s 11721064448s
Error: The location 11721064448s is outside of the device /dev/sda.
```

---

### Post by disabledaccount on 2011-03-28
> **iissmart said:**
> The End isn't aligned to 128 KB boundaries...what should I specify for the end of the partition? Looks like the very last sector is a multiple of 128, can I just use that or do I need an offset from the end as well?You can use "natural" end of array - it can't hit performance for single partition.

---

### Post by YogiPaolo on 2011-11-06
You're the person who wrote that article?!?! THANK YOU!!!!

That was a fantastic piece of information that I still refer to.

---

