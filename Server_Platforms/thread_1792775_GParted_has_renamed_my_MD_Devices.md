---
title: "GParted has renamed my MD Devices"
date: 2011-06-28
forum: Server Platforms
---

### Post by Spitfire1900 on 2011-06-28
I am running a test installation of Ubuntu 10.04 Server on a Virtual Machine (VBox specifically) in order practice recovering RAID problems. When I initialy created the RAID arrays I created a MD Device named "md0" with an ext4 file system and "/" mount point. My other RAID array was called "md1" and was used for swap.

When loading GParted off of a bootable disk I noticed that the devices were changed from md0 and md1 to md127 and md126. I shut down the VM and on reboot grub rescue shows up saying that disk can not be found and using "ls" lists the MD devices as they appeared in GParted (md127 and md126).

I rebuilt the OS via importing an backup Appliance and repeated the same thing. Boot into Ubuntu, success, then sudo shutdown, boot into GParted, note md device name change, shutdown, boot into Ubuntu, grub rescue.

Is there anyway to stop this from happening(in the event that GParted must be used on a Physical Machine). Or a way to revert the problem after GParted messes the system up?

**Edit:** I talked with one individual who suggested changing the md device names to md 127 and md126, but I am looking for a more robust solution than taking a shot in the dark that GParted will set the same names on other systems. (particularly physical ones).

---

### Post by rubylaser on 2011-06-28
I've never experienced renaming any of my block devices (mdadm devices included) via the Live GParted CD.  It shouldn't effect them unless you've performed actions on them, and even if you did perform an action, it still wouldn't effect the naming of the arrays, as those are given by the ARRAY line in your /etc/mdadm/mdadm.conf file (wouldn't be touched by GParted).

I'll try this out in virtualbox later tonight.

---

### Post by rubylaser on 2011-06-28
Well, I just completed my test.  Here are the steps I took from a fresh Virtual Box VM...

Installed 64 bit Debian Squeeze (I had the mini iso on hand) on a 2GB hard drive
Include 3 1GB test drives for 3 disk mdadm RAID 5 array.
Performed minimal install
Packages installed...
```
apt-get update && apt-get upgrade -y && apt-get install ssh screen mdadm -y
```

fdisk each mdadm disk, and create a partition, set type as 83 (linux)

Setup mdadm array and put it at /dev/md0
```
mdadm --create --metadata 1.2 --verbose /dev/md0 --level=5 --chunk=512 --raid-devices=3 /dev/sd[bcd]1
```

verify that it's in sync
```
watch cat /proc/mdstat
```


```
Every 2.0s: cat /proc/mdstat                            Tue Jun 28 19:55:25 2011

Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sdd1[3] sdc1[1] sdb1[0]
      2087936 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>
```


create proper mdadm.conf file...
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```


Create filesystem on array...
```
mkfs.ext4 -v -m 0 -b 4096 -E stride=128,stripe-width=256 /dev/md0
```

mkdir /storage

mount it in /etc/fstab
```
/dev/md0        /storage           ext4    defaults,noatime,nodiratime,commit=60        0       2
```

create a testfile on /storage
```
dd if=/dev/urandom of=/storage/testfile.out bs=1M count=100
```

md5 checksum the created file...
```
md5sum /storage/testfile.out
96a83275b58cea585dfd2867ba6475a8  /storage/testfile.out
```

Boot into GParted CD, view md device, 
[IMG]http://img.skitch.com/20110629-es34seg28ahwkqjn1mcqccp1uk.jpg[/IMG]

As you can see, the mdadm device shows up as md127.  This happens because the Live CD doesn't have the same mdadm.conf file as your install, so this is the first device that it defaults to.  As long as you don't make changes to the mdadm device, everything is fine.

Next, I rebooted into Debian, view mounted filesystems
```
mount
```

[IMG]http://img.skitch.com/20110629-8fej9xy1wnphe7h838tybf55n3.jpg[/IMG]
As you can see, all is well.  My mdadm device came right back up on /dev/md0 as it was supposed to.
```
root@debian-test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Tue Jun 28 19:53:47 2011
     Raid Level : raid5
     Array Size : 2087936 (2039.34 MiB 2138.05 MB)
  Used Dev Size : 1043968 (1019.67 MiB 1069.02 MB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Tue Jun 28 20:14:33 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : debian-test:0
           UUID : bf714b5e:587979ff:288fc3f5:f5b07d76
         Events : 34

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1

```

Next, I'll cd into /storage and verify md5sum of the testfile.out
```
cd /storage
md5sum testfile.out
```

[IMG]http://img.skitch.com/20110629-etr35kf75qym5nhwjsn7gum6ci.jpg[/IMG]

Everything is a perfect match with what it was prior to booting the live GParted CD.  I'm wondering what you're needing to boot the live cd for.  Is it maintenance on the root hard drive?  Otherwise, there's nothing that can't be done on the running server with either parted or fdisk (if you're trying to partition new disks), with mdadm (raid maintenance, adding new disks, removing failed disks, or adding spares), or with resize2fs of xfs_grow (if you're trying to expand the filesystem to expand to more disk space).

I would guess that you're either trying to make changes to the array via GParted, or that your mdadm.conf file is not properly setup.  I hope that helps :)

---

### Post by Spitfire1900 on 2011-06-29
I do not recall making any changes, in fact that is why a ran the second test; to make sure it wasn't me changing something that broke it. 

I am performing test like removing disks from a RAID 1 array in VirtualBox and then practicing and making sure I can replace those disks and successfully sync the with the already mounted partitions.

On another note, I successfully formatted a new "vm" drive using terminal during one of my tests and got it synced. I guess I might not need GParted after all.

Debian eh? I don't know if using that can yield the same results.

---

### Post by rubylaser on 2011-06-29
Of course Debian yields the same results. Ubuntu is deb based (Debian) :)  I've used both interchangeably for years, including transferring my home RAID6 array (Ubuntu 10.04 LTS Server) from a previous Debian Etch server.  In fact, I run mdadm from the Debian Squeeze repos on my Ubuntu server, so I can have a much newer version of mdadm than the 2.6.7 version that shipped with 10.04.

You certainly don't need the live GParted CD to perform any actions on your mdadm array.  If made changes on your array in GParted, you have just discovered the root of your problems.  You would have changed the UUID of your mdadm array, and as result broke your mdadm.conf file.

Here are the proper steps to remove a failed disk with mdadm (or replace it with a larger drive).
```
mdadm --manage /dev/md0 --fail /dev/sdb1[FONT=monospace]
[/FONT]mdadm --manage /dev/md0 --remove /dev/sdb1

```Then format and add in a new disk...
```
mdadm --manage /dev/md0 --add /dev/sdb1
```The array will re-sync at this point, and you then can preform any filesystem tasks that you need to do (grow the filesystem to take advantage of more disk space, etc).

As a warning, it sounds like you'll want to spend more time to read about and understand mdadm before you trust any important data to it.  mdadm is robust, and proven, but if you don't know how to properly interact with it, you can hose your data very quickly.  Continuing to use VBox to test/learn is a great idea. Any questions you may have through this learning process can be asked on the Forums and someone around here, myself included, will be happy to answer them for you.

---

