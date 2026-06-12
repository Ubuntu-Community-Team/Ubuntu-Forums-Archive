---
title: "Can I install XP thru VB to a separate HDD?"
date: 2009-06-26
forum: Virtualisation
---

### Post by 73ckn797 on 2009-06-26
Can I install XP thru VirtualBox to a separate HDD? I do not want to be able to boot into XP but only use it through VB. I have an empty HDD, 160Gib. I have searched but do not find this specific question dealt with (maybe would have to search longer). There are only 2 programs and one task that I would like to have available that are only available using XP. Wine does not meet the need.

I have installed the VB package from Sun. I currently run 9.04 64bit. ext3. Second drive can be configured to whatever is necessary. A third drive (160GiB) is my Documents storage.

---

### Post by steele64e on 2009-06-27
Yes all you have to do is make a virtual hard drive on your empty drive. 
Then just assign that image to one of your machines and install xp.

---

### Post by 73ckn797 on 2009-06-28
Using VirtualBox preferences I designated using the alternate HDD but receive the following error message (see screenshot).

It does not seem to matter whether I create a folder or not, i get the same error.

---

### Post by bodhi.zazen on 2009-06-28
Things you should know :

1. I advise you unmount the partition and use if directly, ie /dev/sdb rather then mounting it and accessing via the mount point.

2. If you use a raw partition like this tools such as gparted will not recognize the partition as having a valid partition table (you will have to resize the partition).

I advise against using a raw partition like this. I advise you either use lvm (you can mount a raw logical volume) or simply make a virtual hard drive.

I do not think that there is any significant advantage of using raw partitions.

---

### Post by 73ckn797 on 2009-06-29
> **bodhi.zazen said:**
> Things you should know :

1. I advise you unmount the partition and use if directly, ie /dev/sdb rather then mounting it and accessing via the mount point.

2. If you use a raw partition like this tools such as gparted will not recognize the partition as having a valid partition table (you will have to resize the partition).

I advise against using a raw partition like this. I advise you either use lvm (you can mount a raw logical volume) or simply make a virtual hard drive.

I do not think that there is any significant advantage of using raw partitions.

I was reading some info on the error code and saw info using a raw partition in the process and, obviously, will have to do some more. Using a raw partition was not advised for the average user. I have partitioned the drive as sdb1 & sdb2, sizing sdb2 to 40GiB to use as the drive.

I was thinking that I would need to create a folder on that drive first. I have tried that and no matter what I do the error displayed upon attempting to create.

FYI:
```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68afe9c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14281   114712101   83  Linux
/dev/sdb2           14282       19457    41576220   83  Linux
```

---

### Post by bodhi.zazen on 2009-06-29
Not sure what you are asking.

If you want to use /dev/sdb2, as a raw partition ...

1. First unmount 

```
sudo umount /dev/sdb2
```

2. You may need to change the ownership and permissions.

```
sudo chown root.vboxusers /dev/sdb2
```

```
sudo chmod 770 /dev/sdb2
```

3. Then in Virtualbox, make a new hard drive, and use /dev/sdb2 directly.

=====

The other option is to simply make a partition on /dev/sdb2 , format /dev/sdb2 , mount /dev/sdb2 (anywhere you wish), and make a virtual disk, say 39 Gb, on the mount point.

---

### Post by 73ckn797 on 2009-06-29
> **bodhi.zazen said:**
> Not sure what you are asking.

If you want to use /dev/sdb2, as a raw partition ...

1. First unmount 

```
sudo umount /dev/sdb2
```2. You may need to change the ownership and permissions.

```
sudo chown root.vboxusers /dev/sdb2
``````
sudo chmod 770 /dev/sdb2
```3. Then in Virtualbox, make a new hard drive, and use /dev/sdb2 directly.

=====

The other option is to simply make a partition on /dev/sdb2 , format /dev/sdb2 , mount /dev/sdb2 (anywhere you wish), and make a virtual disk, say 39 Gb, on the mount point.

Thanks. I was only trying to be able to use the sdb2 for the VirtualBox drive for a WinXP install so that, like a separate /home partition, I would not lose the install should I have to re-install Ubuntu at any time in the future. I have already designated another drive for my documents. I probably would do better to just create a separate /home on one of those other drives. That way VB would do it's thing without this hassle.

I will follow your recommendation when I get back home later today.

Again, Thanks.

---

### Post by bodhi.zazen on 2009-06-29
If you go put your virtual drive on a partition separate from your root partition you will be good to go if you need to re-install.

+1 for that idea.

Personally I make my root partitions 10 Gb in size (gives me a little breathing room) + a large data partition.

---

