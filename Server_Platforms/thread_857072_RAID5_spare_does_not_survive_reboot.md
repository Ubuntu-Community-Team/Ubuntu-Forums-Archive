---
title: "RAID5 spare does not survive reboot"
date: 2008-07-12
forum: Server Platforms
---

### Post by JanCeuleers on 2008-07-12
I'm having the problem that the spare disks on two of my arrays aren't automatically being added upon reboot. I can do so manually with mdadm --add (which causes the spare to be re-added, not just added).

I'd like this to be done automatically. Obviously I can do so in /etc/rc.local but I'd prefer to solve the underlying problem such that the machine will still boot in the event of a degraded array situation.

A bit of background:

I started out with four 320GB disks, each identically partitioned as follows:

```

root@via:~# sfdisk -l /dev/sda

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+    121     122-    979933+  fd  Linux raid autodetect
/dev/sda2        122   38912   38791  311588707+  fd  Linux raid autodetect
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
```

The four large partitions were used to construct a RAID5 array without spares (although the info below does show the spare that I've since added):

```
root@via:~# mdadm --detail /dev/md2
/dev/md2:
        Version : 00.90.03
  Creation Time : Fri Jun 22 20:56:51 2007
     Raid Level : raid5
     Array Size : 934765824 (891.46 GiB 957.20 GB)
  Used Dev Size : 311588608 (297.15 GiB 319.07 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Sat Jul 12 10:06:41 2008
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 714e46f1:479268a7:895e209c:936fa570
         Events : 0.13758

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
       2       8       34        2      active sync   /dev/sdc2
       3       8       50        3      active sync   /dev/sdd2

       4       8       82        -      spare   /dev/sdf2
```

The smaller partitions were turned into two RAID1 arrays, used as two swap partitions with equal priority:

```
root@via:~# mdadm --detail /dev/md[01]
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Jun 22 20:56:08 2007
     Raid Level : raid1
     Array Size : 979840 (957.04 MiB 1003.36 MB)
  Used Dev Size : 979840 (957.04 MiB 1003.36 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jul 12 08:47:50 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 19e69537:f7a6aec8:5a5f7576:3fc29e0d
         Events : 0.50

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1
/dev/md1:
        Version : 00.90.03
  Creation Time : Fri Jun 22 20:56:31 2007
     Raid Level : raid1
     Array Size : 979840 (957.04 MiB 1003.36 MB)
  Used Dev Size : 979840 (957.04 MiB 1003.36 MB)
   Raid Devices : 2
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Jul 12 08:07:54 2008
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

           UUID : 5e728621:c8b356a8:01f8e270:f0e280cb
         Events : 0.54

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       49        1      active sync   /dev/sdd1

       2       8       81        -      spare   /dev/sdf1
```

So: how to I get the spares to automatically be re-enabled upon reboot?

I also want the /dev/sdf1 spare to migrate between /dev/md0 and /dev/md1 if the other array is degraded. To this end I've added spare-group definitions to /etc/mdadm/mdadm.conf, but I'm not sure that file is actually being used for anything.

Just for reference I include /etc/mdadm/mdadm.conf below.

```
root@via:~# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=19e69537:f7a6aec8:5a5f7576:3fc29e0d spare-group=swapgroup
ARRAY /dev/md1 level=raid1 num-devices=2 spares=1 UUID=5e728621:c8b356a8:01f8e270:f0e280cb spare-group=swapgroup
ARRAY /dev/md2 level=raid5 num-devices=4 spares=1 UUID=714e46f1:479268a7:895e209c:936fa570

# This file was auto-generated on Fri, 22 Jun 2007 19:12:10 +0000
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $
MAILFROM root
```

Thanks!

---

### Post by fjgaude on 2008-07-12
The only thing I've noticed in your data is the UUIDs (generated by mdadm in the mdadm.conf file) don't seem right. Are they?

I don't have any suggestions other than to study the docs at:

/usr/share/doc/mdadm/FAQ.gz  and md.txt.gz

You might try some different arrangement for the spare-group... likely the problem is therein.

Good luck!

---

### Post by JanCeuleers on 2008-07-12
Well spotted! Thanks very much; I'll report back here on whether this is the problem when I next reboot the server.

Cheers, Jan

---

### Post by JanCeuleers on 2008-07-20
I have now rebooted the machine following the correction of the UUID mismatch in /etc/mdadm/mdadm.conf

The problem is NOT solved: spare disks are still not being automatically added to arrays on boot.

I'd be grateful for any other hints.

---

### Post by fjgaude on 2008-07-21
Have you read, studied this:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)

