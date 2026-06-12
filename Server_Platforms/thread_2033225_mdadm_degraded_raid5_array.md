---
title: "mdadm degraded raid5 array?"
date: 2012-07-25
forum: Server Platforms
---

### Post by blackstripes on 2012-07-25
After rebooting my server this afternoon I noticed that after booting the OS from grub, that the system complained that my raid5 array was degraded.  It offered to boot to a command line, or also offered to start the "degraded" array and ended up booting normally after a quasi-verbose boot.

I'm in the OS now, and things _seem_ to be working normally.  Here is the output of sudo mdadm --detail /dev/md0

```
/dev/md0:
        Version : 1.2
  Creation Time : Sun Apr 29 20:04:55 2012
     Raid Level : raid5
     Array Size : 2930284032 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976761344 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Wed Jul 25 18:18:39 2012
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : fileserver:0
           UUID : ccfd3103:c2db2111:129b52e1:6d5b8fc3
         Events : 4033

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       64        1      active sync   /dev/sde
       3       8       80        2      active sync   /dev/sdf
       4       8       97        3      active sync   /dev/sdg1

```

...and the output of cat /proc/mdstat

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdg1[4] sdf[3] sdc[0] sde[1]
      2930284032 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

```

Does everything appear to be normal?  And idea why the OS (kernel?) is complaining prior to being booted?

Thanks!

---

### Post by blackstripes on 2012-07-25
One other thing, the message at prior to booting into the OS was telling me to set bootdegraded=true to avoid seeing this message.  Obviously I don't want to do that - I want to know why it thinks the array is degraded and fix it. :)

---

### Post by blackstripes on 2012-07-25
Disk utility shows all 4 drives as "Healthy".

Full Disclosure: I have noticed that disk utility seems to think I have two arrays.  I noticed this a while back, and had booted the machine plenty of times without this warning, so I don't _think_ it is related.

[IMG]https://dl.dropbox.com/u/35008053/Screenshot%20from%202012-07-25%2019%3A21%3A10.png[/IMG]

:confused:

---

### Post by blackstripes on 2012-07-28
Bump...

---

### Post by darkod on 2012-07-28
Could you have fakeraid meta data remains on some disks which might get disk utility to think there is another array?

I'm no expert on raid, and I think it's not a problem right now, but I noticed that the four raid5 devices you have, three are whole disks and the fourth is a partition (sdg1). You should be consistent whencreating the array or adding devices later. Either use disks like sda, sdb, sdc for all devices, or partitions marked as raid type like sda1, sdb1, sdc1. Not sure if mixing them can have any consequences.

On the other hand the mdadm details seem to show a fully running raid5 array...

---

### Post by Kleenux on 2012-07-29
Is it the infamous problem related [here]("http://ubuntuforums.org/showthread.php?t=1861516&page=2") (See dangriffin's post)

---

### Post by blackstripes on 2012-08-10
> **Kleenux said:**
> Is it the infamous problem related [here]("http://ubuntuforums.org/showthread.php?t=1861516&page=2") (See dangriffin's post)

Thanks! I've at work, but during some downtime ssh'd into the box and after making the change, and rebooting the machine the box is back online, so it looks like it did work!  

I'm unable to confirm that the disk utility is no longer showing that strange second array, although I'm a little skeptical that the change I made had any impact on that.

---

### Post by blackstripes on 2012-08-10
> **darkod said:**
> Could you have fakeraid meta data remains on some disks which might get disk utility to think there is another array?

I'm no expert on raid, and I think it's not a problem right now, but I noticed that the four raid5 devices you have, three are whole disks and the fourth is a partition (sdg1). You should be consistent whencreating the array or adding devices later. Either use disks like sda, sdb, sdc for all devices, or partitions marked as raid type like sda1, sdb1, sdc1. Not sure if mixing them can have any consequences.

On the other hand the mdadm details seem to show a fully running raid5 array...

Thanks for the comment.  I wonder if you are correct about the metadata on other disks?  Any thoughts as to how I could look into that theory?

As for the architecture of my raid array, I was using whole disks with the 1TB drives, and then later threw a 1TB partition of a 2TB drive into the mix to add space.  What kind of problems am I setting myself up for?

---

### Post by rubylaser on 2012-08-10
> **blackstripes said:**
> Thanks for the comment.  I wonder if you are correct about the metadata on other disks?  Any thoughts as to how I could look into that theory?

As for the architecture of my raid array, I was using whole disks with the 1TB drives, and then later threw a 1TB partition of a 2TB drive into the mix to add space.  What kind of problems am I setting myself up for?

You aren't setting yourself up for problems mixing whole disks and partitions with mdadm other than the confusion it might cause, and you "might" end up with a new disk not being large enough to add to your array (a few MB too small).

---

### Post by darkod on 2012-08-10
You remove fakeraid (hardware raid) meta data with:
sudo dmraid -E -r /dev/sda

Change /dev/sda with the correct disk. If it finds meta data it asks for permission to remove it. If you only want to check whether it finds something, you can say No when it asks you if you want to remove it.

Also, I think dropping the -E option only checks for meta data without trying to remove it or asking you for permission, but I'm not 100% sure about this.

rubylaser is the expert on raid so he might know if trying to remove fakeraid meta data can mess up the mdadm. In theory, I believe they are separated and not related, but who knows...

---

### Post by rubylaser on 2012-08-11
> **darkod said:**
> You remove fakeraid (hardware raid) meta data with:
sudo dmraid -E -r /dev/sda

Change /dev/sda with the correct disk. If it finds meta data it asks for permission to remove it. If you only want to check whether it finds something, you can say No when it asks you if you want to remove it.

Also, I think dropping the -E option only checks for meta data without trying to remove it or asking you for permission, but I'm not 100% sure about this.

rubylaser is the expert on raid so he might know if trying to remove fakeraid meta data can mess up the mdadm. In theory, I believe they are separated and not related, but who knows...

I know mdadm very well, but only know dmraid via Google (I've never used it myself).  I do not know where it writes it's metadata info.  They should be in a different location on the disks, but I don't know that.  So, although it appears from Google that your command will remove dmraid superblock info, I'm not sure if it will damage the mdadm superblock info.

If it does, the OP should be able to re-create the array with the same metadata version, disk order, and chunk size with the --assume-clean flag.  But, I'd definitely have a backup before I tried that on an array that appears to be working fine now (other than the second dmraid array).

---

