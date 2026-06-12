---
title: "re-install OS on existing RAID"
date: 2012-07-18
forum: Server Platforms
---

### Post by associates on 2012-07-18
Hi,

I was wondering if I could get some help here. I have a working Ubuntu server 10.04 that is set up with RAID 1. Now, because i want to re-install with the latest Ubuntu Server 12.04 from scratch. My question is whether I could re-use the existing RAID 1 configuration or I have to remove the current RAID and re-build it from scratch in order to install server 12.04. I have read some thread posted in this forum that I need a livecd to do this. The problem is the one that i have is for Ubuntu Desktop 8.10 - very old version. I have troubled to install mdadm.

I wonder if there are any other workaround to this.

Any help would be greatly appreciated.

Thank you

---

### Post by darkod on 2012-07-18
You should be able to reinstall with the server 12.04 cd. If it can recognize the raid controller, and in many cases it does, you don't need anything else.

It should also recognize the existing partitions so you can use the same layout if you are happy with it.

Only note that by default, ubuntu marks all partitions as Not Used, to prevent overwriting important data.

You have to select the partitions one by one, and select with what filesystem you want to use them and the mount point.

Don't expect to automatically install over the 10.04 with the same layout, if that's what you mean. It will detect partitions, but never uses them automatically. You have to tell it which partition to use as what.

---

### Post by associates on 2012-07-19
Thank you for your reply.

Based on your info, I have decided to use the same layout when re-installing with Ubuntu Server 12.04.

After the installation, I run "$ cat /proc/mdstat" and got as follows

md1: active raid1 sda2[0] sdb2[1]
     970902464 blocks [2/2] [UU]
md0: active raid1 sda1[0] sdb1[1]
     5858240 blocks [2/2] [UU]

I suspect md0 is for swap because I set it to 6GB of size. I wonder if I have done this correctly.

Thank you

---

### Post by darkod on 2012-07-19
Looks OK. You can also check what is mounted as swap in /etc/fstab with:
cat /etc/fstab

If the entries in fstab are with UUID, not in /dev/mdX format, you can compare the UUIDs with:
sudo blkid

---

### Post by associates on 2012-07-19
Thank you for your reply.

I run "cat /etc/fstab" and the result was

# / was on /dev/md1 during installation
<file system>: UUID=5970c739-0c3f-49ed-8e25-b1027561e7e3
<mount point>: /
<type>: ext4
<options>: errors=remount-ro
<dump>: 0
<pass>: 1
# swap was on /dev/md0 during installation
<file system>: UUID=4efa90c7-49fd-4078-a531-f78f2c645ad4
<mount point>: none
<type>: swap
<options>: sw
<dump>: 0
<pass>: 0

After that, I run "blkid"
...
/dev/md0: UUID="4efa90c7-49fd-4078-a531-f78f2c645ad4" Type="swap"
/dev/md1: UUID="5970c739-0c3f-49ed-8e25-b1027561e7e3" Type="ext4"

From the UUIDs, they are matched. However, I am a bit concerned with <options>: errors=remount-ro. It's got the word "errors". Do you happen to know what this error means?

Thank you in advance

---

### Post by darkod on 2012-07-20
That's a standard option, don't worry. It means if any errors happen during mounting, to remount it RO (Read Only).

That's a standard default option for the root partition.

You can see in fstab it says swap was on /dev/md0 during install, so yes, swap is md0.

---