I can't see anything wrong with what you have showed... you might try some different arrangement for the spare-group... likely the problem is therein... good luck!

---

### Post by JanCeuleers on 2008-07-27
It appears that this problem was caused by the "DEVICE partitions" line in /etc/mdadm/mdadm.conf

I have replaced it with the following:

```
DEVICE /dev/sd[abcdef][12]
```

and now the spares are automatically added to the arrays on boot.

Thanks to all who helped.

---

### Post by fjgaude on 2008-07-27
That's good to know... we learn something new daily! Thanks for fixing your own problem.

---

### Post by djamu on 2008-07-27
Hi
By coincidence I stumbled upon this thread, thought I might give you some undocumented info & advice, in case you ever have to rebuild your array(s), a must read to keep those in good health.

[[COLOR="Navy"]MDADM UUID / superblock ,superblock on /dev/nnn doesn't match[/COLOR]]("http://ubuntuforums.org/showthread.php?t=410136")

[[COLOR="Navy"]MDADM: .... has same UUID but different superblock to[/COLOR]]("http://ubuntuforums.org/showthread.php?t=405782")



Some questions in regard to your install.

Is there a good reason why you are using 2 swap partitions instead of 1 large as I fail to see any advantage in that? 
Because you seem concerned about keeping your data at all cost is there any specific reason why you went for a 4+1 raid5  configuration instead of a 5 disk raid6, as both give you the same amount of raw disk space?



The difference between raid5 and raid6 is that a raid6 gives higher redundancy. ( 2 disks may fail simultaneously ).
What I'm trying to say is this, 
case > **raid 5 with 1 spare**.
As soon as 1 disk fails the spare will start synchronizing, but meanwhile as this will take some time ( especially with large disks )
**your array will have no redundancy until synchronizing is finished** if for any reason another disk fails at this point > your data is a goner.....

not so for **raid6** > as soon as 1 disk fails, your array will continue working as a raid5 without losing redundancy at any given moment.



It's worth noting that you can partition an MD device -now you use it as a large unpartioned superfloppy / USB disk-, instead of partitioning your disks prior creating MD devices.
In other words you can create 1 large array ( /dev/md0 ) which you partition afterward. ( the opposite of what you did now ) The advantage of this is that it saves the troubles of having to configure a spare with matching partitons .... > you ( or someone else with no specific knowledge of your setup ) can then just put in another disk in case of failure...



Please note the differences in syntax between disk and array devices.
While > 
/dev/sda1 is the 1st partition of /dev/sda
/dev/md1 is **NOT** the first partition of /dev/md ( neither is /dev/md0 )

syntax for a partitioned MD array is
/dev/md1p1 as 1st partition of /dev/md1



Use cfdisk for this ( not fdisk ) cfdisk is much easier.
and as always keep in mind that partitioning any device will kill the data on it.
so backup the array before partitioning it.
usage```
sudo cfdisk /dev/md0
```



Instead of partitioning an array you can also install EVMS or LVM on it > gives you the advantage of being able to create rotating snapshots and detaches your physical disks from your storage layer. ( probably a little far-fetched for your setup ).



Just my 5 cents of good advice.



):P

---

### Post by JanCeuleers on 2008-07-27
First of all, I opened a bug about this issue: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/252365](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/252365)

Djamu,

Thanks for your suggestions.

The reason for my set-up is that I started out with 4 disks and only added the other two later. This determined my choice of RAID5 over RAID6.

The two small RAID1 arrays are mounted as swap partitions with equal priority. This causes the kernel to stripe swap space between these two arrays. I chose this for the following reasons:

- identical layout of the four disks
- I didn't want to swap to RAID5 for performance reasons
- better resilience: if two disks fail the system still has a 50% chance of surviving (but the RAID5 array will be dead)

As I bought sde and sdf later they are less likely to fail at the same time as the first four. Furthermore, they are normally spun down. That's another reason why RAID5 is preferable: lower power consumption (only 4 drives are spinning instead of all 6).

