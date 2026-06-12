---
title: "Mdraid shrinking raid-1"
date: 2013-01-27
forum: Server Platforms
---

### Post by finni on 2013-01-27
I'd like to shrink my raid-devices size from 4 to 2 in my raid-1 array. How do I do this? I tried it with --grow and --manage option, but no luck. My ubuntu version is 10.04 server.

Error with --grow option:
```

$ mdadm --grow /dev/md2 --raid-devices=2
mdadm: Cannot set raid-devices for /dev/md2: Device or resource busy

```

Details of the array:
```

$ mdadm -D /dev/md2
/dev/md2:
        Version : 00.90
  Creation Time : Wed Nov 10 23:21:40 2010
     Raid Level : raid1
     Array Size : 8385856 (8.00 GiB 8.59 GB)
  Used Dev Size : 8385856 (8.00 GiB 8.59 GB)
   Raid Devices : 4
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Sat Jan 26 16:57:57 2013
          State : active, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : a5675e86:78b79e69:f3705577:10422964 (local to host beatrix)
         Events : 0.1015

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       8       50        2      active sync   /dev/sdd2
       3       8       66        3      active sync   /dev/sde2


```

---

### Post by darkod on 2013-01-27
First, you can't work on md2 while it's mounted.

Second, it already shows two devices as removed, there are only two left currently. So, it seems you already shrinked it to two devices.

---

### Post by finni on 2013-01-27
I can't edit raid-devices even when I stop the raid array and try to change it then, or at least don't know how to.

As you see the raid-1 array is in degraded state because there is 2 drives missing. Is there a way to shrink raid-devices from 4 to 2?

There is another question: I did the same with another mdraid raid-1 array (md0 - I added 2 new disks) and when I remove the original two disks from the array the linux won't boot. I did do a grub-install on the new 2 disks before booting. Grub is loaded to stage where it says "(fd0) read error" and then it just reboots. (It does say that error also normally when booting is successful also.) And when I reattached the 2 original drives linux booted normally. How should I proceed? Grub2 is set to boot from md0 array.

---

### Post by darkod on 2013-01-27
But what is the point? To replace the two raid1 disks with bigger ones?

If you want to replace them with bigger ones, you replace one by one. You don't add two new ones and try to remove the older ones. Just like if one disk failed and you replace it with a new one. And after it's synced, you replace the other one too.

I haven't worked too much with mdadm and moving the disks around so much.

What actually are you trying to achieve?

---

### Post by finni on 2013-01-27
Yes, that was the idea. I just happened to try growing the raid-1 array to 4 drives also. Didn't realise there was no going back to 2 drives, or is there?

---

### Post by darkod on 2013-01-27
There should be going back to 2 devices, but now it will be much more complicated.

First of all, how did you remove the 2 disks? Did you simply shut down and removed them physically?
I'm asking because before physically removing you need mark the disk failed first, then mark as removed, and then disconnect it.

But even before doing that, you need to shrink the filesystem to a size smaller than the array size when it will be shrinked to 2 disks.

If you only disconnected the 2 disks, I sugegst connecting them back, boot your machine with all 4 disks, and post the outputs of these commands:
```
sudo mdadm -V
sudo mdadm --detail /dev/mdX #(replace the X with the number of the md device you want shrinked)
df -h
```

Then we can see what can be done.

---

### Post by finni on 2013-01-28
In the case of md2 raid I first set the drives failed with mdadm and then removed the drives with mdadm. Drives are still attached physically because they are in use in md0 raid-1 array.

