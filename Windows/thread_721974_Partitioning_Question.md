---
title: "Partitioning Question"
date: 2008-03-11
forum: Windows
---

### Post by bcr88 on 2008-03-11
I installed XP to a small partition on my internal drive because I wanted to use a partition on my external drive to install programs (so it wouldn't take up too much space on my laptop). I figured that although I needed to install Windows to one of the first 4 partitions on a hard drive, that once installed it should recognize all of them, like Ubuntu. Well, it still sees only the first 4 partitions on my external HD (I looked in Disk Management), and the partition I made for it was sdb7.

Is there any way to get Windows to recognize that partition?

And, btw, I cannot make an extended/logical partitions (GPT doesn't support it).

Thanks in advance for any help.

Bradley

---

### Post by sandysandy on 2008-03-11
windows will not be able to see the ubuntu partition by default. what is the requirement. however there are programs available which allow u to access ur ubuntu partitions from windows. 

if u want a common folder between windows and ubuntu 7.10 u can use any NTFS partition for that as ubuntu 7.10 can read and write to windows partitions though not vice versa.

hard disks generally can have 4 primary partitions. u can use an extended parition inlieu of one primary partition, which can then have other partitions.

regards

---

### Post by bcr88 on 2008-03-11
Sorry, what I meant was that I want an NTFS partition on my external drive to install Windows programs on (I mainly want to use it just to play a few games). However, my first 4 partitions on my external HD are already taken. (The partition I made for Windows is sdb7.)

My question is can I get Windows to recognize an NTFS partition that is past the first 4 partitions allowed by MBR?

I thought this was only necessary for booting. For example, in Ubuntu, /boot is on sda3, but / and /home are on sdb5 and sdb6. However, in Disk Management, Windows will only see the first 4 partitions.

And once again, I cannot make and extended partition because GPT (GUID Partition Table) does not support it (because GPT can, I believe, theoretically have an unlimited number of primary partitions, so there is no need for extended).

---

### Post by sandysandy on 2008-03-11
to quote wikepedia [http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

> A PC hard disk can contain either as many as four primary partitions, or 1-3 primaries and a single extended partition. Each of these partitions are described by a 16-byte entry in the Partition Table which is located in the Master Boot Record 

to quote teh-faq [http://www.tech-faq.com/hard-disk-partition.s](http://www.tech-faq.com/hard-disk-partition.s)

>  Extended Partitions

A standard partition table is only able to store information about four partitions. At one time this meant that a hard disk could have a maximum of four partitions.

To work around this limitation, extended partitions were created.

An extended partition stores information about other partitions. By using an extended partition, you can create many more than four partitions on your hard disk.

The four standard partitions are often called the primary partitions.

Partitions configured into an extended partition are often referred to as logical partitions.

so it seems u will have to forsake one primary partition and make an extended partition in which u can have further partitions.

regards

---

