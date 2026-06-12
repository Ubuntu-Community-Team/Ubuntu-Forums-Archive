---
title: "format and mounting Raid problem"
date: 2012-09-28
forum: Server Platforms
---

### Post by sheridon on 2012-09-28
Hello,

I've got a server with Ubuntu 10.10 loaded and am trying to mount a hardware raid.

The raid is 50+ TB controlled by a hardware controller.  

When I run sudo fdisk -l the OS shows the drive as /dev/sda.

I run sudo fdisk /dev/sda and create a partion type ee GPT, removing the DOS compatibility and write the table.

Now when I run fdisk -l the OS shows /dev/sda1

When I try to format the drive running sudo mkfs.xfs /dev/sda1 I get the following error:
"Cannot stat /dev/sda1: No such file or directory"

Any ideas as to what the problem is?

Thanks!

---

### Post by szafran on 2012-09-28
> **sheridon said:**
> Hello,

I've got a server with Ubuntu 10.10 loaded and am trying to mount a hardware raid.

The raid is 50+ TB controlled by a hardware controller.  

When I run sudo fdisk -l the OS shows the drive as /dev/sda.

I run sudo fdisk /dev/sda and create a partion type ee GPT, removing the DOS compatibility and write the table.

Now when I run fdisk -l the OS shows /dev/sda1

When I try to format the drive running sudo mkfs.xfs /dev/sda1 I get the following error:
"Cannot stat /dev/sda1: No such file or directory"

Any ideas as to what the problem is?

Thanks!

As far as I know fdisk doesn't work with GPT - use parted. And for using a 64-bit size disks you need a kernel+e2fsprogs mix that can handle 64-bit filesystems (if you're planning to use ext4) - then you need to update to 12.04 or kernel + e2fsprogs (>= v1.42 I think - but some utils still don't work with 64-bit ext4 in that version - eg. tune2fs).

---

### Post by darkod on 2012-09-28
Definitely use parted, including to write new gpt table on the disk. After that create the partition(s) and format them.

I am not sure if such big filesystems are supported on 10.10 especially since it's not LTS version. Most people use only LTS versions for servers, I suggest you consider that.

---

### Post by rubylaser on 2012-09-28
+1 for parted.

XFS will support a volume of 50TB without a problem (other than when it comes to fsck it, then I hope you have a heap of RAM).  I would definitely be using 12.04 or 10.04 so that you are using a Long Term Support Release.  Also, I would suggest tuning XFS to maximize it's throughput. Also, please tell me that you are using RAID6 at the **absolute minimum**.

---

### Post by sheridon on 2012-09-28
Thank you for the answers,  I am using 10.10 because I cloned it from another server we are currently using with the same drive size.  

The previous admin that set this up is no longer with us so I am picking up the pieces to get another server running.

I am looking to possibly update the server to a new OS that will be supported longer.

Yes I am also using Raid 6.

I will look into using parted, although I'm not really sure of the differences yet.

I tried the setting I had above because that is what was set up on a duplicate system.

---

### Post by darkod on 2012-09-29
parted is much better to use on a server especially with gpt.

You enter the parted prompt with:
sudo parted /dev/sda

Once there, there are different options, investigate what you need to do BEFORE doing it, since the changes are immediate!!!

To create new blank gpt table you would do:
mklabel gpt

To change the units that parted displays (and this one I like most) to MiB for example (the real binary MegaByte which is 1024KiB) you would do:
unit Mib

At any time you can print current table/partitions with:
print

To create gpt partition after making gpt table, you use:
mkpart <name> <begin> <end>

It has to have name assigned, and you can set exact start and end point on the disk. Note that this depends on the current unit set. So, for example, after setting the unit to MiB to create partition starting at 1MiB and ending at 500,000MiB you would do:
mkpart PAR1 1 500000

Note, parted creates only partitions, not filesystems. It can, but I rather not use it to create filesystems. After you create the partition you format it outside parted.

parted manual:
[http://www.gnu.org/software/parted/manual/parted.html](http://www.gnu.org/software/parted/manual/parted.html)

---

### Post by sheridon on 2012-10-02
darkod,

Thanks alot!  That worked.  Not sure why using fdisk to make the partitions didn't work but this got it done!

Thanks, again

---

