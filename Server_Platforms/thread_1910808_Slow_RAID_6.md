---
title: "Slow RAID 6"
date: 2012-01-17
forum: Server Platforms
---

### Post by alfonso78 on 2012-01-17
Hi there,

I have 4x Seagate Barracuda Green SATA Revision 3.0 &#8211; 2 TB.

I was running my RAID without particular issues, but then while doing a check (echo check >> /sys/block/md0/md/sync_action) I realized the speed was low, around 20000K/sec

after a bit of research I found that I didn't correctly aligned the partitions:

```
# fdisk -l /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22cf0cdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect
``` 

so I deleted the ARRAY and used fdisk to start over and now my 4 disks all look like this:

```
# fdisk -l /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22cf0cdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   fd  Linux raid autodetect
```

see the start? now they are aligned.

then I removed all traces of the previous RAID (not easy. Look here: [http://www.tcpdump.com/kb/os/linux/removing-raid-devices.html](http://www.tcpdump.com/kb/os/linux/removing-raid-devices.html) )

and I created it again with chunks of 64K (the best for RAID 6 according to the benchmarks of this blog: [http://louwrentius.com/blog/category/raid/](http://louwrentius.com/blog/category/raid/) )

first problem, why do I have an error?

```
# sudo mdadm --verbose --create /dev/md0 --level 6 --chunk 64 --raid-devices 4 /dev/sd[b-e]1
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: size set to 1953512384K
mdadm: Defaulting to version 1.2 metadata
mdadm: ADD_NEW_DISK for /dev/sdb1 failed: Device or resource busy
```

second problem: why is it still so freaking slow????

```
# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sde1[3] sdd1[2] sdc1[1] sdb1[0]
      3907024768 blocks super 1.2 level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  resync =  0.0% (62776/1953512384) finish=1555.6min speed=20925K/sec

unused devices: <none>
```

thank you for your help.

Someone with the same MB, faster CPU and similar disks (4 x Green WD10EARS) can achieve almost 100000K/sec (see his blog: [http://www.tjansson.dk/?p=1398](http://www.tjansson.dk/?p=1398) )

any suggestion?

thanks,
alfonso

---

### Post by rubylaser on 2012-01-17
mdadm's default settings are set to not severely impact the system during a resync.  Have you performed any [tuning]("http://ubuntuforums.org/showthread.php?t=1494846") on your array?  This is by far the easiest / fastest way to make your array MUCH faster.

---

### Post by alfonso78 on 2012-01-18
> **rubylaser said:**
> mdadm's default settings are set to not severely impact the system during a resync.  Have you performed any [tuning]("http://ubuntuforums.org/showthread.php?t=1494846") on your array?  This is by far the easiest / fastest way to make your array MUCH faster.

ah! rubylaser! We meet again! :) thank you! you already answers my questions on RAID before. :)

can I run the script during the sync? or do I need to wait?

is it not-destructive?

thank you.

---

### Post by alfonso78 on 2012-01-18
Hi, trying to play with the script you linked, made me realize I have a basic question.

Once each of my drives look like this:

```
$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22cf0cdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   fd  Linux raid autodetect

```

meaning well aligned (for 4K issue) and ready for RAID (with the correct ID), what should I mention when I want to create the array? disks or partitions?

```
sudo mdadm --verbose --create /dev/md0 --level 6 --chunk 64 --raid-devices 4 /dev/sd[b-e]1
```

or

```
sudo mdadm --verbose --create /dev/md0 --level 6 --chunk 64 --raid-devices 4 /dev/sd[b-e]
```

both commands seem to work (although in the first case the RAID started syncing automatically while in the second case I saw this:

```
$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md127 : active (auto-read-only) raid6 sde[3] sdc[1] sdd[2] sdb[0]
      3907026816 blocks super 1.2 level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
        resync=PENDING

unused devices: <none>

```

and I manually started the sync with this:

```
$ sudo mdadm --readwrite /dev/md127
```

(also wondering why the heck md0 became md127, the system does that frequently)

I ask the question since the script seems to expect I use sdb (instead of sdb1) in creating the array since it runs the command 

```
echo $MINMAXHWSECKB > /sys/block/$DISK/queue/max_sectors_kb
```

which is only valid on disks, not on partitions.

you can see both examples around the internet...

I think I should use partitions (otherwise why bothering creating them?). Please help me understand!

---

### Post by rubylaser on 2012-01-18
> **alfonso78 said:**
> Hi, trying to play with the script you linked, made me realize I have a basic question.

Once each of my drives look like this:

```
$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22cf0cdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   fd  Linux raid autodetect

```

meaning well aligned (for 4K issue) and ready for RAID (with the correct ID), what should I mention when I want to create the array? disks or partitions?

```
sudo mdadm --verbose --create /dev/md0 --level 6 --chunk 64 --raid-devices 4 /dev/sd[b-e]1
```

or

```
sudo mdadm --verbose --create /dev/md0 --level 6 --chunk 64 --raid-devices 4 /dev/sd[b-e]
```

both commands seem to work (although in the first case the RAID started syncing automatically while in the second case I saw this:

```
$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md127 : active (auto-read-only) raid6 sde[3] sdc[1] sdd[2] sdb[0]
      3907026816 blocks super 1.2 level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
        resync=PENDING

unused devices: <none>

```

and I manually started the sync with this:

```
$ sudo mdadm --readwrite /dev/md127
```

(also wondering why the heck md0 became md127, the system does that frequently)

I ask the question since the script seems to expect I use sdb (instead of sdb1) in creating the array since it runs the command 

```
echo $MINMAXHWSECKB > /sys/block/$DISK/queue/max_sectors_kb
```

which is only valid on disks, not on partitions.

you can see both examples around the internet...

I think I should use partitions (otherwise why bothering creating them?). Please help me understand!

That's a lot of questions :)
1. Yes, you can run the script when the array is syncing and it is non-destructive (I use the original version of the script in the first post).
2. You should create the array with the partitions rather than the block devices, since you've aligned the partitions to 4K sectors.  So, use this version.
```
sudo mdadm --verbose --create /dev/md0 --level 6 --chunk 64 --raid-devices 4 /dev/sd[b-e]1

```
3. That script is making changes to the array, and the underlying block devices.  So, even using the partitions (as you should be doing), this will make the array MUCH faster.
4. What options are you passing when you are creating your filesystem?
5. Finally, md127 indicates that your mdadm.conf is not valid. You can recreate a working one like this.
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR  youruser@gmail.com" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

After a restart, your array should come up as /dev/md0.  Anytime you make changes to your array, you'll want to update your mdadm.conf file.  Hope that helps.

---

### Post by alfonso78 on 2012-01-18
> **rubylaser said:**
> That's a lot of questions :)


and you gave me a lot of answers! :) thanks!

> That script is making changes to the array, and the underlying block devices. So, even using the partitions (as you should be doing), this will make the array MUCH faster.

I didn't use the 1st version but the last version I found. In the last version I had the impression the script expects the RAID was made using block devices, not partitions.

> 
4. What options are you passing when you are creating your filesystem?

I still didn't create any filesystem. I will create a luks encryption layer (any suggestion on special parameters?) and then create a partition like this:

```
mkfs.ext4 -b 4096 -E stride=16,stripe-width=32
```

NOTE: to choose the parameters for mkfs I used [this online script]("http://busybox.net/~aldot/mkfs_stride.html").
I used as input:
RAID level: 6
Number of physical disks: 4
RAID chunk size (in KiB): 64 (again, based on [this blog]("http://louwrentius.com/blog/2010/05/linux-raid-level-and-chunk-size-the-benchmarks/"))
number of filesystem blocks (in KiB):4 (to match the physical sectors? not so sure about this parameter)

What do you think? Does the encryption layer mean the ext4 optimization are useless?

I also have a lot of options for mounting (that I picked up who knows where), I'll send them later for your review (if you have time).
I also thought about trying out btrfs, do you think it's ready for a stable system? What filesystem do you suggest for RAID 6 + LUKS?

> 
5. Finally, md127 indicates that your mdadm.conf is not valid. 

ok thanks. You're right, I rebooted without mdadm.conf just to test the speed of the system.

Does the script require reboot?

---

### Post by jchung on 2012-01-18
The later scripts do expect block devices. But if you have some experience writing scripts, that should be easy enough to change/update.

I don't recall if I wrote it to be tolerant of block devices/partitions.  I'd have to take a look at the script again.

The script does not require a reboot. The tuning should take effect immediately.

---

### Post by rubylaser on 2012-01-18
> **alfonso78 said:**
> and you gave me a lot of answers! :) thanks!



I didn't use the 1st version but the last version I found. In the last version I had the impression the script expects the RAID was made using block devices, not partitions.


I still didn't create any filesystem. I will create a luks encryption layer (any suggestion on special parameters?) and then create a partition like this:

```
mkfs.ext4 -b 4096 -E stride=16,stripe-width=32
```

What do you think? Does the encryption layer mean the ext4 optimization are useless?

I also have a lot of options for mounting (that I picked up who knows where), I'll send them later for your review (if you have time).
I also thought about trying out btrfs, do you think it's ready for a stable system? What filesystem do you suggest for RAID 6 + LUKS?



ok thanks. You're right, I rebooted without mdadm.conf just to test the speed of the system.

Does the script require reboot?

If this is for home use I would probably try to steer you away from LUKS unless you can really make a good case for why you need it.  It's one extra layer that in the event of a problem makes troubleshooting more difficult.

Your filesystem create line is perfect, and I would suggest you stick with ext4, as it's proven itself to be very stable.

Personally, I wouldn't trust btrfs with my data until it 1. has an fsck method and 2. it's a time proven filesystem check.  Here's what they say about it on the btrfs wiki.
> Note that Btrfs does not yet have a fsck tool that can fix errors. While Btrfs is stable on a stable machine, it is currently possible to corrupt a filesystem irrecoverably if your machine crashes or loses power on disks that don't handle flush requests correctly. This will be fixed when the fsck tool is ready.

---

### Post by alfonso78 on 2012-01-18
> **rubylaser said:**
> If this is for home use I would probably try to steer you away from LUKS unless you can really make a good case for why you need it.  It's one extra layer that in the event of a problem makes troubleshooting more difficult.

While I appreciate your concern, I'll go on with LUKS.

> 
Your filesystem create line is perfect, and I would suggest you stick with ext4, as it's proven itself to be very stable.

Personally, I wouldn't trust btrfs with my data until it 1. has an fsck method and 2. it's a time proven filesystem check.  Here's what they say about it on the btrfs wiki.

thanks. I'll keep ext4.

This, as promised, is my way to mount the filesystem. At the time I searched it, these options made sense. Any comment is appreciated.

```
sudo mount -t ext4 -o noauto_da_alloc,nodelalloc,noatime,nodiratime,barrier=1 /dev/mapper/big_raid /mnt/big_raid
```

---

### Post by rubylaser on 2012-01-18
Frankly, I would just go with the safe default options on ext4 and maybe add noatime if you'd like.  I've never had a problem saturating a gigabit ethernet connection (and well beyond 120 MB/s) with the default (safe) options.
```
/dev/md0 /storage ext4      defaults,noatime      0      2
```

Again, my 2 cents. To me, squeezing those last few MB/s out at the with an increased risk to the safety of my data just isn't worth the tradeoff.

---

### Post by alfonso78 on 2012-01-18
> **rubylaser said:**
> 
Again, my 2 cents. To me, squeezing those last few MB/s out at the with an increased risk to the safety of my data just isn't worth the tradeoff.

great! thanks I'll appreciate and follow your advice.

to be honest I don't even remember why I used these options. Might it be something to do with helping the disks "going to sleep"?
That will be an other hot topic that I will face if I ever manager to go pass the 20 MB/sec that I'm experiencing now.
I'm actually redoing the whole RAID right now. I hope you'll review my howto when it's ready! :)

---

### Post by rubylaser on 2012-01-18
> **alfonso78 said:**
> great! thanks I'll appreciate and follow your advice.

to be honest I don't even remember why I used these options. Might it be something to do with helping the disks "going to sleep"?
That will be an other hot topic that I will face if I ever manager to go pass the 20 MB/sec that I'm experiencing now.
I'm actually redoing the whole RAID right now. I hope you'll review my howto when it's ready! :)

None of those options will help your disks spin down any differently than the defaults.  But, you are in luck, I already have [directions]("http://zackreed.me/articles/60-spin-down-idle-hard-disks") created for spinning down idle disks.

Also, I have written up a few things on [mdadm on my website]("http://zackreed.me/articles?tag_id=22") if you'd like to take a look.

---

### Post by alfonso78 on 2012-01-18
> **rubylaser said:**
> mdadm's default settings are set to not severely impact the system during a resync.  Have you performed any [tuning]("http://ubuntuforums.org/showthread.php?t=1494846") on your array?  This is by far the easiest / fastest way to make your array MUCH faster.

Hi,

almost there.

can you please comment on two variables of the script?

```
BLOCKSIZE=4                     # of file system in kb
FORCECHUNKSIZE=true             # force max sectors kb to chunk size > 512
```

does blocksize have to do with sector? the famous 4k sectors?
if not, what is it and where do I find the right value?

about FORCECHUNKSIZE: what is it? should it be true of false? and why?

I see the script has a printout "setting max sectors kb to match chunk size" but I'd like to understand what I'm doing...

thanks!

---

### Post by alfonso78 on 2012-01-18
Ok so despite the two variables I wasn't sure about I run the script (actually I [rewrote it]("http://ubuntuforums.org/showpost.php?p=11622143&postcount=22") to understand what it does first)

and actually the commands I issued are:

```
blockdev --setra 1024 /dev/sdb /dev/sdc /dev/sdd /dev/sde
blockdev --setra 4096 /dev/md0
echo 128 > /sys/block/md0/md/stripe_cache_size
echo 64 > /sys/block/sde/queue/max_sectors_kb
echo 64 > /sys/block/sdd/queue/max_sectors_kb
echo 64 > /sys/block/sdc/queue/max_sectors_kb
echo 64 > /sys/block/sdb/queue/max_sectors_kb
echo 1 > /sys/block/sde/device/queue_depth
echo 1 > /sys/block/sdd/device/queue_depth
echo 1 > /sys/block/sdc/device/queue_depth
echo 1 > /sys/block/sdb/device/queue_depth
```


and my previous values were:

```
blockdev --getra /dev/sdb /dev/sdc /dev/sdd /dev/sde
256 256 256 256
blockdev --getra /dev/md0
512
cat /sys/block/md0/md/stripe_cache_size
256
cat /sys/block/sde/queue/max_sectors_kb
512
cat /sys/block/sdd/queue/max_sectors_kb
512
cat /sys/block/sdc/queue/max_sectors_kb
512
cat /sys/block/sdb/queue/max_sectors_kb
512
cat /sys/block/sde/device/queue_depth
1
cat /sys/block/sdd/device/queue_depth
1
cat /sys/block/sdc/device/queue_depth
1
cat /sys/block/sdb/device/queue_depth
1
```

but despite these changes the RAID is still very slow (and I didn't do anything about encryption yet, so that cannot be the reason!

```
# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sde1[3] sdd1[2] sdc1[1] sdb1[0]
      3907024768 blocks super 1.2 level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      [==>..................]  resync = 11.2% (218922556/1953512384) finish=1749.2min speed=16526K/sec

unused devices: <none>

```

any idea?

---

### Post by alfonso78 on 2012-01-18
Ok this is odd...

in fact maybe the sync is not a good way to check speed!

```
# hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   7352 MB in  2.00 seconds = 3677.83 MB/sec
 Timing buffered disk reads: 682 MB in  3.00 seconds = 227.31 MB/sec

```

so I went back to my previous values to confront...

```
# hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   7362 MB in  2.00 seconds = 3683.27 MB/sec
 Timing buffered disk reads: 608 MB in  3.00 seconds = 202.36 MB/sec

```

so the script does help a bit (I repeated the test many times and I get more or less 10% better performances), but then why my /proc/mdstat shows so poor performances?

please note I still didn't create any filesystem. Does it affect the system?

---

### Post by rubylaser on 2012-01-18
> **alfonso78 said:**
> Ok this is odd...

in fact maybe the sync is not a good way to check speed!

```
# hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   7352 MB in  2.00 seconds = 3677.83 MB/sec
 Timing buffered disk reads: 682 MB in  3.00 seconds = 227.31 MB/sec

```

so I went back to my previous values to confront...

```
# hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   7362 MB in  2.00 seconds = 3683.27 MB/sec
 Timing buffered disk reads: 608 MB in  3.00 seconds = 202.36 MB/sec

```

so the script does help a bit (I repeated the test many times and I get more or less 10% better performances), but then why my /proc/mdstat shows so poor performances?

please note I still didn't create any filesystem. Does it affect the system?

Those are decent speeds for a 4 disk RAID6 array, but hdparm is not exactly the best way to test either.  I'd really throw a filesystem on there and mount it at /storage.  Then try something like this...
Write Speed 10GB testfile
```
dd if=/dev/zero of=/storage/testfile.out bs=1M count=10000
```
Read Speed
```
dd if=/storage/testfile.out of=/dev/null bs=1M
```

That's a much better way to test.  I really wouldn't expect this to be blazing fast, you don't have very many spindles and the drives you're using are Green edition drives (not exactly speed merchants ;) )

---

### Post by alfonso78 on 2012-01-19
> **rubylaser said:**
> Those are decent speeds for a 4 disk RAID6 array, but hdparm is not exactly the best way to test either.  I'd really throw a filesystem on there and mount it at /storage.  Then try something like this...
Write Speed 10GB testfile
```
dd if=/dev/zero of=/storage/testfile.out bs=1M count=10000
```
Read Speed
```
dd if=/storage/testfile.out of=/dev/null bs=1M
```

thanks! I'll try when the filesystem is ready.

> 
That's a much better way to test.  I really wouldn't expect this to be blazing fast, you don't have very many spindles and the drives you're using are Green edition drives (not exactly speed merchants ;) )
sure. I know it won't be the fastest system. I just want it to be well configured.

if possible, can I ask you an explanation why the sync is so slow (or maybe it's not?) and the meaning of these two settings in the tune script:
```
BLOCKSIZE=4                     # of file system in kb
FORCECHUNKSIZE=true             # force max sectors kb to chunk size > 512
```

thanks!

---

### Post by rubylaser on 2012-01-19
> **alfonso78 said:**
> thanks! I'll try when the filesystem is ready.


sure. I know it won't be the fastest system. I just want it to be well configured.

if possible, can I ask you an explanation why the sync is so slow (or maybe it's not?) and the meaning of these two settings in the tune script:
```
BLOCKSIZE=4                     # of file system in kb
FORCECHUNKSIZE=true             # force max sectors kb to chunk size > 512
```

thanks!

Sure, your array and filesystem based off of the mkfs line you posted are going to be using 4KiB filesystem blocks, so these two options will ensure that your max sector size matches your chunk size on each device.  Again, this is non destructive, so you can try it without worrying about losing data.

Have you tried to run the first script as is, and compare with what you've seen.  You can set it up like this...

```
sudo -i
```
```
mkdir /root/scripts
cd /root/scripts
```
```
nano raidspeed.sh
```
and paste this (I've edited the script for your array)...
```
## parameters ##
MDDEV=md0               # e.g. md51 for /dev/md51
CHUNKSIZE=64           # in kb
BLOCKSIZE=4             # of file system in kb
NCQ=disable             # disable, enable. ath. else keeps current setting
NCQDEPTH=31             # 31 should work for almost anyone
FORCECHUNKSIZE=true     # force max sectors kb to chunk size > 512
DOTUNEFS=true           # run tune2fs, ONLY SET TO true IF YOU USE EXT[34]
RAIDLEVEL=raid6         # raid5, raid6


## code ##
# test for priviledges
if [ "$(whoami)" != 'root' ]
then
  exit 1
fi

# set number of parity devices
NUMPARITY=1
if [[ $RAIDLEVEL == "raid6" ]]
then
  NUMPARITY=2
fi

# get all devices
DEVSTR="`grep \"^$MDDEV : \" /proc/mdstat` eol"
while \
 [ -z "`expr match \"$DEVSTR\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\? \)'`" ]
do
  DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done

# get active devices list and spares list
DEVS=""
SPAREDEVS=""
while [ "$DEVSTR" != "eol" ]; do
  CURDEV="`echo $DEVSTR|cut -f -1 -d \ `"
  if [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\)'`" ]
  then
    SPAREDEVS="$SPAREDEVS${CURDEV:2:1}"
  elif [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\)'`" ]
  then
    DEVS="$DEVS${CURDEV:2:1}"
  fi
  DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done
NUMDEVS=${#DEVS}
NUMSPAREDEVS=${#SPAREDEVS}

# test if number of devices makes sense
if [ ${#DEVS} -lt $[1+$NUMPARITY] ]
then
  echo $(date): Need more devices >> /data51/smbshare1/#tuneraid.log
  exit 1
fi

# set read ahead
RASIZE=$[$NUMDEVS*($NUMDEVS-$NUMPARITY)*2*$CHUNKSIZE]   # in 512b blocks
echo read ahead size per device: $RASIZE blocks \($[$RASIZE/2]kb\)
MDRASIZE=$[$RASIZE*$NUMDEVS]
echo read ahead size of array: $MDRASIZE blocks \($[$MDRASIZE/2]kb\)
blockdev --setra $RASIZE /dev/sd[$DEVS]
blockdev --setra $RASIZE /dev/sd[$SPAREDEVS]
blockdev --setra $MDRASIZE /dev/$MDDEV

# set stripe cache size
STRCACHESIZE=$[$RASIZE/8]                               # in pages per device
echo stripe cache size of devices: $STRCACHESIZE pages \($[$STRCACHESIZE*4]kb\)
echo $STRCACHESIZE > /sys/block/$MDDEV/md/stripe_cache_size

# set max sectors kb
DEVINDEX=0
MINMAXHWSECKB=$(cat /sys/block/sd${DEVS:0:1}/queue/max_hw_sectors_kb)
until [ $DEVINDEX -ge $NUMDEVS ]
do
  DEVLETTER=${DEVS:$DEVINDEX:1}
  MAXHWSECKB=$(cat /sys/block/sd$DEVLETTER/queue/max_hw_sectors_kb)
  if [ $MAXHWSECKB -lt $MINMAXHWSECKB ]
  then
    MINMAXHWSECKB=$MAXHWSECKB
  fi
  DEVINDEX=$[$DEVINDEX+1]
done
if [ $CHUNKSIZE -le $MINMAXHWSECKB ] &&
  ( [ $CHUNKSIZE -le 512 ] || [[ $FORCECHUNKSIZE == "true" ]] )
then
  echo setting max sectors kb to match chunk size
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMDEVS ]
  do
    DEVLETTER=${DEVS:$DEVINDEX:1}
    echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    DEVINDEX=$[$DEVINDEX+1]
  done
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMSPAREDEVS ]
  do
    DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
    echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    DEVINDEX=$[$DEVINDEX+1]
  done
fi

# enable/disable NCQ
DEVINDEX=0
if [[ $NCQ == "enable" ]] || [[ $NCQ == "disable" ]]
then
  if [[ $NCQ == "disable" ]]
  then
    NCQDEPTH=1
  fi
  echo setting NCQ queue depth to $NCQDEPTH
  until [ $DEVINDEX -ge $NUMDEVS ]
  do
    DEVLETTER=${DEVS:$DEVINDEX:1}
    echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
    DEVINDEX=$[$DEVINDEX+1]
  done
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMSPAREDEVS ]
  do
    DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
    echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
    DEVINDEX=$[$DEVINDEX+1]
  done
fi

# tune2fs
if [[ $DOTUNEFS == "true" ]]
then
  STRIDE=$[$CHUNKSIZE/$BLOCKSIZE]
  STRWIDTH=$[$CHUNKSIZE/$BLOCKSIZE*($NUMDEVS-$NUMPARITY)]
  echo setting stride to $STRIDE blocks \($CHUNKSIZEkb\)
  echo setting stripe-width to $STRWIDTH blocks \($[$STRWIDTH*$BLOCKSIZE]kb\)
  tune2fs -E stride=$STRIDE,stripe-width=$STRWIDTH /dev/$MDDEV
fi

# exit
exit 0
```
Make it executable.
```
chmod +x raidspeed.sh
```
Finally, run it.
```
. raidspeed.sh
```

---

### Post by alfonso78 on 2012-01-19
> **rubylaser said:**
> Sure, your array and filesystem based off of the mkfs line you posted are going to be using 4KiB filesystem blocks, so these two options will ensure that your max sector size matches your chunk size on each device.  Again, this is non destructive, so you can try it without worrying about losing data.

Have you tried to run the first script as is, and compare with what you've seen.  You can set it up like this...



Hi, and thank you!

It creates the same changes as my version -- since it's the same script... ;-)
the difference is mine gathers all possible information from the system... I don't think it's a bad idea!

The only interesting thing I've noticed is that /sys/block/md0/md/stripe_cache_size has a life of its own:

```
# echo 128 > /sys/block/md0/md/stripe_cache_size
# cat /sys/block/md0/md/stripe_cache_size
140

```

So then I guess the slow speed of syncing is "natural", would you agree?

---

### Post by rubylaser on 2012-01-19
I wouldn't say based on the few hard drives you have, and the fact that they're Green Edition drives, coupled with RAID6, that those speeds are terribly slow.  I've never had my disks sync that slowly, but I've got 10 disks in a RAID6 and they're all WD Black or RE drives.

---

### Post by alfonso78 on 2012-01-20
> **alfonso78 said:**
> 
can you please comment on two variables of the script?

```
BLOCKSIZE=4                     # of file system in kb
FORCECHUNKSIZE=true             # force max sectors kb to chunk size > 512
```


that was a silly question, sorry.
Now I realize what BLOCKSIZE is:
this is a parameter of mkfs when you created your filesystem
e.g. mkfs.ext4 -b 4096 -E stride=16,stripe-width=32 /dev/md0
if you don't know your block size, run 
```
dumpe2fs -h /dev/md0 | grep "Block size"
```

so I guess I only need to understand FORCECHUNKSIZE now... ;-)

---

### Post by rubylaser on 2012-01-20
> **alfonso78 said:**
> that was a silly question, sorry.
Now I realize what BLOCKSIZE is:
this is a parameter of mkfs when you created your filesystem
e.g. mkfs.ext4 -b 4096 -E stride=16,stripe-width=32 /dev/md0
if you don't know your block size, run 
```
dumpe2fs -h /dev/md0 | grep "Block size"
```

so I guess I only need to understand FORCECHUNKSIZE now... ;-)

FORCECHUNKSIZE is editing the max_sectors_kb for each block (/dev/sd[bcde] rather than the partition).  This sets the queue length for each device and is in 512b units.  This can be helpful with sequential data like you'd have in a media server.

---

### Post by alfonso78 on 2012-01-20
> **rubylaser said:**
> FORCECHUNKSIZE is editing the max_sectors_kb for each block (/dev/sd[bcde] rather than the partition).  This sets the queue length for each device and is in 512b units.  This can be helpful with sequential data like you'd have in a media server.

thanks a lot! :)

---

### Post by rubylaser on 2012-01-20
No problem :)

---

### Post by alfonso78 on 2012-01-20
> **rubylaser said:**
> 
I'd really throw a filesystem on there and mount it at /storage.  Then try something like this...
Write Speed 10GB testfile
```
dd if=/dev/zero of=/storage/testfile.out bs=1M count=10000
```
Read Speed
```
dd if=/storage/testfile.out of=/dev/null bs=1M
```

That's a much better way to test.


Hi rubylaser! I created a small script based on your idea and reported results.
Please have a look and tell me if you see something wrong.
from my tests, the tuning script reduces performances!
[http://ubuntuforums.org/showthread.php?p=11627044](http://ubuntuforums.org/showthread.php?p=11627044)

---

### Post by rubylaser on 2012-01-20
> **alfonso78 said:**
> Hi rubylaser! I created a small script based on your idea and reported results.
Please have a look and tell me if you see something wrong.
from my tests, the tuning script reduces performances!
[http://ubuntuforums.org/showthread.php?p=11627044](http://ubuntuforums.org/showthread.php?p=11627044)

How much RAM did you say you had (I think I remember 8GB)?  If, so you might want to run the test with a larger dd size than 10GB to avoid caching in RAM instead of hitting the hard disks.  I used a script like this to test my Solaris ZFS fileserver.  It's uses some varying blocksizes(10MB really isn't typical) and writes out 16GB testfiles.

```
#!/bin/bash
NOW=$(date +"%b-%d-%H-%M-%S")
LOGFILE="/root/ddtest_output-$NOW.txt"
# Replace with your array mount point
MOUNT_POINT=storage
echo $LOGFILE > $LOGFILE
echo "-------------------------------------------------------------------" >> $LOGFILE
uname -a >> $LOGFILE
pwd >> $LOGFILE
echo "-------------------------------------------------------------------" >> $LOGFILE
echo "Write test"
echo "Write test" >> $LOGFILE
echo "dd if=/dev/zero of=/$MOUNT_POINT/ddfile bs=8k count=2000000" >> $LOGFILE
/usr/bin/time sh -c "dd if=/dev/zero of=/$MOUNT_POINT/ddfile bs=8k count=2000000" 1>> $LOGFILE 2>&1
echo "-------------------------------------------------------------------" >> $LOGFILE
echo "Flush buffer"
echo "Flush buffer" >> $LOGFILE
echo "dd if=/dev/zero of=/$MOUNT_POINT/ddfile2 bs=8k count=1000000" >> $LOGFILE
/usr/bin/time sh -c "dd if=/dev/zero of=/$MOUNT_POINT/ddfile2 bs=8k count=1000000" 1>> $LOGFILE 2>&1
echo "-------------------------------------------------------------------" >> $LOGFILE
echo "Read test"
echo "Read test" >> $LOGFILE
echo "dd if=/$MOUNT_POINT/ddfile of=/dev/null bs=8k" >> $LOGFILE
/usr/bin/time sh -c "dd if=/$MOUNT_POINT/ddfile of=/dev/null bs=8k" >> $LOGFILE 2>&1
echo "-------------------------------------------------------------------" >> $LOGFILE
echo "Cleanup"
rm /$MOUNT_POINT/ddfile
rm /$MOUNT_POINT/ddfile2
echo $LOGFILE
cat $LOGFILE
```

---

### Post by alfonso78 on 2012-01-20
> **rubylaser said:**
> How much RAM did you say you had (I think I remember 8GB)?  If, so you might want to run the test with a larger dd size than 10GB to avoid caching in RAM instead of hitting the hard disks.  

Hi!

I have 4 GB of RAM.
I write 3 files of 10 GB and then read them.
Do you think the cache might change results?

---

### Post by rubylaser on 2012-01-20
> **alfonso78 said:**
> Hi!

I have 4 GB of RAM.
I write 3 files of 10 GB and then read them.
Do you think the cache might change results?

At 4GB of RAM, no it's not likely, but it would be interesting to test with a larger dd file.

---

### Post by alfonso78 on 2012-01-21
> **rubylaser said:**
> At 4GB of RAM, no it's not likely, but it would be interesting to test with a larger dd file.

sure, I can try this week.

what about your system? Can you try my script after reboot (so without the tuning) and after the tuning script (my version or the original, it's the same)?
(but with mine you can quickly see if the script does anything or nothing at all...)

I'd like to see if other systems respond differently!

thanks!

---

### Post by rubylaser on 2012-01-21
Here the the results on the slower of my two arrays at home (5) 2TB Hitachi 5K3000 drives in RAID5 on an AMD 4600+ X2.  My other array is running it's backup jobs right now, so it wouldn't be a valid test to run at this point.  This array is a (10) disk 1TB array of 7200 RPM drives untuned it's around 240 MB/s.

```
writing tests:
10000000000 bytes (10 GB) copied, 49.1305 s, 204 MB/s
10000000000 bytes (10 GB) copied, 50.6779 s, 197 MB/s
10000000000 bytes (10 GB) copied, 51.0533 s, 196 MB/s
reading tests:
10000000000 bytes (10 GB) copied, 37.8263 s, 264 MB/s
10000000000 bytes (10 GB) copied, 39.4478 s, 253 MB/s
10000000000 bytes (10 GB) copied, 38.8445 s, 257 MB/s
```

I can't restart the server because my daughter is watching Finding Nemo on the array right now.  Untuned, this array was around 115 MB/s.

---

### Post by alfonso78 on 2012-01-21
> **rubylaser said:**
> Here the the results on the slower of my two arrays at home (5) 2TB Hitachi 5K3000 drives in RAID5 on an AMD 4600+ X2.  My other array is running it's backup jobs right now, so it wouldn't be a valid test to run at this point.  This array is a (10) disk 1TB array of 7200 RPM drives untuned it's around 240 MB/s.

```
writing tests:
10000000000 bytes (10 GB) copied, 49.1305 s, 204 MB/s
10000000000 bytes (10 GB) copied, 50.6779 s, 197 MB/s
10000000000 bytes (10 GB) copied, 51.0533 s, 196 MB/s
reading tests:
10000000000 bytes (10 GB) copied, 37.8263 s, 264 MB/s
10000000000 bytes (10 GB) copied, 39.4478 s, 253 MB/s
10000000000 bytes (10 GB) copied, 38.8445 s, 257 MB/s
```

I can't restart the server because my daughter is watching Finding Nemo on the array right now.  Untuned, this array was around 115 MB/s.

thank you.

Why do you think the tuning make your system run faster and mine slower? next time you boot (if you don't mind) can you run my script without execute flag to see the difference before your default setting and what the tuning script suggests?

I'd love to understand more about it, but I have very little doubt the script doesn't work well for me.

thanks!

---

