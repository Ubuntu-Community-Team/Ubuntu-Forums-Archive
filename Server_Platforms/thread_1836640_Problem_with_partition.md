---
title: "Problem with partition"
date: 2011-08-31
forum: Server Platforms
---

### Post by foobar9527 on 2011-08-31
Things like this happend:

[https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/561573](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/561573)


I have installed ubuntu 10.04 on my server with lvm on software raid
5,when a disk failed, I replaced one disk, use fdisk patition it, the other
partitions have one more cylinder than the new one

how can i patition the new disk to add the raid array?

thanks

---

### Post by YesWeCan on 2011-08-31
Hi, you might want to try directly copying the partition table from one of the old drives to the new one (as root):

sfdisk -d /dev/sdx | sfdisk /dev/sdy

where x is old drive and y is new drive

---

### Post by foobar9527 on 2011-08-31
There is an error for 

sfdisk -d /dev/sda | sfdisk /dev/sdg

error message:

partition 1 does not end at cylinder boundary

but I can use --force option to force the copy

sfdisk -d /dev/sda | sfdisk -f /dev/sdg

Is that ok?

---

### Post by foobar9527 on 2011-09-01
can somebody help me? thanks

---

### Post by YesWeCan on 2011-09-01
Ok. It looks like your sdg drive is brand new? So it hasn't been formatted at all.

Either:
1) Use Disk Utility to "format drive" with a Master Boot Record
Then repeat the sfdisk command, force it if necessary.

Or
2) Run this command to copy the whole MBR from sda to sdg (this is a dangerous command so don't make a mistake copying it)
[COLOR="Navy"]sudo dd if=/dev/sda of=/dev/sdg bs=512 count=1[/COLOR]

---

