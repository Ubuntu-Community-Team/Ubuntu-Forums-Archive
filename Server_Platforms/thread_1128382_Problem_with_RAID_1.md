---
title: "Problem with RAID 1"
date: 2009-04-17
forum: Server Platforms
---

### Post by Jack Thomson on 2009-04-17
I installed Ubuntu Server 7.10 using RAID 1 as a home server and all was well for a year and a halt. Then it wouldn't boot up and one of the hard drives started making funny clicking noises. So I manually removed the hard drive that was making the noises and it booted up fine again so obviously the hard drive was bust.

I've got another hard drive now and want to set up the RAID 1 again however I can't seem to be able to do this. I've plugged the hard drive in and I think it's being recognised as /dev/md1 and /dev/sdb are appearing when it's plugged in. However when I run the following command *sudo mdadm --query --detail /dev/md1* I get

[FONT="Lucida Sans Unicode"]mdadm: md device /dev/md1 does not appear to be active.[/FONT]

If I run *sudo mdadm --query --detail /dev/md0* I get

[FONT="Lucida Sans Unicode"]/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Nov 17 20:05:55 2007
     Raid Level : raid1
     Array Size : 483492096 (461.09 GiB 495.10 GB)
  Used Dev Size : 483492096 (461.09 GiB 495.10 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Apr 17 18:22:25 2009
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 66d7837f:8edab322:b747be23:29f1f006
         Events : 0.799817

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed [/FONT]

I'm not an Ubuntu expert so I'm sure I'm missing something obvious. But I'd be grateful if anyone could help.

---

### Post by Wayne_V on 2009-04-17
can you 'cat /proc/mdstat' ?

---

### Post by Jack Thomson on 2009-04-17
Sure. It gives

[FONT="Lucida Console"]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : inactive sda2[0](S)
      4891712 blocks

md0 : active raid1 sda1[0]
      483492096 blocks [2/1] [U_]

unused devices: <none>[/FONT]

---

### Post by Wayne_V on 2009-04-17
So you have two md devices - md0 is sda1/sdb1 and md1 is sda2 - but inactive, is it swap?  You need to partition the new disk to match the old one (fdisk or parted) and then remirror the partitions:

# mdadm /dev/md0 --add /dev/sdb1

Then cat /proc/mdstat again and you should see them remirroring.

Does 'swapon -s' show /dev/md1 is swap?

---

### Post by Jack Thomson on 2009-04-17
*sudo mdadm /dev/md0 --add /dev/sdb1 *gives 

[FONT="Lucida Console"]mdadm: cannot find /dev/sdb1: No such file or directory[/FONT]

If I try *sfdisk --d /dev/sda | sfdisk /dev/sdb* I get

[FONT="Lucida Console"]
sfdisk: cannot open /dev/sdb read-write[/FONT]

*swapon -s* gives nothing...

[FONT="Lucida Console"]Filename                                Type            Size    Used    Priority[/FONT]

I'm not even sure it's mounted correctly so I tried *mount* and it gives

[FONT="Lucida Console"]/dev/md0 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)[/FONT]

---

### Post by Wayne_V on 2009-04-17
You need to partition the new drive before you can add it back in.  

You must be root to run sfdisk:

$ sudo -s
# [I]sfdisk --d /dev/sda | sfdisk /dev/sdb

Do you have any swap listed in /etc/fstab?   Does 'sudo swapon -a' mount it?


[/I]

---

### Post by Jack Thomson on 2009-04-19
Not sure why sfdisk wasn't working but I used fdisk to create the partitions and then used *mdadm /dev/md0 --add /dev/sdb1* and the disks started synching. :D

I had a little more problem with md1 but I found a thread which recommended I used *mdadm --assemble --scan --force* and then I was able to add sdb2 to md1.

All is well now. *cat /proc/mdstat * gives

[FONT="Lucida Console"]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb2[1] sda2[0]
      4891712 blocks [2/2] [UU]

md0 : active raid1 sdb1[1] sda1[0]
      483492096 blocks [2/2] [UU][/FONT]

Many many thanks! \\:D/

/Salute

---

