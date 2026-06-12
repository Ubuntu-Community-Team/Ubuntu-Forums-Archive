---
title: "total newb here with raid questions"
date: 2008-06-04
forum: Server Platforms
---

### Post by kosmokramer314 on 2008-06-04
I setup a raid1+0 on my first two 9.1GB hdd's, and a raid5 on the other four 18.1GB hdd's. I have a total of six hdd's.


I have Hardy Heron installed and running properly, but when I checked available disk space it says I only have 7.9GB total of which 3.2 is used and 4.7 available.

when I was installing I chose to have the partitions set up automatically and it showed that /ext3 was on raid1+0 and that /swap was on raid5

my question then is why am I not utilizing the storage space on the raid5??  I am fairly certain that I simply need to mount the hardware or repartition so that it's recognized, but I want to see if anyone has the right answer.

I'm jumping head first into all of this after using windows my whole life, so go easy on me because I'm not that familiar with using the terminal.  Also I am using a compaq ML370 server.  

THANKS FOR THE HELP IN ADVANCE!!!

---

### Post by quelx on 2008-06-04
> **kosmokramer314 said:**
> I setup a raid1+0 on my first two 9.1GB hdd's, and a raid5 on the other four 18.1GB hdd's. I have a total of six hdd's.

raid 1+0 requires 4 physical drives (two mirrored drives that are striped with another mirrored pair)  I guess you could do that 4 partitions with **mdadm** but I don't know what good that is.

> I have Hardy Heron installed and running properly, but when I checked available disk space it says I only have 7.9GB total of which 3.2 is used and 4.7 available.

Sounds like Ubuntu is only on the raid1+0 can you post output from these 3 commands```
sudo fdisk -l
mount
cat /proc/mdstat
```

---

### Post by kosmokramer314 on 2008-06-04
I'm at work right now, but I will definitely reply with that info when I get home tonight.  What raid configuration should I use if I want to only use two hdd's one mirror of the other?  

I originally started out with a raid0 and had a drive fail on me, so I won't make that mistake again.

thanks again for looking into this!

---

### Post by quelx on 2008-06-04
> **kosmokramer314 said:**
> I'm at work right now, but I will definitely reply with that info when I get home tonight.  What raid configuration should I use if I want to only use two hdd's one mirror of the other?

I would do it as you did, I am confused about the raid1+0, I'm curious how you set that up with only two drives.  Without knowing the details, I would do a simple raid1 with the 9.1GB and keep the others as you have them.  

*If* speed is an issue, you could raid0 the 9.1's and mirror (not with the hardware, but **rsync** or some interval backup scheme) to a bootable partition on the raid5 array. If you lost the raid0 you could boot the raid5, until the raid0 failed you could get the speed boost.  I don't think that's worth it, but maybe you could use the extra read/write speed.

---

### Post by kosmokramer314 on 2008-06-05
***OUTPUT FROM sudo fdisk -l COMMAND:

Disk /dev/ida/c0d0: 9091 MB, 9091153920 bytes
255 heads, 63 sectors/track, 1105 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00067dfe

         Device Boot      Start         End      Blocks   Id  System
/dev/ida/c0d0p1   *           1        1052     8450158+  83  Linux
/dev/ida/c0d0p2            1053        1105      425722+   5  Extended
/dev/ida/c0d0p5            1053        1105      425691   82  Linux swap / Solaris

Disk /dev/ida/c0d1: 54.6 GB, 54609592320 bytes
255 heads, 32 sectors/track, 13071 cylinders
Units = cylinders of 8160 * 512 = 4177920 bytes
Disk identifier: 0xf04d8dff

Disk /dev/ida/c0d1 doesn't contain a valid partition table


***OUTPUT FROM mount COMMAND:

/dev/ida/c0d0p1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-17-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

***OUTPUT FROM cat /proc/mdstat COMMAND:

cat /proc/mdstat

---

### Post by quelx on 2008-06-05
```
Disk /dev/ida/c0d1 doesn't contain a valid partition table
```

So your second drive (raid5) is not being used at all, how did you want your partitions setup, what did you want installed/stored on the raid5?

---

### Post by kosmokramer314 on 2008-06-05
what I was attempting to accomplish is to have linux running strictly on the raid1+0 and teh raid5 would be for everything else....

---