Cheers, Jan

---

### Post by djamu on 2008-07-27
K, let me clear up some widespread misconceptions about RAID.
Unlike what most "pro's" say there's nearly no performance difference between a 4 disk raid0 stripe and a 5 disk raid5.
The very simple reason is that a raid5 is also a stripe featuring redundancy, so performance on reading will almost be equal ( the redundancy check is a simple XOR ( eXclusive OR ) operation... writing might be a little slower as there are 2 write cycles ( the data + parity check )

> **JanCeuleers said:**
> 
...This causes the kernel to stripe swap space between these two arrays. I chose this for the following reasons...


So IMHO waste of resources..

> 
- identical layout of the four disks
- I didn't want to swap to RAID5 for performance reasons
- better resilience: if two disks fail the system still has a 50% chance of surviving (but the RAID5 array will be dead)


I just posted a topic about another misconception in RAID partitioning .. 
People tend to partition disks in order too create arrays.. This is just plain wrong.. because not all data will be redundant, your data will, but not your partition scheme ...
see my post [[COLOR="Navy"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5469131#post5469131") 
better is to partition your array ( the very opposite, fail for those howto's )

> 
They are normally spun down. That's another reason why RAID5 is preferable: lower power consumption (only 4 drives are spinning instead of all 6).


are you sure about that ? very likely to depend on controller type / power management installed / enabled..
onboard electronics will always be active.. motor spindle doesn't consume much.. most energy is used with head seeking ( which does it very violently, if you ever have the chance to see )


;)

---

### Post by kwisher on 2009-07-10
Hello All,

Stumbled upon this thread searching for a solution to a similar situation. I recently built a home server for a customer using 3 identical 1TB Seagate drives in a raid-5 array. This is my first attempt at any type of raid except for a raid-0 setup I had a few years ago. I used this how-to for my reference:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID")

This how-to does not mention anything about setting up one disk as a spare. I enabled the email notification from mdadm and have been receiving messages as below:

```
This is an automatically generated mail message from mdadm
running on doud-server

A SparesMissing event had been detected on md device /dev/md0.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sdd1[2] sdc1[1]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
```

Is this something I should be concerned about? If so, how do I fix this without compromising any data?

TIA

---

### Post by djamu on 2009-07-10
> **kwisher said:**
> 
```
This is an automatically generated mail message from mdadm
running on doud-server

A SparesMissing event had been detected on md device /dev/md0.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sdd1[2] sdc1[1]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
```



does a mail with subject 
```
DegradedArray event on /dev/md0
```
was followed by the one you posted ?

if not
did you create the array with a "missing" disk ? > to prevent premature resyncing 
and did you add the "missing" later on ?  

in that case this is a normal message stating that the spare disk you added is now active and in use by the array 

as a side note > it might be tempting to create a swap partition on a raid0/1/5/6
but don't do it! whenever by chance your mdadm module gets swapped out .... your computer will lockup


;)

---

### Post by kwisher on 2009-07-11
> **djamu said:**
> does a mail with subject 
```
DegradedArray event on /dev/md0
```
was followed by the one you posted ?

if not
did you create the array with a "missing" disk ? > to prevent premature resyncing 
and did you add the "missing" later on ?  

in that case this is a normal message stating that the spare disk you added is now active and in use by the array 

as a side note > it might be tempting to create a swap partition on a raid0/1/5/6
but don't do it! whenever by chance your mdadm module gets swapped out .... your computer will lockup


;)

No, this is the only message I receive. The array was created with all 3 disks. I have a separate HD with the O/S and swap partition on it.

---

### Post by djamu on 2009-07-11
mmm,

Can you post the contents of /etc/mdadm/mdadm.conf?

**keep in mind the individual UUID's of the array components/devices are not the same ones as used by the MD devices and needed by for example fstab / menu.lst etc.. **
each device has it's own UUID meaning /dev/md0 has a different UUID as /dev/sda1 ( which might be part of former )
to check which UUID is used by your md devices do 
```
ls -l /dev/disk/by-uuid/
```

as a reference I'll post one of my mdadm configs > the one of my main storage

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=314e409e:375c3aa8:247e84d4:8ea7b4e9
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=0f16aecc:01420a0a:c2880a56:8d20eddf
ARRAY /dev/md2 level=raid6 num-devices=10 UUID=51536667:a1d89dc7:c230666b:5103eba0
# This file was auto-generated on Thu, 21 Jul 2008 18:16:02 +0200
# by mkconf $Id$

```
I've configured postfix to pick up these mails and send them to a real email adress 


there's 2 raid1 array for faster concurrent access 
md0 = / my system and boot partition
md1 =  my database 
md2 = large storage array with raid6

maybe it's worth to recreate this config
so delete your original and recreate it using
```
sudo rm /etc/mdadm/mdadm.conf
sudo mdadm --assemble --scan

```

then lastly do
```
sudo dpkg-reconfigure mdadm
```
to re-configure mdadm itself and recreate your initramfs
( depending on your preference you can opt to chose whether or not your system should continue to work in case of disk failure > yes for me )

if the problem still persists after this > reconfigure postfix, as it might be a recurrent mail that gets send over and over....

lastly if nothing seems to work > purge mdadm 
```
sudo apt-get purge mdadm
reboot 
sudo vi /etc/apt/sources.list ( comment out your CD source > might be a corrupt CD image )
sudo apt-get install mdadm ( and reconfigure with the instructions above )

```

good luck

):P

---

### Post by kwisher on 2009-07-11
```
# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=48f50736:6f2c84a7:f757593b:1e46e20b
   spares=1

# This file was auto-generated on Sun, 28 Jun 2009 21:00:31 -0400
# by mkconf $Id$
```

In the how-to I mentioned in my original post, it said to create the file /etc/mdadm.conf file. Which file does mdadm use, /etc/mdadm.conf or /etc/mdadm/mdadm.conf?

Also, what exactly is a spare disk? Is this the disk that contains the parity? Is it necessary? What is it's purpose?

Thanks for your help.

---

### Post by djamu on 2009-07-11
> **kwisher said:**
> 
In the how-to I mentioned in my original post, it said to create the file /etc/mdadm.conf file. Which file does mdadm use, /etc/mdadm.conf or /etc/mdadm/mdadm.conf?

depends a bit on the linux flavor.
On Debian(and Ubuntu) it's in /etc/mdadm/mdadm.conf

> 
Also, what exactly is a spare disk? Is this the disk that contains the parity? Is it necessary? What is it's purpose?
Thanks for your help.

A spare disk is just a spare disk nothing more nothing less. It's just a disk that is known to be available.
a raid array with a dedicated parity disk is a RAID4
RAID5 uses a rotating parity > parity is evenly distributed across the other disks.

I'll elaborate the spare concept with a couple of examples

**Case1** > complete working array ( not degraded ) before adding a spare

```
cat /proc/mdstat
```
shows 
```
debian:~# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sda1[0] sdc1[2] sdb1[1]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>

```

when I add a disk (spare ) to this array with 
```
sudo mdadm /dev/md0 --add /dev/sdd1
```

the result of cat /proc/mdstat is
```
debian:~# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sdd1[3][S] sda1[0] sdc1[2] sdb1[1] 
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]