In the case of md0 raid-1 I just physically disconnected them and it seems it will not boot a degraded array unless set manually; [https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

Does anyone know about shrinking the array? The array's storage size is not what I want/need to shrink, but the raid-devices size.

---

### Post by finni on 2013-01-28
After reboot it seems the grow worked for md2 array!

```

$ mdadm --detail /dev/md2
/dev/md2:
        Version : 00.90
  Creation Time : Wed Nov 10 23:21:40 2010
     Raid Level : raid1
     Array Size : 8385856 (8.00 GiB 8.59 GB)
  Used Dev Size : 8385856 (8.00 GiB 8.59 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Mon Jan 28 17:43:08 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : a5675e86:78b79e69:f3705577:10422964 (local to host beatrix)
         Events : 0.1252

    Number   Major   Minor   RaidDevice State
       0       8       34        0      active sync   /dev/sdc2
       1       8        2        1      active sync   /dev/sda2

```

I also managed to shrink md0 raid-1 to 2 raid-devices by faulting and removing the devices with mdadm!
```

$ mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Nov 10 20:05:09 2010
     Raid Level : raid1
     Array Size : 14651136 (13.97 GiB 15.00 GB)
  Used Dev Size : 14651136 (13.97 GiB 15.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jan 28 18:44:22 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : b57016b4:9c9155bd:639d399e:66818d76
         Events : 0.1124

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       81        1      active sync   /dev/sdf1


```

---

### Post by darkod on 2013-01-28
> **finni said:**
> 
Does anyone know about shrinking the array? The array's storage size is not what I want/need to shrink, but the raid-devices size.

It doesn't work exactly like that. First you have to shrink the filesystem on all md devices that will be affected by the removal of physical disks. Even if the filesystem is 90% empty (free), you have to shrink it because you don't know where physically the 10% of the data is. Maybe it's on the disk you will remove.

Then you need to shrink the array size.

Only after that you "shrink" the actual md device from 4 to 2 devices for example.

Look at this thread at the rubylaser posts:
[http://ubuntuforums.org/showthread.php?t=1794121](http://ubuntuforums.org/showthread.php?t=1794121)

Note that the cases are not identical, in that thread there is also LVM involved, so just ignore the LVM part.

Also, I have never done mdadm shrinking and maybe it will remove the last disk from the array (I don't see anywhere in the commands an option to specify which disk/partition you want removed when doing the shrinking with --grow). So, you might need to shrink the array in a way that it will throw out the newer devices (which I assume you want to keep, that's why you added them), and then replace the older devices one by one, they way you were supposed to do it originally.

Also, when replacing smaller with bigger disks, never forget you need to replace only one, let the array rebuild (sync), and only then replace the second one. When we say one by one, it doesn't mean right away without waiting for the array to rebuild after you have replaced one disk with a bigger one. It always has to sync fully first.

---

### Post by finni on 2013-01-29
You need not shrink the raid-1 volume physical size or so it seems. Now there is a question of how I should proceed on moving the md0 raid-1 (includes the system) to 2 new disks?

---

### Post by darkod on 2013-01-29
This should be good:
[http://zackreed.me/articles/69-mdadm-replace-smaller-disks-with-larger-ones](http://zackreed.me/articles/69-mdadm-replace-smaller-disks-with-larger-ones)

Notice that his example is with raid5, you have raid1, so you will replace two disks one by one. It's very important to let the array sync after replacing the first disk.

Also, in that example he creates the small array first, you already have an array so you can start from the part saying Replace the first disk.

The new disks in the example are sde, sdg and sdf. That has no meaning, it's only a VBox example. If you remove /dev7sda1, and the new disk/partition is also /dev/sda1, no problem. Add the bigger sda1 back to the array and let it sync. It will work even when the new disk has the same device name as the old one.

EDIT PS: This is also one link:
[http://wiki.linuxservertech.com/faq/index.php?action=artikel&cat=7&id=11&artlang=en](http://wiki.linuxservertech.com/faq/index.php?action=artikel&cat=7&id=11&artlang=en)

Replace all disks with larger drives. That should get you going.

---

### Post by darkod on 2013-01-29
> **finni said:**
> You need not shrink the raid-1 volume physical size or so it seems. 

It looks to me like you only got lucky. Since the system didn't work as you expected after adding the two more disks, maybe there was no data on them.

I would still say the safe way is:
1. Shrink the filesystem first.
2. Shrink the array size.
3. Remove devices.

What if for example you have more data than the 2 disks can hold after you remove the other 2. Where will it fit?

That's why you shrink the filesystem first, because it will not let you shrink it to size smaller than the used data size.

In fact, after adding the disks if you didn't grow the array and the filesystem, they were not even taking the new disks. That's why removing them without any resizing worked.

After you add more disks, you need to grow the array specifically, and also the filesystem. They don't grow automatically just because mdadm says you have 4 devices now in the array.

If you care about your data, NEVER shrink partitions (or raid arrays) without shrinking the filesystem first.

---

### Post by finni on 2013-02-05
Things I did to successfully move the array to new disks:

Edited the /etc/default/grub and uncommented line: (To fix the cycle reset at boot. See link: [http://ubuntuforums.org/showthread.php?t=1661341&page=10](http://ubuntuforums.org/showthread.php?t=1661341&page=10) )
```
GRUB_TERMINAL=console
```

Then I replaced the disks one by one like this:

1. Removed the old partition (disk).
```

$ mdadm --manage /dev/mdX --fail /dev/sdXX
$ mdadm --manage /dev/mdX --remove /dev/sdXX

```
2. Added the new partition (disk). 
```

$ mdadm --manage /dev/mdX --add /dev/sdXX

```
3. Waited for the mdadm finish copying data.
```

$ mdadm -D /dev/mdX

```
4. Updated initramfs.
```

$ update-initramfs -u

```
5. Updated grub
```

$ update-grub

```
6. Installed grub on new disk
```

$ install-grub /dev/sdX

```
7. Rebooted and did the same cycle for another drive. And then I had a fresh and working array using new disks. I removed the old disks after all was done and rebooted once more. All worked OK. :-)

---