```

this shows that /dev/sdd1 is now assigned to /dev/md0 but inactive > mind the [S] behind sdd1 > Spare
so whenever either sda1 / sdb1 / sdc1 fails sdd1 will take over immediately



**Case2** > degraded array ( either by a failing disk or by an incomplete create > which might sometimes be very convenient ) before adding a spare / resyncing

```
cat /proc/mdstat
```
shows 
```
debian:~# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sda1[0] sdc1[2]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [2/3] [U_U]

unused devices: <none>

```

in this case sdb1 failed > which is also indicated by the [U_U] ( missing 2nd U )

when I add a disk (spare) to this array with 
```
sudo mdadm /dev/md0 --add /dev/sdd1
```

the result of cat /proc/mdstat will be
```
debian:~# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sdd1[1] sda1[0] sdc1[2]  
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

```

Then disk won't act as a spare but will be active immediately


This is only a very simple example
Spare disks can be arranged in pools ( for very large/complex setups ) and be dynamically assigned to the array that needs them


**A note on performance**
In contrast to popular belief and what so called "experts" say a raid5 with n+1 disks isn't notably slower then a raid0 with n disks, where n is the amount of disks.
RAID0/3/4/5/6 are all striped block devices where RAID3/4/5/6 adds parity (dual parity for RAID6)
writing is a little slower on RAID3/4/5/6 as there are 2 write cycles ( for the parity )

throughput speed goes up (almost) linear with every disk added in the array on single file read / writes.
but seek / access times for raid0/5/6 are always <= access/seek times of the slowest disk in the array

in other words > raid0/5/6 work synchronized ( all disks work in tandem ) and this is also a bottleneck whenever a lot of concurrent files need to be accessed ( a mailserver for example )

for this a RAID1 ( mirror ) might be a better solution as it can(*) read ( not write ) data independently.
So while the absolute throughput is always <= a single disk 
concurrent access will go up with each disk added
(*) this actually depends on the type of controller either software / hardware > mdadm does do this...

RAID10 and RAID01 are actually hybrids 
but a RAID10 <> RAID01    ( former is a striped mirror / latter is a mirrored stripe )

more reading and nice graphs

[http://en.wikipedia.org/wiki/Raid4](http://en.wikipedia.org/wiki/Raid4)
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by kwisher on 2009-07-11
Thanks for the very informative post!!

After my last post, I removed the "spares=1" line in my mdadm.conf and I am no longer receiving email alerts.

One last question:
Without a spare disk, do I have redundancy in case of a drive failure? Will I be able to swap in a new drive and rebuild the array without losing data?

---

### Post by djamu on 2009-07-12
> **kwisher said:**
> Thanks for the very informative post!!

After my last post, I removed the "spares=1" line in my mdadm.conf and I am no longer receiving email alerts.

One last question:
Without a spare disk, do I have redundancy in case of a drive failure? Will I be able to swap in a new drive and rebuild the array without losing data?

The line "spare=1" in mdadm.conf doesn't indicate redundancy, because a (complete) raid5 in itself is redundant ( it has parity ), this line just enforces a mailing for whenever you start to run out of spare ( reserve ) disks.
For example if you have a big array with 30disks ( or 5 arrays with each 6 disks ) and 5 spare reserve disks ( in a pool ) then mdadm will notify you whenever you have only 1 disk left in reserve.
In your case you could have a Raid5 with 3 disks and 10 spare disks > within 5 years ( lol ) a couple of disks will fail and some spares will take over transparently. mdadm will notify you when you have only 1 reserve disk left 

This answers also your last question > You have redundancy as long as your array is complete and synced. ( syncing is calculating redundancy and spreading that parity data accross the array )
Redundancy is not needed to correctly operate your array ( the very purpose of raid1/3/4/5/6 ). And you don't have to wait either for an array to be fully synced to use it. ( or format it ).



**note:**

Raid5+1 ( raid5 +1 spare ) vs Raid6

Both require a minimum of 4 disks, the main difference is that whenever a disk fails in Raid5 it starts rebuilding the array using the spare disk. While doing that your array doesn't have redundancy (syncing large disks takes a couple of hours). If you get another fail in that timespan > your data is toasted.

Not so with a Raid6 > Since it has dual parity
So whenever a disk fails in a Raid6 array, the array will continue to operate as a Raid5 until you add the replacement disk.

While it is unlikely that 2 disks fail in a timespan of a couple of hours, it's not impossible ( I've been so unlucky to face that already )


If you ever have to rebuild your raid3/4/5/6 array ( with data on it ) > Always use the "missing" statement !!! This is **very important** because mdadm won't know how the parity is spread > syncing a wrong assembled array will permanently erase your data. > There's a bunch of posts from me on the this forum concerning that 
example: if you had an array md0 consisting of /dev/sda1 /dev/sdb1 /dev/sdc1 and rebuild it as follows 
> mdadm /dev/md0 --create --level=5 --raid-devices=3 --assume-clean /dev/sda1 /dev/sdb1 **missing**

The missing statement will prevent the array from re-syncing > if the array mounts and the OS recognizes a valid file system you can safely add the last disk, if it doesn't mount you can recreate it using a different combination 
for example > mdadm /dev/md0 --create --level=5 --raid-devices=3 --assume-clean /dev/sda1 **missing** /dev/sdb1
**use 2 missing statements for a raid6**

never ever ever ever !!!! use fsck on an array that refuses to mount after such a rebuild until you're 100% sure it was rebuild correctly > check my other posts regarding this issue..


**A couple of guidelines with fresh arrays** 

Not very known to people is that new disks do a write /read cycle for all data passing through for the 10 first power  cycles ( 10 times powering on/off your computer ). This is because disks tend to fail either very early or very late in their lifespan.
This means that the very first times you benchmark the array it will be slower ( if those disks have less then 10 power cycles ).
It also means that it is a good idea to completely overwrite them a couple of times with garbage data.

> All disks have bad blocks but you won't find them as the internal logic of the drives dynamically remaps data to other areas ( a modern drive has spare sectors ).

Writing garbage data to to full extent of the disk will prematurely map those areas. 

So to be fully on the safe side.
do this once or twice before creating the array and on the full disk not the partition only > use /dev/sda not /dev/sda1.
Not all data on the disk is redundant in a raid1/5/6 > the MBR and partition table are not... Using the full disk ensures that non redundant areas are also checked.

**This will completely destroy any data on disk so pay attention for typing mistakes**
```
dd if=/dev/random of=/dev/sda bs=64k 
```
do this for each physical disk > It writes random data to the disk. And end with
```
dd if=/dev/zero of=/dev/sda bs=64k 
```
Which just blanks the disk.
This will take a while, but it's well worth it...
You can do this on an existing array, by removing a disk > checking it > re-adding it ( wait until it's resynced ) and moving up with the next one.
Any weakness will show and you can RMA your (new disk) if needed.

It is also wise ( maybe a bit exaggerated )to use disks of different batches > meaning not bought all at once.
This will prevent disks to (all) fail because of production error.


**a note on hot/cold-swapping** 

> While sata disks where designed to be hot/cold-swappable, this is only true when using the 15pin power connector without a Molex ( 4 pin adapter ).
In general disks don't need the 3.3V (5th wire) supplied by the 15Pins SATA connector, but still use this to detect a power interuption ( hot removing disks )

The difference between hot/cold swap is that with a hot swap you just can remove the disk whenever you like ( computer on ).
With a cold swap you tell mdadm ( or whatever controller ) first you are going to remove that disk ( mdadm /dev/md0 --fail /dev/sda1 --remove /dev/sda1 ) and then remove the disk while the computer is running.


**Power supplies**

A decent power supply is an absolute necessity. ( 8-10W / disk (on the 12V rail) in general is enough > might be smaller / larger depending on disk type ).
There are some people which I helped before here on the forum  who thought they could use a couple of old PSU's mixed on their array. ( 1 PSU for the first 5 disks another on the 5 next for example )
This is very dangerous as those power-supplies are transformerless ( high freq. switched ). In other words instead of transforming current they'll switch current very fast on/off and by doing so approximate the required voltage. ( like a light dimmer but faster )
The problem when using 2 ( or more ) unmodified PSU's is that switching will then be asynchronous and higher then required voltages may arise ( destroying your logic ).
Proper shunting and filtering may fix that, but requires more then basic knowledge of electronics......



:popcorn:

---

### Post by kwisher on 2009-07-12
You have provided me with information I wish had known before I gave this server to my customer. I guess I could still do the disk write & blanking. I somewhat understand the commands to add & remove disks from the array, but I would feel better if you would provide me with specific command line instructions to do this so that I don't lose any data. Here is the array info:

```
# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sdd1[2] sdc1[1]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
```

Once again, thanks for your help. I have learned more about RAID in this post than I have taking classes at the local community college.

---

### Post by djamu on 2009-07-12
> **kwisher said:**
> You have provided me with information I wish had known before I gave this server to my customer. I guess I could still do the disk write & blanking. I somewhat understand the commands to add & remove disks from the array, but I would feel better if you would provide me with specific command line instructions to do this so that I don't lose any data. Here is the array info:

```
# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sdd1[2] sdc1[1]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
```

Once again, thanks for your help. I have learned more about RAID in this post than I have taking classes at the local community college.

:lolflag: 


k,
removing / blanking / re-adding disks on a live system 
( good finger practice )

proper removing from the array is as follows and you can start with any disk ( but not all at once [-X ) 
so in your case you'll have to perform following 3 times each with a different disk.

```
sudo mdadm /dev/md0 --fail /dev/sdb1 --remove /dev/sdb1 
```

this will first set that specific disk as faulty and will then remove it from the array ( your system should continue working )

overwrite it using the previously mentioned commands
```
sudo dd if=/dev/random of=/dev/sdb bs=64k && dd if=/dev/zero of=/dev/sdb bs=64k
```

pay attention that your not using partitions but the whole disk
( dev/sdb instead of /dev/sdb1 )
 > do not do this if there's multiple partitions on the disk from which one might contain non redundant data.

blanking isn't really necessary, but I suggest that you not skip it in case a random sequence might actually resemble a real disk structure ( highly unlikely but you never know )

repartition the disk using fdisk or cfdisk ( cfdisk is easy )
```
sudo cfdisk /dev/sdb
```

re add that disk to the array
```
sudo mdadm /dev/md0 --add /dev/sdb1
```

and wait until it's finished resyncing 
> use 
```
cat /proc/mdstat
```
takes a while, don't wait for it, you can use the array without a problem while it's resyncing

do this for all disks.



other usefull mdadm options

```
sudo mdadm /dev/md0 --detail
```

prints detailed info from the array


```
sudo mdadm -E /dev/sdb1
```
prints detailed info from members of an array


**Booting raid arrays:**
In general you can't boot from a raid0/3/4/5/6
notable exception > raid1 as this is a non striped type of array ( it's a mirror ) > all my computers and servers boot raid1 's > well at least the ones that have disks as most of them are diskless ( including my workstations ) that PXE boot an OS > I keep all my OS images on my main storage...

each member of a raid1 array can be mounted individually. ( the boot sequence mounts them readonly until the OS is raid aware > needs initramfs.

you can even run your root filesystem on a raid5 if you make a separate small ( 100-200MB ) /boot raid1 boot partition.
in other words > you can perfectly fine run your OS on the same disks as your main storage...
( RAID1 arrays can consist of more then 2 disks )


lastly: I don't recommend running an array on a desktop system > if it's a normal user then it's quite alright, but if it's someone like me who likes fiddling around / compiling his own kernel etc... it's definitely not recommended > 
array's tend to start resyncing on unclean shutdowns (crashes etc )... and they're vulnerable at that time....


if anything bad happens with the array > don't panic ... your data is there.. when unsure ask for guidance..
practicing worst case scenarios on virtual machines ( with virtual arrays ) is how I learned things...
and before you try and rescue a broken array > dd copy all disks into disk images and try assembling those into a virtual machine / live CD

Jan :biggrin:

---

### Post by kwisher on 2009-07-12
Is the last line a normal response?

```
# mdadm /dev/md0 --fail /dev/sdb1 --remove /dev/sdb1
mdadm: set /dev/sdb1 faulty in /dev/md0
mdadm: hot remove failed for /dev/sdb1: Device or resource busy

```

I received the following email alert after issuing the remove command.

```
This is an automatically generated mail message from mdadm
running on doud-server

A Fail event had been detected on md device /dev/md0.

It could be related to component device /dev/sdb1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[3](F) sdd1[2] sdc1[1]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
      
unused devices: <none>
```

---

### Post by djamu on 2009-07-12
> **kwisher said:**
> Is the last line a normal response?

```
# mdadm /dev/md0 --fail /dev/sdb1 --remove /dev/sdb1
mdadm: set /dev/sdb1 faulty in /dev/md0
mdadm: hot remove failed for /dev/sdb1: Device or resource busy

```

I received the following email alert after issuing the remove command.

```
This is an automatically generated mail message from mdadm
running on doud-server

A Fail event had been detected on md device /dev/md0.

It could be related to component device /dev/sdb1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[3](F) sdd1[2] sdc1[1]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
      
unused devices: <none>
```

yup, it means mdadm does what it should do > mail you when a disk fails ;)
( mmm it shouldn't say "Device or resource busy" ), but don't worry to much about it > do a reboot after dd'ing and it should be alright

are you doing this as root or with sudo ? > you need too

---

### Post by kwisher on 2009-07-13
How long do you estimate the disk wiping to take on a 1TB drive? It has been running for close to 10 hours now.

---

### Post by Anthon berg on 2009-08-28
> **djamu said:**
> does a mail with subject 
[CODE]as a side note > it might be tempting to create a swap partition on a raid0/1/5/6
but don't do it! whenever by chance your mdadm module gets swapped out .... your computer will lockup


;)

Hey, where is the button to pin a medal on a post?

---

