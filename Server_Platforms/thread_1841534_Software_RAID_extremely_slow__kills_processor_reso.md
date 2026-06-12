---
title: "Software RAID extremely slow / kills processor resource"
date: 2011-09-09
forum: Server Platforms
---

### Post by jtupulis on 2011-09-09
Hi,

I'm not a total newbie, but not very experienced also :) Have enjoyed Ubuntu Desktop since 9th version. Now struggling for couple of month with software RAID performance issue.

Here it is. I have built desktop HW intended for home file server. Asus P7F7-E WS supercomputer motherboard, INTEL CORE I3-560 3.33G processor, 4GB RAM, INTEL 510 SSD MLC 120GB for system disk and 4 HDDs for data: WD Caviar Green, 2TB, SATA/300, 64MB cache.

Installed Ubuntu server 11.04, nice and smoothly. First thing was to set up it as file server. Created software RAID (using Webmin, but checked mdadm config manually as there were some problems initially). First version was RAID1+0 (I mean two RAID1 arrays and then RAID0 on top of those), then strightforward RAID10. IO speeds of the array like ~2Mbps, load averages above 4 while copying data... Then tried 2 RAID1 arrays + LVM to make one volume because idea was that striping eats processor resource. The same outcome... Simple partition on one of the disks - speeds ~ 600Mbps.

Now I'm almost sure that i3 processor just can't afford syncing of 8TB of raw space in any SW RAID config normally. Seeking for confirmation of my thinking or any other ideas/proposals/critics/anything for me to move forward.

BR,
Janis

---

### Post by Vegan on 2011-09-09
might be easier to juts use a bunch of disks and mount them under a folder somewhere

This way less likely to loss everything if it breaks

---

### Post by jtupulis on 2011-09-10
> **Vegan said:**
> might be easier to juts use a bunch of disks and mount them under a folder somewhere

This way less likely to loss everything if it breaks

Yes, I was thinking about that, but this way I'm not getting safety RAID1 provides. On the JBOD if disc fails, data is lost.

---

### Post by zackwasa on 2011-09-10
why are you using a software raid? shouldn't your motherboard have some generic hardware RAID adapter?

---

### Post by rubylaser on 2011-09-10
An i3 is massive overkill just for mdadm.  I've just recently upgraded, but I ran my fileserver on an AMD 3000+ (1.8 Ghz single core processor) for years and could saturate a gigabit connection with it.  There's no need for LVM in your scenario, so I'd eliminate that portion.  It's just overhead, extra complexity with no benefit.

One other caveat.  Do you ever plan on expanding your array to have more disks?  If so mdadm does not support growing a RAID10.  You could go with RAID5/6 if this was a need.  I currently use RAID6 on my 10 disk array.

Here's a bunch of quesitons:
1. Are your WD drives advanced format drives, that need their partitions properly aligned?  (model #)
2. Can you post your 
```
/etc/mdadm/mdadm.conf
```
3. and...
```
mdadm --detail scan
```
4. Describe of how you're building your array (command line vs. ubuntu disk gui)
5. What type of filesystem are you using and how are you creating it?
6. Is this slow speed across the network or on the machine?  Can you post the result of something like this
Write Speed
```
dd if=/dev/zero of=/path/to/array/testfile.out bs=1M count=10000
```
Read Speed
```
dd if=/path/to/array/testfile.out of=/dev/null bs=1M
```

That''s a good place to start.

---

### Post by rubylaser on 2011-09-10
> **zackwasa said:**
> why are you using a software raid? shouldn't your motherboard have some generic hardware RAID adapter?

Fakeraid (motherboard software RAID) has all of the negatives of hardware raid with performance that typically doesn't rival a hardware RAID card. Also, you need the same motherboard to reassemble the RAID in the case of a motherboard failure. Finally, in the case of motherboard fakeraid, it isn't even as portable as a RAID card (drop it into a new system / better hardware).

Software RAID (mdadm) works great, there's just something that's not working properly in the OP's case.

---

### Post by Vegan on 2011-09-10
That is why I like to use a RAID card. Ideally spare RAID cards should be on hand in the data center in case on dies.

I posted my server load on [my gaming site]("http://www.hardcore-games.tk/"). I am now using a Sempron 3400+ to run the web pages, much better than the Celeron 335 I was using before.

I have not been able to produce graphs of server load with my Linux server VM to my satisfaction.

My PCI VIA card lacks a CPU so its not any better than a fake RAID

A good RAID card has a CPU and memory to offload the server processor workload. Such cards cost $$$$$$$

---

### Post by jtupulis on 2011-09-10
> **zackwasa said:**
> why are you using a software raid? shouldn't your motherboard have some generic hardware RAID adapter?

It's simple - it's fakeRAID, anyway processor does the job. Btw, being desperate, I tried my MB's RAID controller - speeds are the same as in case of software RAID.

---

### Post by jtupulis on 2011-09-10
> **Vegan said:**
> That is why I like to use a RAID card. Ideally spare RAID cards should be on hand in the data center in case on dies.

I posted my server load on [my gaming site]("http://www.hardcore-games.tk/"). I am now using a Sempron 3400+ to run the web pages, much better than the Celeron 335 I was using before.

I have not been able to produce graphs of server load with my Linux server VM to my satisfaction.

My PCI VIA card lacks a CPU so its not any better than a fake RAID

A good RAID card has a CPU and memory to offload the server processor workload. Such cards cost $$$$$$$

I'm not at the datacenter, you know, It's a home fileserver ;)

Yeah, you are right, I was starting to think about real HW RAID card, but before that I'm willing to understand is it really so that 8TB raw space kills i3 processor + 4GB RAM.

---

### Post by jtupulis on 2011-09-10
> **rubylaser said:**
> An i3 is massive overkill just for mdadm.  I've just recently upgraded, but I ran my fileserver on an AMD 3000+ (1.8 Ghz single core processor) for years and could saturate a gigabit connection with it.  There's no need for LVM in your scenario, so I'd eliminate that portion.  It's just overhead, extra complexity with no benefit.

Yeah, I've run my RAID5 of 3TB raw on the Pentium D for more than year, no problem. Therefore I'm wondering here.

One other caveat.  Do you ever plan on expanding your array to have more disks?  If so mdadm does not support growing a RAID10.  You could go with RAID5/6 if this was a need.  I currently use RAID6 on my 10 disk array.

No, there is no idea to extend, because current case will not hold more disks and current data amout is ~50% of the planned array. And, even if so, it would be fun to do it :)

Here's a bunch of quesitons:
1. Are your WD drives advanced format drives, that need their partitions properly aligned?  (model #)

I'm not sure I understand the question, except that advanced format mean sector bigger than 512B. But have no clue how to perform it. Model is ATA WDC WD20EARS-00M. Btw, while configuring LVM I noticed a message about differences in physical and logical sector sizes but had no clue what to do with it.

2. Can you post your 
```
/etc/mdadm/mdadm.conf
```

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
ARRAY /dev/md/0 metadata=1.2 UUID=f0d5cae4:0f013eb8:5fc10523:9effb5f6 name=KURMIS:0

# This file was auto-generated on Sat, 10 Sep 2011 20:15:50 +0300
# by mkconf $Id$
DEVICE /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
ARRAY /dev/md0 level=raid10 devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1





```

3. and...
```
mdadm --detail scan
```

mdadm --detail scan didn't work, issued instead: sudo mdadm --detail /dev/md0

```

jtupulis@KURMIS:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat Sep 10 20:17:30 2011
     Raid Level : raid10
     Array Size : 3907020800 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Sat Sep 10 20:17:33 2011
          State : active, resyncing
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2
     Chunk Size : 1024K

 Rebuild Status : 1% complete

           Name : KURMIS:0  (local to host KURMIS)
           UUID : 9e688152:765f3ceb:6a6b7c44:8022da77
         Events : 1

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1


```

4. Describe of how you're building your array (command line vs. ubuntu disk gui)

Webmin, this utility makes use of mdadm by some scripts.

5. What type of filesystem are you using and how are you creating it?

sudo mkfs.ext4 /dev/md0

6. Is this slow speed across the network or on the machine?  Can you post the result of something like this
Write Speed
```

jtupulis@KURMIS:~$ sudo dd if=/dev/zero of=/media/V_data_3000/testfile.out bs=1M count=10000
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 162.047 s, 64.7 MB/s


```
Read Speed
```

jtupulis@KURMIS:~$ sudo dd if=/media/V_data_3000/testfile.out of=/dev/null bs=1M 
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 60.8723 s, 172 MB/s


```

That''s a good place to start.

Btw, reinstalled mdadm and recreated array from scratch, at the moment it shows ~480Mbps while copying data from single disc to RAID array. Much better. Strange, will se if it will persist. And what about reaching max controller allows (3Gbps)?

---

### Post by jtupulis on 2011-09-10
No, dropped to ~50 Mbps already...

---

### Post by rubylaser on 2011-09-10
Your /etc/mdadm/mdadm.conf file is a little messy.  I'd regenerate a clean one like this...

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Also, there's a great [script]("http://ubuntuforums.org/showthread.php?t=1494846") for tuning mdadm arrays here on the forums.  This basically tunes the read_ahead values, and stripe_cache_size as well as tuning of NCQ on your drives.  This is harmless to your data, and should make your array much faster.

```
sudo -i
```
```
nano /root/raid_speedup.sh
```
and paste this in...
```
#!/bin/bash
###############################################################################
#  simple script to set some parameters to increase performance on a mdadm
# raid5 or raid6. Ajust the ## parameters ##-section to your system!
#
#  WARNING: depending on stripesize and the number of devices the array might
# use QUITE a lot of memory after optimization!
#
#  27may2010 by Alexander Peganz
###############################################################################


## parameters ##
MDDEV=md0              # e.g. md51 for /dev/md51
CHUNKSIZE=1024          # in kb
BLOCKSIZE=4             # of file system in kb
NCQ=disable             # disable, enable. ath. else keeps current setting
NCQDEPTH=31             # 31 should work for almost anyone
FORCECHUNKSIZE=true     # force max sectors kb to chunk size > 512
DOTUNEFS=true          # run tune2fs, ONLY SET TO true IF YOU USE EXT[34]
RAIDLEVEL=raid5         # raid5, raid6


## code ##
# test for privileges
if [ "$(whoami)" != 'root' ]
then
  echo $(date): Need to be root >> /root/tuneraid.log
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
  echo $(date): Need more devices >> /root/tuneraid.log
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

echo $(date): Success >> /root/tuneraid.log
```

I've already changed the values for you, so this should work great.  Then run it like this...
```
. /root/raid_speedup.sh
```

After doing that, try to re-run the dd commands I gave you earlier.

If you're feeling more adventurous, and want to really make this perform better, those drives are advanced format drives, so you're receiving up to a 30% speed penalty for not aligning the partitions. This [IBM article]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-twtr4KB-Disksdth-LX") shows the effects of improperly aligned partitions, and shows how fdisk them to get the partitions aligned properly. Hint: like this ```
fdisk -H 224 -S 56 /dev/sda
```

If you don't have any important data on the array yet. I'd repartition the disks, zero the superblocks on your drives, and rebuild the array.  If you do that you should make your filesystem for the right stride/stripe width after you've recreated the array like this...
```
mkfs.ext4 -b 4096 -E stride=256,stripe-width=512
```

---

### Post by jtupulis on 2011-09-11
Thanks, rubylaser for great advice.

Decided to go for rebuilding. Stopped array, zeroed superblocks, deleted partitions, created new ones using

```
fdisk -H 224 -S 56 /dev/sd*
```

Decided to create raid using console instead of Webmin. Something fails on me:

```


root@KURMIS:/home/jtupulis# mdadm -v --create /dev/md0 --level=raid10 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: layout defaults to n2
mdadm: chunk size defaults to 512K
mdadm: layout defaults to n2
mdadm: layout defaults to n2
mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=1953513560K  mtime=Fri Sep  9 20:40:36 2011
mdadm: layout defaults to n2
mdadm: layout defaults to n2
mdadm: layout defaults to n2
mdadm: size set to 1953511936K
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: ADD_NEW_DISK for /dev/sdc1 failed: Device or resource busy



```

How can it be with partitions created just a minute ago and noting else done on discs?

Also, during the process noticed that fdisk warns me that physical sector size is bigger thatn logical sector size. I think this is about advanced format. But then - noticed that warnings come not for all discs... Strange, identical HDDs, I even screwed those out in order to check if manufacturer model labels are identical - they are! Here is disc info:

```

root@KURMIS:/home/jtupulis# fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
218 heads, 56 sectors/track, 320038 cylinders
Units = cylinders of 12208 * 512 = 6250496 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x03a6db51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      320039  1953513560   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
218 heads, 56 sectors/track, 320038 cylinders
Units = cylinders of 12208 * 512 = 6250496 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      320039  1953513560   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
218 heads, 56 sectors/track, 320038 cylinders
Units = cylinders of 12208 * 512 = 6250496 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      320039  1953513560   fd  Linux raid autodetect

...

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
218 heads, 56 sectors/track, 320038 cylinders
Units = cylinders of 12208 * 512 = 6250496 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      320039  1953513560   fd  Linux raid autodetect

Disk /dev/md0: 4000.8 GB, 4000792444928 bytes
2 heads, 4 sectors/track, 976755968 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

...


```

And, hoping that I'll proceed with creating my array, question about the script you propose to run on array. RAID5 is one of the parameters in the script. Do you think it will work on my RAID10 as well? 

Thanks,
Janis

---

### Post by jtupulis on 2011-09-11
Restarted and succeded with array creation. Created filesystem with options suggested previously.

Now test speed, dd shows better situation than previously:

```

root@KURMIS:/home/jtupulis# dd if=/dev/zero of=/media/V_data_3000/testfile.out bs=1M count=10000
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 48.025 s, 218 MB/s
root@KURMIS:/home/jtupulis# dd if=/media/V_data_3000/testfile.out of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 46.8913 s, 224 MB/s


```

---

### Post by rubylaser on 2011-09-11
Now that's more like it :)  Let it run for a while and try it again to make sure that your performance doesn't degrade, but you should be all set.  I'll modify that script for you in a few minutes for use in raid10.

---

### Post by rubylaser on 2011-09-11
This should do it...

```
#!/bin/bash
###############################################################################
#  simple script to set some parameters to increase performance on a mdadm
# raid5 or raid6. Adjust the ## parameters ##-section to your system!
#
#  WARNING: depending on stripe-size and the number of devices the array might
# use QUITE a lot of memory after optimization!
#
#  27may2010 by Alexander Peganz
###############################################################################


## parameters ##
MDDEV=md0               # e.g. md0 for /dev/md0
CHUNKSIZE=1024          # in kb
BLOCKSIZE=4             # of file system in kb
NCQ=disable             # disable, enable. ath. else keeps current setting
NCQDEPTH=31             # 31 should work for almost anyone
FORCECHUNKSIZE=true     # force max sectors kb to chunk size > 512
DOTUNEFS=true           # run tune2fs, ONLY SET TO true IF YOU USE EXT[34]
RAIDLEVEL=raid10         # raid5, raid6, raid10


## code ##
# test for privileges
if [ "$(whoami)" != 'root' ]
then
  echo $(date): Need to be root >> /root/tuneraid.log
  exit 1
fi

# set number of parity devices
if [[ $RAIDLEVEL == "raid6" ]]
then
  NUMPARITY=2
elif [[ $RAIDLEVEL == "raid10" ]]
then
  NUMPARITY=0
else
  NUMPARITY=1
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
  echo $(date): Need more devices >> /root/tuneraid.log
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

echo $(date): Success >> /root/tuneraid.log
```

---

### Post by jtupulis on 2011-09-12
Yeah, looked very nice, copied ~0.5TB of data @ ~550 Mbps :) Thanks for your advice!

But then had to stop copying in the middle and strange thing happened. Tried copy update (cp -rau) in order to continue and it was very slow again. Then dropped data already copied in order to do simple cp from the beginning and speeds were again @ ~1Mbps.

Will remake an array from scratch again, but it would be good to have an idea why could that happened.

---

### Post by jtupulis on 2011-09-12
Yeah, recreated an array and speed is rocking again.

After copying some data to the array I'll run the script.

---

### Post by rubylaser on 2011-09-12
It's hard to say what happened without seeing a logfile, but I'm glad to hear it's working properly again.  Please let me know how it turns out.

---

### Post by jtupulis on 2011-09-13
:( left cp yesterday night and today morning discovered that it has copied just 22G overnight...

I think I did recreation of array exactly as previous time, I even used most of the commands from shell history.

Any suggestions about deeper troubleshooting of the problem? Or maybe I should have run the optimization script first?

---

### Post by rubylaser on 2011-09-13
It sounds like you might have a hardware problem.  What's the output of this...
```
dmesg | grep md0
```

And, you could try to make bigger local files via dd to rule out a network card or other issue.  This will make a 80GB file then read it back. Let me know what those result in
```
dd if=/dev/zero of=/media/V_data_3000/testfile.out bs=1M count=80000
```
```
dd if=/media/V_data_3000/testfile.out of=/dev/null bs=1M count=80000
```

I would say if your array can create and read that file back properly, you're probably looking at a networking issue, and not a mdadm issue. Let me know what you find.

---

### Post by jchung on 2011-09-13
You may want to look at your network settings and also perhaps the kernel VM settings.

Put this in /etc/sysctl.conf 
```

# increase TCP max buffer size
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
# increase Linux autotuning TCP buffer limits
# min, default, and max number of bytes to use
net.ipv4.tcp_rmem = 4096 524288 16777216
net.ipv4.tcp_wmem = 4096 524288 16777216

net.ipv4.tcp_base_mss = 1440

net.ipv4.tcp_no_metrics_save = 1
net.core.netdev_max_backlog = 2500

vm.swappiness = 1
vm.vfs_cache_pressure = 50
vm.dirty_background_ratio = 1
vm.dirty_ratio = 5

```

And then run 'sysctl -p'

You should have enough memory to support these settings. If its network settings, this should help. If its the virtual memory manager doing huge page flushes thats killing performance, this should help as well.

While you are doing the cp and when it gets slow, it would probably be good to get the output of the 'free' command.

Possibly run 'vmstat 5' to see if lots of memory is being used, if there are a lot of context switches, pages being read in and being written out, etc...

Is there anything else running on this server?

Joo

---

### Post by jtupulis on 2011-09-13
Thanks for your your suggestions. One pre-question - why should network settings impact on copying data from disk to the array withinnthe same SATA controller? Or haven't I mentioned that this is not network copy?

---

### Post by rubylaser on 2011-09-13
> **jtupulis said:**
> Thanks for your your suggestions. One pre-question - why should network settings impact on copying data from disk to the array withinnthe same SATA controller? Or haven't I mentioned that this is not network copy?

You might have mentioned that it's all disk to disk, but I must have missed that :)  Please try the dd commands that I gave above, and let's see how those go.

---

### Post by jchung on 2011-09-13
> **rubylaser said:**
> You might have mentioned that it's all disk to disk, but I must have missed that :)  Please try the dd commands that I gave above, and let's see how those go.


If its all local... (and please excuse me if this has already been answered)...

1. check memory utilization. Is it swapping? Is it caching a whole bunch of pages and then having to write out a whole bunch later...

2. What other processes are running

3. What filesystem are you using? What settings did you use when creating the filesystems?

---

### Post by rubylaser on 2011-09-13
The thread is only 3 pages long.  It would make sense to look through it so you have the whole picture to aid in troubleshooting.  The OP is using mdadm with partitions aligned to the 4k sectors on his drives, with and ext4 filesystem with the stride and stripe_width tailored for the number of disks and chunk size of the array (page 2).

---

### Post by jchung on 2011-09-13
Thats a fair point Ruby. I should have looked back through the other posts.

Regarding the stride and stripe width... It looks like his chunk size is 512KB. Shouldn't stride be 128 (512KB / 4KB blocks) and stripe width be 256? (stride * 2)

Looking back through the posts, I don't see any mention of mount options used when mounting the filesystem. 

I'd probably still look at running processes, memory utilization, etc...

---

### Post by rubylaser on 2011-09-13
Yes, I was posting at the time between 3 separate mdadm threads, I forgot that he's got a raid10.  The command should have been...

```
mkfs.ext4 -b 4096 -E stride=128,stripe-width=256
```

---

### Post by jtupulis on 2011-09-13
> **rubylaser said:**
> It sounds like you might have a hardware problem.  What's the output of this...
```
dmesg | grep md0
```

And, you could try to make bigger local files via dd to rule out a network card or other issue.  This will make a 80GB file then read it back. Let me know what those result in
```
dd if=/dev/zero of=/media/V_data_3000/testfile.out bs=1M count=80000
```
```
dd if=/media/V_data_3000/testfile.out of=/dev/null bs=1M count=80000
```

I would say if your array can create and read that file back properly, you're probably looking at a networking issue, and not a mdadm issue. Let me know what you find.




Untill now just first dd has finished:

```

root@KURMIS:/home/jtupulis# dmesg | grep md0
[    3.551873] md/raid10:md0: not clean -- starting background reconstruction
[    3.551875] md/raid10:md0: active with 4 out of 4 devices
[    3.551896] md0: detected capacity change from 0 to 4000792444928
[    3.551931] md: resync of RAID array md0
[    3.551945] md: resuming resync of md0 from checkpoint.
[    4.706158]  md0: unknown partition table
[    7.011947] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
root@KURMIS:/home/jtupulis# dd if=/dev/zero of=/media/V_data_3000/testfile.out bs=1M count=80000
80000+0 records in
80000+0 records out
83886080000 bytes (84 GB) copied, 10191.4 s, 8.2 MB/s
root@KURMIS:/home/jtupulis# dd if=/media/V_data_3000/testfile.out of=/dev/null bs=1M count=80000


```

Will post the rest in the evening.

Yes, and regatding what else ir up on the machine. I was experimenting previously with several things and those are up (dns server, apache, mysql, samba), but not in active use. Btw, those were up during good RAID speeds also. As I has experimented with a machine during couple of month, maybe I should consider clean install...

---

### Post by jtupulis on 2011-09-13
Btw, any idea why physical sector size differ on identical disks? Disks were not attached at the same time, maybe recognition failed somehow?

---

### Post by jtupulis on 2011-09-14
Regarding mount options, it would be great if you could comment. I can't remember exactly, but it is possible that good speeds were in place when I mounted manually and bad speeds are when /etc/fstab record works, I made it some time ago for different setup and haven't rechecked recently. Here it is:

```

/dev/md0		/media/V_data_3000	ext4	rw,group,owner,users,exec,auto,sync,user	0	0


```

Second dd just finished:

```

root@KURMIS:/home/jtupulis# dd if=/media/V_data_3000/testfile.out of=/dev/null bs=1M count=80000
80000+0 records in
80000+0 records out
83886080000 bytes (84 GB) copied, 1158.61 s, 72.4 MB/s


```

---

### Post by jchung on 2011-09-14
> **jtupulis said:**
> Regarding mount options, it would be great if you could comment. I can't remember exactly, but it is possible that good speeds were in place when I mounted manually and bad speeds are when /etc/fstab record works, I made it some time ago for different setup and haven't rechecked recently. Here it is:

```

/dev/md0		/media/V_data_3000	ext4	rw,group,owner,users,exec,auto,sync,user	0	0


```

Second dd just finished:

```

root@KURMIS:/home/jtupulis# dd if=/media/V_data_3000/testfile.out of=/dev/null bs=1M count=80000
80000+0 records in
80000+0 records out
83886080000 bytes (84 GB) copied, 1158.61 s, 72.4 MB/s


```

Here are the options I use...

```
/dev/md0p1    /data   ext4	async,nodiratime,noatime,stripe=384,data=writeback,nobarrier,journal_async_commit,nobh	0 2

```

async - I don't see a difference in performance. turning async on. 
nodiratime - one less write that has to be done to update meta data for the directory
noatime - one less write that has to be done to update meta data for a file
stripe=384 - this should match the stripe width when you created the filesystem
data=writeback - this is a slightly more dangerous setting. highest throughput setting for this option
nobarrier - another "dangerous" setting. again supposed to help performance
journal_async_commit - from the man page "Commit block can be  written  to  disk  without  waiting  for  descriptor blocks."
nobh - some debate as to whether it helps with an ext4 filesystem

Not sure if setting these will help with your problem. But something you can try.

while you are doing the 'dd', in another window would you run the following?

```

# sar -P ALL 5

```

In yet another window:

```

iostat -dm 5

```

In a 3rd window:
```

vmstat 5

```

in a 4th window:
```

top
```

So.. the sar will show the CPU utilization. 
iostat will show disk IO per drive. So we can see if there is one particular drive which is underperforming or if the load is identical across each drive
vmstat will show memory utilization, context switches, swapping
top will show which processes are using the most CPU. Also gives summary of overall load, memory utilization, and swap utilization.

Some other things you might want to try:

1. Run the following and compare against every disk in the array:
```
hdparm -I /dev/sdX
```

2. If you don't have smartctl installed, then install smartctl (package is smartmontools) and run the following on each drive:
```

# smartctl -l errors /dev/sdX
# smartctl -l selftest /dev/sdX
# smartctl --test=long /dev/sdX
*** wait for self test to finish ***
# smartctl -l selftest /dev/sdX

```


Joo

---

### Post by jtupulis on 2011-09-14
```

root@KURMIS:/home/jtupulis# top

top - 19:52:42 up 1 day, 20:19,  6 users,  load average: 6.33, 5.90, 5.55
Tasks: 186 total,   2 running, 183 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.3%us,  1.7%sy,  0.0%ni, 63.3%id, 33.3%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   3876612k total,  3833008k used,    43604k free,   334408k buffers
Swap:  4011004k total,      148k used,  4010856k free,  2748364k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4604 root      20   0 10944 1692  616 D    2  0.0   0:04.93 dd                 
29517 root      20   0     0    0    0 D    1  0.0   0:10.58 kworker/u:0        
  290 root      20   0     0    0    0 S    1  0.0  22:11.18 md0_raid10         
 5549 root      20   0 36884 1968 1132 S    1  0.1   0:00.03 vsftpd             
 3243 root      20   0 18356  852  688 D    1  0.0  12:23.55 cp                 
 5546 nobody    20   0     0    0    0 D    1  0.0   0:00.02 vsftpd             
    1 root      20   0 24116 2108 1216 S    0  0.1   9:43.74 init               
   12 root      20   0     0    0    0 S    0  0.0   1:58.84 kworker/2:0        
   16 root      20   0     0    0    0 S    0  0.0   0:02.35 ksoftirqd/3        
   32 root      20   0     0    0    0 S    0  0.0   1:39.02 kworker/3:1        
   34 root      20   0     0    0    0 S    0  0.0   1:30.30 kswapd0            
  291 root      20   0     0    0    0 D    0  0.0   2:30.40 md0_resync         
  393 root      20   0 17052  632  452 S    0  0.0   8:24.30 upstart-udev-br    
  789 root      20   0     0    0    0 D    0  0.0   6:25.33 jbd2/md0-8         
 1624 root      20   0 65948 1752  768 S    0  0.0   4:29.53 winbindd           


```

```


root@KURMIS:/home/jtupulis# sar -P ALL 5
Linux 2.6.38-11-server (KURMIS) 	09/14/2011 	_x86_64_	(4 CPU)

07:49:06 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:49:11 PM     all      0.95      0.00      2.50     30.63      0.00     65.92
07:49:11 PM       0      0.40      0.00      5.00     85.60      0.00      9.00
07:49:11 PM       1      1.80      0.00      0.80      0.00      0.00     97.40
07:49:11 PM       2      0.00      0.00      2.99     36.93      0.00     60.08
07:49:11 PM       3      1.60      0.00      1.20      0.00      0.00     97.20

07:49:11 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:49:16 PM     all      2.29      0.00      2.89     30.52      0.00     64.29
07:49:16 PM       0      3.60      0.00      6.20     84.00      0.00      6.20
07:49:16 PM       1      1.60      0.00      1.60      2.20      0.00     94.60
07:49:16 PM       2      3.76      0.00      2.77     33.27      0.00     60.20
07:49:16 PM       3      0.20      0.00      1.00      2.60      0.00     96.20

07:49:16 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:49:21 PM     all      0.70      0.00      3.59     29.55      0.00     66.17
07:49:21 PM       0      0.80      0.00      6.00     81.80      0.00     11.40
07:49:21 PM       1      1.20      0.00      1.20      5.99      0.00     91.62
07:49:21 PM       2      0.20      0.00      5.14     30.43      0.00     64.23
07:49:21 PM       3      0.60      0.00      2.00      0.00      0.00     97.40

07:49:21 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:49:26 PM     all      0.90      0.00      2.10     30.69      0.00     66.32
07:49:26 PM       0      0.20      0.00      3.40     88.80      0.00      7.60
07:49:26 PM       1      0.00      0.00      0.60      1.80      0.00     97.60
07:49:26 PM       2      0.60      0.00      2.38     31.35      0.00     65.67
07:49:26 PM       3      2.80      0.00      2.00      0.80      0.00     94.40

07:49:26 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:49:31 PM     all      1.10      0.05      2.24     31.11      0.00     65.50
07:49:31 PM       0      0.40      0.20      3.80     88.40      0.00      7.20
07:49:31 PM       1      1.20      0.00      1.00      0.00      0.00     97.80
07:49:31 PM       2      0.20      0.00      2.96     35.97      0.00     60.87
07:49:31 PM       3      2.60      0.00      1.20      0.00      0.00     96.20

07:49:31 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:49:36 PM     all      1.25      0.05      2.90     29.29      0.00     66.52
07:49:36 PM       0      0.60      0.00      5.99     88.22      0.00      5.19
07:49:36 PM       1      1.40      0.00      1.20      0.20      0.00     97.20
07:49:36 PM       2      0.59      0.20      3.56     26.93      0.00     68.71
07:49:36 PM       3      2.42      0.00      0.81      1.41      0.00     95.35

07:49:36 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:49:41 PM     all      1.15      0.00      2.44     30.48      0.00     65.94
07:49:41 PM       0      0.60      0.00      5.80     87.80      0.00      5.80
07:49:41 PM       1      2.00      0.00      0.20      0.00      0.00     97.80
07:49:41 PM       2      0.20      0.00      2.79     34.46      0.00     62.55
07:49:41 PM       3      1.78      0.00      0.99      0.00      0.00     97.23

07:49:41 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:49:46 PM     all      0.95      0.00      2.35     29.94      0.00     66.77
07:49:46 PM       0      0.40      0.00      5.40     83.40      0.00     10.80
07:49:46 PM       1      1.40      0.00      0.60      0.00      0.00     98.00
07:49:46 PM       2      0.20      0.00      2.99     36.33      0.00     60.48
07:49:46 PM       3      1.80      0.00      0.40      0.00      0.00     97.80

07:49:46 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:49:51 PM     all      0.95      0.00      1.75     35.10      0.00     62.20
07:49:51 PM       0      0.00      0.00      3.80     90.40      0.00      5.80
07:49:51 PM       1      2.20      0.00      0.20      0.00      0.00     97.60
07:49:51 PM       2      0.20      0.00      2.20     50.00      0.00     47.60
07:49:51 PM       3      1.40      0.00      0.80      0.00      0.00     97.80

07:49:51 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:49:56 PM     all      1.00      0.45      3.54     30.79      0.00     64.23
07:49:56 PM       0      0.00      1.20      5.20     81.20      0.00     12.40
07:49:56 PM       1      2.00      0.20      1.80      1.20      0.00     94.81
07:49:56 PM       2      0.00      0.20      5.35     39.80      0.00     54.65
07:49:56 PM       3      2.00      0.20      1.80      1.00      0.00     95.01

07:49:56 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:01 PM     all      1.45      0.00      2.75     34.40      0.00     61.41
07:50:01 PM       0      0.20      0.00      5.00     86.60      0.00      8.20
07:50:01 PM       1      1.99      0.00      0.60      0.40      0.00     97.01
07:50:01 PM       2      0.60      0.00      2.79     50.10      0.00     46.51
07:50:01 PM       3      3.00      0.00      2.60      0.60      0.00     93.80

07:50:01 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:06 PM     all      1.15      0.00      1.99     35.91      0.00     60.96
07:50:06 PM       0      0.40      0.00      3.40     91.80      0.00      4.40
07:50:06 PM       1      1.19      0.00      0.20      0.00      0.00     98.61
07:50:06 PM       2      0.00      0.00      2.58     51.98      0.00     45.44
07:50:06 PM       3      2.99      0.00      1.80      0.00      0.00     95.21

07:50:06 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:11 PM     all      0.95      0.00      2.60     32.73      0.00     63.72
07:50:11 PM       0      1.20      0.00      6.18     89.04      0.00      3.59
07:50:11 PM       1      0.00      0.00      0.60      0.20      0.00     99.20
07:50:11 PM       2      0.40      0.00      2.58     41.35      0.00     55.67
07:50:11 PM       3      2.21      0.00      1.21      0.00      0.00     96.58

07:50:11 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:16 PM     all      1.09      0.00      2.48     32.13      0.00     64.30
07:50:16 PM       0      0.40      0.00      3.80     88.80      0.00      7.00
07:50:16 PM       1      1.00      0.00      0.40      1.59      0.00     97.01
07:50:16 PM       2      1.19      0.00      3.76     38.42      0.00     56.63
07:50:16 PM       3      1.78      0.00      1.78      0.00      0.00     96.44

07:50:16 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:21 PM     all      0.80      0.00      2.05     32.88      0.00     64.27
07:50:21 PM       0      0.60      0.00      3.59     88.42      0.00      7.39
07:50:21 PM       1      1.60      0.00      0.60      4.21      0.00     93.59
07:50:21 PM       2      0.20      0.00      2.58     38.57      0.00     58.65
07:50:21 PM       3      0.80      0.00      1.40      0.20      0.00     97.60

07:50:21 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:26 PM     all      0.90      0.00      2.35     31.04      0.00     65.72
07:50:26 PM       0      1.00      0.00      4.60     86.20      0.00      8.20
07:50:26 PM       1      0.20      0.00      0.99      0.00      0.00     98.81
07:50:26 PM       2      0.20      0.00      2.40     37.92      0.00     59.48
07:50:26 PM       3      2.20      0.00      1.40      0.20      0.00     96.20

07:50:26 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:31 PM     all      1.20      0.00      3.24     27.53      0.00     68.03
07:50:31 PM       0      0.60      0.00      6.80     67.20      0.00     25.40
07:50:31 PM       1      1.20      0.00      1.00      2.99      0.00     94.81
07:50:31 PM       2      0.60      0.00      2.78     38.57      0.00     58.05
07:50:31 PM       3      2.40      0.00      2.40      1.40      0.00     93.81

07:50:31 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:36 PM     all      0.80      0.00      2.60     31.20      0.00     65.40
07:50:36 PM       0      0.00      0.00      4.60     90.00      0.00      5.40
07:50:36 PM       1      1.60      0.00      0.60      1.20      0.00     96.60
07:50:36 PM       2      0.00      0.00      4.37     33.60      0.00     62.03
07:50:36 PM       3      1.60      0.00      0.80      0.00      0.00     97.60

07:50:36 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:41 PM     all      1.05      0.00      1.75     31.39      0.00     65.82
07:50:41 PM       0      0.60      0.00      4.00     85.00      0.00     10.40
07:50:41 PM       1      1.00      0.00      0.40      0.00      0.00     98.60
07:50:41 PM       2      0.39      0.00      1.97     40.04      0.00     57.59
07:50:41 PM       3      2.21      0.00      0.60      0.20      0.00     96.99

07:50:41 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:46 PM     all      1.15      0.00      1.89     35.46      0.00     61.50
07:50:46 PM       0      0.20      0.00      3.80     90.20      0.00      5.80
07:50:46 PM       1      1.39      0.00      0.80      0.00      0.00     97.81
07:50:46 PM       2      0.00      0.00      1.60     51.10      0.00     47.31
07:50:46 PM       3      2.98      0.00      1.39      0.99      0.00     94.64

07:50:46 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:51 PM     all      0.95      0.00      1.89     34.88      0.00     62.29
07:50:51 PM       0      0.60      0.00      4.20     87.40      0.00      7.80
07:50:51 PM       1      1.00      0.00      0.80      0.00      0.00     98.20
07:50:51 PM       2      0.00      0.00      1.96     51.76      0.00     46.27
07:50:51 PM       3      2.20      0.00      0.60      0.00      0.00     97.20

07:50:51 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:50:56 PM     all      1.10      0.00      1.94     33.68      0.00     63.28
07:50:56 PM       0      0.40      0.00      3.60     92.60      0.00      3.40
07:50:56 PM       1      0.40      0.00      0.20      0.00      0.00     99.40
07:50:56 PM       2      0.20      0.00      2.16     41.76      0.00     55.88
07:50:56 PM       3      3.39      0.00      1.80      0.00      0.00     94.81

07:50:56 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:01 PM     all      1.05      0.00      2.04     32.21      0.00     64.71
07:51:01 PM       0      0.80      0.00      2.80     84.80      0.00     11.60
07:51:01 PM       1      1.39      0.00      0.99      0.40      0.00     97.23
07:51:01 PM       2      0.79      0.00      2.18     43.85      0.00     53.17
07:51:01 PM       3      1.20      0.00      2.20      0.00      0.00     96.60

07:51:01 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:06 PM     all      0.80      0.00      3.59     30.94      0.00     64.67
07:51:06 PM       0      0.40      0.00      6.37     85.46      0.00      7.77
07:51:06 PM       1      0.40      0.00      0.20      0.00      0.00     99.40
07:51:06 PM       2      0.00      0.00      5.15     37.82      0.00     57.03
07:51:06 PM       3      2.40      0.00      2.60      0.20      0.00     94.80

07:51:06 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:11 PM     all      1.00      0.05      2.59     33.77      0.00     62.59
07:51:11 PM       0      0.20      0.00      4.80     86.20      0.00      8.80
07:51:11 PM       1      1.20      0.20      0.80      0.00      0.00     97.80
07:51:11 PM       2      0.20      0.00      2.77     48.71      0.00     48.32
07:51:11 PM       3      2.40      0.00      2.00      0.00      0.00     95.60

07:51:11 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:16 PM     all      0.75      0.00      1.80     34.47      0.00     62.99
07:51:16 PM       0      0.00      0.00      3.98     89.24      0.00      6.77
07:51:16 PM       1      1.40      0.00      0.40      0.00      0.00     98.20
07:51:16 PM       2      0.00      0.00      1.60     48.40      0.00     50.00
07:51:16 PM       3      1.60      0.00      1.20      0.00      0.00     97.20

07:51:16 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:21 PM     all      1.20      0.00      2.54     34.16      0.00     62.10
07:51:21 PM       0      0.20      0.00      4.20     93.00      0.00      2.60
07:51:21 PM       1      1.20      0.00      0.80      0.00      0.00     98.00
07:51:21 PM       2      0.79      0.00      3.15     43.50      0.00     52.56
07:51:21 PM       3      2.60      0.00      2.00      0.00      0.00     95.40

07:51:21 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:26 PM     all      1.30      0.00      2.09     34.31      0.00     62.29
07:51:26 PM       0      1.00      0.00      3.60     88.60      0.00      6.80
07:51:26 PM       1      1.40      0.00      0.60      0.80      0.00     97.20
07:51:26 PM       2      0.59      0.00      3.17     47.72      0.00     48.51
07:51:26 PM       3      2.20      0.00      1.00      0.00      0.00     96.80

07:51:26 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:31 PM     all      0.90      0.00      2.41     34.82      0.00     61.87
07:51:31 PM       0      1.00      0.00      3.99     85.23      0.00      9.78
07:51:31 PM       1      1.22      0.00      0.81      0.00      0.00     97.96
07:51:31 PM       2      0.40      0.00      3.39     51.90      0.00     44.31
07:51:31 PM       3      1.00      0.00      1.40      1.40      0.00     96.20

07:51:31 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:36 PM     all      0.79      0.05      2.43     27.90      0.00     68.82
07:51:36 PM       0      0.20      0.00      5.00     78.40      0.00     16.40
07:51:36 PM       1      0.39      0.20      0.00      0.00      0.00     99.41
07:51:36 PM       2      0.40      0.00      3.18     33.60      0.00     62.82
07:51:36 PM       3      2.19      0.00      1.59      0.20      0.00     96.02

07:51:36 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:41 PM     all      1.14      0.00      2.19     33.30      0.00     63.36
07:51:41 PM       0      0.20      0.00      4.20     89.20      0.00      6.40
07:51:41 PM       1      1.00      0.00      0.60      0.60      0.00     97.80
07:51:41 PM       2      0.20      0.00      2.36     43.11      0.00     54.33
07:51:41 PM       3      3.20      0.00      1.60      0.20      0.00     95.00

07:51:41 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:46 PM     all      1.00      0.00      2.20     34.92      0.00     61.89
07:51:46 PM       0      1.20      0.00      4.40     89.60      0.00      4.80
07:51:46 PM       1      0.20      0.00      0.60      1.00      0.00     98.20
07:51:46 PM       2      0.40      0.00      2.19     48.91      0.00     48.51
07:51:46 PM       3      2.20      0.00      1.60      0.00      0.00     96.20

07:51:46 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:51 PM     all      0.95      0.00      2.39     32.72      0.00     63.94
07:51:51 PM       0      0.60      0.00      4.60     89.80      0.00      5.00
07:51:51 PM       1      0.60      0.00      0.60      0.00      0.00     98.80
07:51:51 PM       2      0.20      0.00      2.78     41.07      0.00     55.95
07:51:51 PM       3      2.40      0.00      1.60      0.00      0.00     96.00

07:51:51 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:51:56 PM     all      0.80      0.05      2.29     32.02      0.00     64.84
07:51:56 PM       0      0.20      0.00      4.60     84.20      0.00     11.00
07:51:56 PM       1      0.80      0.20      0.80      1.40      0.00     96.81
07:51:56 PM       2      0.00      0.00      1.79     42.54      0.00     55.67
07:51:56 PM       3      2.20      0.00      2.00      0.00      0.00     95.81

07:51:56 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:01 PM     all      1.20      0.00      2.40     31.88      0.00     64.52
07:52:01 PM       0      0.40      0.00      4.20     88.20      0.00      7.20
07:52:01 PM       1      0.60      0.00      0.00      0.00      0.00     99.40
07:52:01 PM       2      0.40      0.00      4.00     39.40      0.00     56.20
07:52:01 PM       3      3.40      0.00      1.40      0.00      0.00     95.20

07:52:01 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:06 PM     all      0.80      0.00      2.15     33.10      0.00     63.95
07:52:06 PM       0      0.40      0.00      4.19     90.22      0.00      5.19
07:52:06 PM       1      0.80      0.00      0.80      1.00      0.00     97.40
07:52:06 PM       2      0.40      0.00      2.39     41.04      0.00     56.18
07:52:06 PM       3      1.60      0.00      1.20      0.00      0.00     97.20

07:52:06 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:11 PM     all      1.15      0.00      2.64     28.08      0.00     68.13
07:52:11 PM       0      0.80      0.00      5.00     80.60      0.00     13.60
07:52:11 PM       1      1.00      0.00      0.60      0.00      0.00     98.41
07:52:11 PM       2      0.60      0.00      3.98     31.01      0.00     64.41
07:52:11 PM       3      2.20      0.00      1.00      0.80      0.00     96.00

07:52:11 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:16 PM     all      1.00      0.05      2.20     33.73      0.00     63.02
07:52:16 PM       0      0.00      0.20      4.00     87.60      0.00      8.20
07:52:16 PM       1      2.00      0.00      1.20      1.00      0.00     95.80
07:52:16 PM       2      0.20      0.00      2.20     46.31      0.00     51.30
07:52:16 PM       3      1.80      0.00      1.40      0.00      0.00     96.80

07:52:16 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:21 PM     all      1.00      0.00      2.05     32.50      0.00     64.45
07:52:21 PM       0      0.80      0.00      3.60     84.00      0.00     11.60
07:52:21 PM       1      0.80      0.00      0.60      0.00      0.00     98.60
07:52:21 PM       2      0.20      0.00      2.58     45.92      0.00     51.29
07:52:21 PM       3      2.20      0.00      1.40      0.00      0.00     96.40

07:52:21 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:26 PM     all      1.20      0.00      2.69     32.04      0.00     64.08
07:52:26 PM       0      0.80      0.00      5.20     89.80      0.00      4.20
07:52:26 PM       1      1.00      0.00      0.40      0.00      0.00     98.60
07:52:26 PM       2      0.79      0.00      3.37     38.42      0.00     57.43
07:52:26 PM       3      2.20      0.00      1.80      0.00      0.00     96.01

07:52:26 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:31 PM     all      1.21      0.00      2.11     32.48      0.00     64.20
07:52:31 PM       0      0.00      0.00      4.79     90.62      0.00      4.59
07:52:31 PM       1      1.00      0.00      0.40      1.20      0.00     97.41
07:52:31 PM       2      0.60      0.00      2.40     36.20      0.00     60.80
07:52:31 PM       3      3.31      0.00      0.83      0.83      0.00     95.04

07:52:31 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:36 PM     all      1.48      0.00      1.93     34.42      0.00     62.17
07:52:36 PM       0      0.80      0.00      3.80     90.60      0.00      4.80
07:52:36 PM       1      1.39      0.00      0.20      0.00      0.00     98.41
07:52:36 PM       2      1.80      0.00      2.40     39.52      0.00     56.29
07:52:36 PM       3      1.93      0.00      1.35      8.67      0.00     88.05

07:52:36 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:41 PM     all      1.15      0.00      1.95     34.33      0.00     62.56
07:52:41 PM       0      0.60      0.00      3.00     91.40      0.00      5.00
07:52:41 PM       1      0.00      0.00      0.60      2.00      0.00     97.41
07:52:41 PM       2      0.40      0.00      3.00     43.80      0.00     52.80
07:52:41 PM       3      3.62      0.00      1.21      0.00      0.00     95.17

07:52:41 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:46 PM     all      0.95      0.00      2.49     26.64      0.00     69.92
07:52:46 PM       0      0.80      0.00      3.80     77.00      0.00     18.40
07:52:46 PM       1      1.20      0.00      1.00      0.00      0.00     97.80
07:52:46 PM       2      0.40      0.00      3.97     29.56      0.00     66.07
07:52:46 PM       3      1.39      0.00      1.19      0.20      0.00     97.22

07:52:46 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:51 PM     all      1.00      0.00      2.44     31.87      0.00     64.69
07:52:51 PM       0      0.80      0.00      4.59     87.03      0.00      7.58
07:52:51 PM       1      1.40      0.00      1.20      0.00      0.00     97.40
07:52:51 PM       2      0.40      0.00      2.58     39.68      0.00     57.34
07:52:51 PM       3      1.40      0.00      1.40      0.60      0.00     96.60

07:52:51 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:52:56 PM     all      0.85      0.00      2.05     33.95      0.00     63.14
07:52:56 PM       0      0.80      0.00      4.40     85.20      0.00      9.60
07:52:56 PM       1      0.61      0.00      0.00      0.00      0.00     99.39
07:52:56 PM       2      0.00      0.00      2.38     50.00      0.00     47.62
07:52:56 PM       3      2.00      0.00      1.40      0.00      0.00     96.60

07:52:56 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:01 PM     all      0.90      0.00      2.14     33.05      0.00     63.91
07:53:01 PM       0      0.00      0.00      3.80     94.60      0.00      1.60
07:53:01 PM       1      0.98      0.00      0.39      0.00      0.00     98.62
07:53:01 PM       2      0.20      0.00      2.79     38.12      0.00     58.88
07:53:01 PM       3      2.40      0.00      1.60      0.00      0.00     96.00

07:53:01 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:06 PM     all      0.80      0.00      2.10     32.65      0.00     64.45
07:53:06 PM       0      0.60      0.00      3.80     88.80      0.00      6.80
07:53:06 PM       1      0.00      0.00      0.40      1.00      0.00     98.60
07:53:06 PM       2      0.00      0.00      1.99     40.76      0.00     57.26
07:53:06 PM       3      2.60      0.00      2.20      0.00      0.00     95.20

07:53:06 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:11 PM     all      0.95      0.00      2.29     33.32      0.00     63.44
07:53:11 PM       0      0.20      0.00      4.40     92.00      0.00      3.40
07:53:11 PM       1      1.60      0.00      0.60      0.40      0.00     97.40
07:53:11 PM       2      0.20      0.00      3.37     40.79      0.00     55.64
07:53:11 PM       3      1.80      0.00      0.80      0.00      0.00     97.40

07:53:11 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:16 PM     all      0.90      0.00      2.15     33.65      0.00     63.31
07:53:16 PM       0      0.80      0.00      3.80     88.00      0.00      7.40
07:53:16 PM       1      0.80      0.00      0.80      1.20      0.00     97.20
07:53:16 PM       2      0.00      0.00      2.98     44.73      0.00     52.29
07:53:16 PM       3      2.00      0.00      1.00      0.60      0.00     96.40

07:53:16 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:21 PM     all      0.80      0.00      3.90     26.27      0.00     69.03
07:53:21 PM       0      0.60      0.00      6.59     70.46      0.00     22.36
07:53:21 PM       1      0.00      0.00      2.00      0.20      0.00     97.80
07:53:21 PM       2      0.40      0.00      4.55     31.88      0.00     63.17
07:53:21 PM       3      2.22      0.00      2.42      2.22      0.00     93.15

07:53:21 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:26 PM     all      0.90      0.00      1.99     34.46      0.00     62.65
07:53:26 PM       0      0.20      0.00      3.00     92.40      0.00      4.40
07:53:26 PM       1      0.60      0.00      0.00      0.00      0.00     99.40
07:53:26 PM       2      0.00      0.00      3.19     45.62      0.00     51.20
07:53:26 PM       3      2.78      0.00      1.79      0.20      0.00     95.24

07:53:26 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:31 PM     all      1.00      0.00      1.85     33.62      0.00     63.54
07:53:31 PM       0      0.20      0.00      3.80     89.80      0.00      6.20
07:53:31 PM       1      0.40      0.00      0.20      0.00      0.00     99.40
07:53:31 PM       2      0.60      0.00      1.79     44.62      0.00     52.99
07:53:31 PM       3      2.80      0.00      1.60      0.00      0.00     95.60

07:53:31 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:36 PM     all      1.05      0.00      1.90     35.08      0.00     61.97
07:53:36 PM       0      0.40      0.00      3.20     89.20      0.00      7.20
07:53:36 PM       1      1.20      0.00      1.00      0.00      0.00     97.80
07:53:36 PM       2      0.20      0.00      2.40     49.80      0.00     47.60
07:53:36 PM       3      2.40      0.00      1.00      1.40      0.00     95.20

07:53:36 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:41 PM     all      1.04      0.00      2.64     29.94      0.00     66.38
07:53:41 PM       0      0.20      0.00      5.60     82.40      0.00     11.80
07:53:41 PM       1      0.40      0.00      0.40      0.00      0.00     99.20
07:53:41 PM       2      0.78      0.00      2.73     35.67      0.00     60.82
07:53:41 PM       3      2.81      0.00      1.81      1.41      0.00     93.98

07:53:41 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:46 PM     all      1.05      0.00      2.10     32.85      0.00     64.00
07:53:46 PM       0      0.80      0.00      3.80     89.60      0.00      5.80
07:53:46 PM       1      0.40      0.00      0.40      0.00      0.00     99.20
07:53:46 PM       2      0.00      0.00      2.79     41.92      0.00     55.29
07:53:46 PM       3      2.99      0.00      1.39      0.00      0.00     95.62

07:53:46 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:51 PM     all      1.04      0.05      2.78     32.89      0.00     63.24
07:53:51 PM       0      1.00      0.00      4.79     81.04      0.00     13.17
07:53:51 PM       1      1.79      0.00      1.79      0.00      0.00     96.41
07:53:51 PM       2      0.20      0.20      2.75     48.92      0.00     47.94
07:53:51 PM       3      1.20      0.00      1.80      1.40      0.00     95.61

07:53:51 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:53:56 PM     all      0.70      0.00      2.50     30.97      0.00     65.83
07:53:56 PM       0      0.40      0.00      4.78     80.28      0.00     14.54
07:53:56 PM       1      0.60      0.00      0.60      0.00      0.00     98.80
07:53:56 PM       2      0.60      0.00      2.98     42.94      0.00     53.48
07:53:56 PM       3      1.22      0.00      1.62      0.00      0.00     97.16

07:53:56 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:54:01 PM     all      0.60      0.00      1.93     32.19      0.00     65.28
07:54:01 PM       0      0.40      0.00      2.99     92.22      0.00      4.39
07:54:01 PM       1      1.20      0.00      0.80      0.60      0.00     97.40
07:54:01 PM       2      0.00      0.00      2.37     36.36      0.00     61.26
07:54:01 PM       3      0.79      0.00      1.57      0.00      0.00     97.64

07:54:01 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:54:06 PM     all      1.35      0.00      2.60     31.03      0.00     65.02
07:54:06 PM       0      0.20      0.00      4.99     84.83      0.00      9.98
07:54:06 PM       1      2.00      0.00      0.80      0.00      0.00     97.20
07:54:06 PM       2      0.59      0.00      2.76     38.46      0.00     58.19
07:54:06 PM       3      2.65      0.00      1.84      0.00      0.00     95.51

07:54:06 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:54:11 PM     all      0.84      0.00      2.29     33.15      0.00     63.72
07:54:11 PM       0      0.20      0.00      3.60     90.40      0.00      5.80
07:54:11 PM       1      1.20      0.00      1.40      0.80      0.00     96.61
07:54:11 PM       2      0.20      0.00      2.57     41.78      0.00     55.45
07:54:11 PM       3      1.78      0.00      1.58      0.00      0.00     96.64

07:54:11 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:54:16 PM     all      1.04      0.05      2.93     31.92      0.00     64.05
07:54:16 PM       0      0.00      0.00      6.00     86.80      0.00      7.20
07:54:16 PM       1      0.80      0.20      1.00      0.00      0.00     98.00
07:54:16 PM       2      0.00      0.00      3.17     41.19      0.00     55.64
07:54:16 PM       3      3.37      0.00      1.58      0.00      0.00     95.05

07:54:16 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:54:21 PM     all      0.75      0.00      1.76     34.47      0.00     63.02
07:54:21 PM       0      0.00      0.00      3.60     90.00      0.00      6.40
07:54:21 PM       1      2.24      0.00      0.00      0.00      0.00     97.76
07:54:21 PM       2      0.00      0.00      1.99     47.21      0.00     50.80
07:54:21 PM       3      0.80      0.00      1.40      0.00      0.00     97.80

07:54:21 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:54:26 PM     all      2.33      0.00      2.92     31.52      0.00     63.23
07:54:26 PM       0      2.39      0.00      5.58     78.49      0.00     13.55
07:54:26 PM       1      2.54      0.00      2.54      0.00      0.00     94.91
07:54:26 PM       2      1.78      0.00      2.57     42.57      0.00     53.07
07:54:26 PM       3      2.60      0.00      1.00      5.40      0.00     91.00

07:54:26 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:54:31 PM     all      0.60      0.00      2.02     33.37      0.00     64.01
07:54:31 PM       0      0.00      0.00      3.40     89.20      0.00      7.40
07:54:31 PM       1      0.20      0.00      1.00      0.00      0.00     98.80
07:54:31 PM       2      0.20      0.00      1.99     43.03      0.00     54.78
07:54:31 PM       3      2.07      0.00      1.66      0.00      0.00     96.27

07:54:31 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:54:36 PM     all      0.84      0.00      2.07     33.32      0.00     63.77
07:54:36 PM       0      0.00      0.00      4.40     88.80      0.00      6.80
07:54:36 PM       1      0.60      0.00      0.40      0.00      0.00     99.00
07:54:36 PM       2      0.79      0.00      2.37     44.18      0.00     52.66
07:54:36 PM       3      1.93      0.00      1.16      1.35      0.00     95.56

07:54:36 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:54:41 PM     all      1.00      0.00      2.29     34.01      0.00     62.70
07:54:41 PM       0      0.80      0.00      3.99     90.62      0.00      4.59
07:54:41 PM       1      1.00      0.00      1.00      0.00      0.00     98.00
07:54:41 PM       2      0.00      0.00      3.55     45.17      0.00     51.28
07:54:41 PM       3      2.20      0.00      0.60      0.00      0.00     97.20

07:54:41 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
07:54:46 PM     all      1.05      0.00      2.60     33.40      0.00     62.95
07:54:46 PM       0      0.20      0.00      5.00     90.00      0.00      4.80
07:54:46 PM       1      1.20      0.00      0.60      0.00      0.00     98.20
07:54:46 PM       2      0.20      0.00      3.00     43.60      0.00     53.20
07:54:46 PM       3      2.60      0.00      1.80      0.00      0.00     95.60

```

```


root@KURMIS:/home/jtupulis# vmstat 5
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0    148  43608 354720 2770928    0    0   343   480   63   22  1  2 72 25
 0  0    148  29392 354236 2783900    0    0   402 10188  799 1843  1  3 67 28
 0  0    148  30184 353620 2783928    0    0   323  9715  748 1759  1  2 64 32
 0  2    148  36948 352976 2776184    0    0   370  9522  771 1826  1  2 67 30
 0  2    148  36752 352348 2778976    0    0   385 11282  798 2074  2  3 64 31
 0  2    148  87464 351132 2728836    0    0   360 10168  819 2556  1  4 66 30
 0  2    148  40432 351248 2775924    0    0   282  9495  745 1702  1  2 67 29
 0  2    148  34884 350916 2781476    0    0   307  8893  724 1667  1  2 65 32
 0  1    148  29120 350560 2786888    0    0   308  8900  763 1760  1  3 67 29
 0  2    148  28556 350128 2790364    0    0   334  9558  763 1819  1  2 66 31
 1  1    148  34756 349608 2782748    0    0   334  8565  751 1741  1  2 66 31
 0  2    148  34652 349384 2782600    0    0   313  6850  716 1607  1  2 64 33
 1  1    148  89932 348376 2727852    0    0   322  6642  814 2660  1  4 64 31
 0  2    148  56516 348504 2762368    0    0   359  6945  744 1577  1  3 62 34
 0  2    148  31400 348516 2788636    0    0   385  7334  734 1575  1  2 62 35
 1  2    148  28472 348220 2791360    0    0   383  8002  757 1659  1  3 62 35
 0  2    148  32132 347708 2786148    0    0   363  8325  757 1727  1  2 65 32
 0  1    148  33924 347260 2785456    0    0   364  7963  747 1735  1  2 64 33
 0  1    148  31776 346852 2786772    0    0   335  6837  695 1532  1  2 66 31
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  2    148  27760 346472 2791668    0    0   363  8562  851 3094  1  4 68 27
 0  1    148  32040 346112 2786372    0    0   359  8579  754 1669  1  2 66 32
 0  2    148  27740 345820 2791928    0    0   309  7474  728 1665  1  2 67 30
 0  1    148  28784 345456 2789564    0    0   333  6704  729 1630  1  2 60 36
 0  1    148  27780 345104 2790912    0    0   368  7330  720 1576  1  2 63 34
 1  1    148  26916 344580 2791804    0    0   358  8164  763 1707  1  2 63 33
 0  2    148  28892 344164 2790172    0    0   389  7824  775 1717  1  2 62 35
 0  2    148  73264 343052 2746792    0    0   334  6878  808 2555  1  3 66 30
 0  1    148  41076 343152 2778928    0    0   359  6496  741 1596  1  3 63 33
 0  2    148  29984 342796 2788840    0    0   358  7164  731 1606  1  2 64 33
 0  1    148  29040 342480 2790064    0    0   359  6943  730 1579  1  2 62 35
 0  1    148  28504 342060 2790888    0    0   384  7179  757 1665  1  2 62 35
 0  2    148  34036 341436 2785916    0    0   375  7126  726 1638  1  2 62 35
 0  2    148  71712 340512 2748608    0    0   288  6163  751 2299  1  2 68 29
 0  2    148  33480 340616 2786064    0    0   358  7558  774 1796  1  2 63 33
 4  1    148  31684 340232 2787848    0    0   386  7473  742 1725  1  2 62 35
 0  2    148  27012 339820 2791696    0    0   386  7882  755 1706  1  2 64 33
 0  2    148  31552 339408 2788364    0    0   262  5945  678 1527  1  2 65 32
 0  2    148  30628 338924 2788052    0    0   359  7558  746 1686  1  2 64 32
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  2    148  34560 338424 2786364    0    0   358  7720  735 1560  1  2 65 32
 0  2    148  83220 337180 2736364    0    0   334  7900  799 2343  1  3 67 29
 0  1    148  45704 337288 2773768    0    0   358  7553  742 1668  1  2 64 33
 0  2    148  35400 336996 2784248    0    0   397  7196  745 1654  1  2 64 33
 1  1    148  34128 336492 2784896    0    0   359  7737  762 1647  1  3 66 30
 0  1    148  37156 335968 2782092    0    0   359  8006  759 1715  1  2 64 33
 1  1    148  32580 335608 2786680    0    0   362  7360  738 1720  2  2 62 35
 0  1    148  32016 335160 2787624    0    0   384  7399  755 1705  1  2 63 34
 0  2    148  55344 334448 2765028    0    0   309  5966  749 2430  1  2 70 27
 0  2    148  30476 334356 2789332    0    0   358  7338  744 1701  1  2 64 32
 0  1    148  32420 333848 2787552    0    0   334  6689  721 1565  1  2 64 34
 0  2    148  33244 333344 2786232    0    0   384  7390  754 1680  1  2 64 32
 1  2    148  35660 332916 2783984    0    0   360  6950  730 1620  1  2 64 33
 1  2    148  31412 332484 2786276    0    0   384  7590  751 1744  1  3 62 35
 0  2    148  28960 332144 2791904    0    0   360  7168  743 1650  1  2 64 33
 0  2    148  51300 331392 2769804    0    0   324  6830  777 2417  1  3 70 26
 0  2    148  27020 331292 2793144    0    0   384  7198  752 1637  1  2 63 34
 1  1    148  37440 330716 2782392    0    0   385  6928  733 1674  1  2 63 35
 0  2    148  29220 330484 2791024    0    0   335  7309  733 1721  1  2 63 34
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1    148  28404 329976 2791284    0    0   341  7302  725 1629  1  2 67 30
 0  1    148  29052 329448 2790916    0    0   370  8562  765 1772  1  2 63 34
 0  1    148  31988 328832 2788764    0    0   361  8160  736 1679  1  2 63 34
 0  1    148  32816 328576 2787132    0    0   287  6402  778 2371  1  3 66 29
 0  2    148  27648 328184 2793500    0    0   360  7724  735 1670  1  2 64 33
 0  2    148  31292 325880 2791352    0    0   334  7930  743 1680  1  2 65 32
 0  1    148  30616 325380 2794740    0    0   385  7795  743 1684  1  2 65 32
 0  2    148  32584 325020 2802352    0    0   373  7105  743 1636  1  3 64 32
 0  1    148  36064 324552 2798652    0    0   358  7339  732 1648  1  2 63 34
 0  3    148  94376 323200 2741040    0    0   430  7574  819 2557  2  3 63 31
 0  2    148  60732 323340 2775052    0    0   334  6877  707 1587  1  2 64 34
 0  2    148  35792 323260 2798240    0    0   358  6730  738 1628  1  2 64 34
 1  2    148  28384 322900 2805532    0    0   334  6498  725 1588  1  2 63 34
 0  1    148  34968 322668 2799028    0    0   384  6945  738 1666  1  3 63 34
 0  1    148  36284 322696 2798624    0    0   359  7132  741 1598  1  2 62 34
 0  2    148  33284 322748 2800708    0    0   372  6954  731 1630  2  2 61 35
 0  1    148  93240 322660 2741348    0    0   338  5832  750 2241  1  2 65 32
 0  1    148  60472 322764 2774764    0    0   393  6741  715 1542  1  2 62 35
 1  2    148  32956 322836 2801596    0    0   334  7899  736 1659  1  2 63 34
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  3    148  28996 322828 2805124    0    0   378  8586  751 1744  1  3 66 30
 0  1    148  33588 322856 2802252    0    0   308  8062  723 1751  1  1 66 32
 0  2    148  38452 322884 2796616    0    0   358  8581  765 1789  1  2 64 33
 0  1    148  34080 322908 2800764    0    0   359  7775  743 1632  1  3 64 32
 0  2    148  79204 322820 2756212    0    0   335  7881  772 2325  1  4 64 31
 0  2    148  33188 322936 2802040    0    0   385  9239  780 1821  1  3 63 33
 0  2    148  36632 322924 2798064    0    0   359  8385  754 1718  1  2 63 34
 0  0    148  31548 322952 2802836    0    0   360  7131  714 1561  1  2 64 33
 0  2    148  29496 322940 2805288    0    0   384  7960  727 1587  1  2 64 34
 0  2    148  36824 322912 2801500    0    0   334  7118  723 1613  1  2 61 36
 0  2    148  26932 322976 2820560    0    0   360  6775  707 1521  1  3 64 32
 0  1    148  71060 322840 2776604    0    0   309  6654  790 2504  1  3 66 30
 0  1    148  36960 322956 2809756    0    0   360  6694  731 1605  1  2 62 34
 0  2    148  28056 322956 2819232    0    0   372  7145  726 1603  1  2 66 31
 0  1    148  37280 322976 2809116    0    0   371  6926  722 1576  1  2 61 35
 0  1    148  34080 323016 2812764    0    0   390  6948  738 1646  1  1 64 34
 0  2    148  35148 323036 2811796    0    0   390  6927  711 1574  1  2 64 33
 0  0    148  36060 323028 2810480    0    0   359  7561  808 2280  1  3 64 32
 1  2    148  72424 322920 2775860    0    0   309  7024  755 2270  1  3 66 30

```

iostat

```

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              57.00         0.00         4.24          0         21
sdc              58.60         0.00         4.34          0         21
sdd              57.40         0.00         4.34          0         21
sde               2.80         0.33         0.00          1          0
sdb              56.80         0.00         4.23          0         21
md0            2226.40         0.00         8.67          0         43
sdf              28.60         0.02         0.11          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              57.20         0.00         4.08          0         20
sdc              52.20         0.00         3.98          0         19
sdd              52.20         0.00         3.98          0         19
sde               2.60         0.33         0.00          1          0
sdb              58.00         0.00         4.08          0         20
md0            2069.00         0.00         8.06          0         40
sdf              16.40         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              53.20         0.00         3.91          0         19
sdc              57.40         0.00         3.89          0         19
sdd              57.20         0.00         3.89          0         19
sde               3.00         0.35         0.00          1          0
sdb              52.40         0.00         3.91          0         19
md0            1979.40         0.00         7.71          0         38
sdf              24.40         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              59.40         2.11         3.93         10         19
sdc              61.00         0.15         3.98          0         19
sdd              60.60         0.22         3.98          1         19
sde               2.80         0.35         0.00          1          0
sdb              58.60         2.06         3.92         10         19
md0            2030.00         0.00         7.90          0         39
sdf              25.80         0.00         0.10          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              63.00         1.24         4.08          6         20
sdc              58.40         3.23         3.96         16         19
sdd              58.00         3.15         3.96         15         19
sde               2.60         0.33         0.00          1          0
sdb              62.40         1.29         4.08          6         20
md0            2115.20         0.00         8.24          0         41
sdf              22.00         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              62.80         0.00         4.19          0         20
sdc              58.40         0.00         4.27          0         21
sdd              60.20         0.00         4.27          0         21
sde               3.20         0.38         0.00          1          0
sdb              61.60         0.00         4.19          0         20
md0            2148.80         0.00         8.37          0         41
sdf              17.00         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              55.40         0.00         3.93          0         19
sdc              57.20         0.00         3.89          0         19
sdd              57.20         0.00         3.89          0         19
sde               2.80         0.35         0.00          1          0
sdb              55.00         0.00         3.93          0         19
md0            1981.80         0.00         7.71          0         38
sdf              23.60         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              46.40         0.00         3.39          0         16
sdc              50.60         0.00         3.50          0         17
sdd              53.20         0.00         3.49          0         17
sde               3.00         0.35         0.00          1          0
sdb              46.20         0.00         3.40          0         16
md0            1768.00         0.00         6.89          0         34
sdf              16.20         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              58.60         0.00         3.99          0         19
sdc              57.00         0.00         3.94          0         19
sdd              56.60         0.00         3.95          0         19
sde               3.00         0.38         0.00          1          0
sdb              58.40         0.00         3.99          0         19
md0            2038.80         0.00         7.94          0         39
sdf              20.60         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              48.40         0.00         3.30          0         16
sdc              45.00         0.00         3.17          0         15
sdd              46.20         0.00         3.17          0         15
sde               2.80         0.33         0.00          1          0
sdb              50.00         0.00         3.30          0         16
md0            1661.00         0.00         6.47          0         32
sdf              22.60         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              59.60         4.55         3.01         22         15
sdc              69.40         4.51         3.29         22         16
sdd              67.80         4.51         3.29         22         16
sde               2.40         0.30         0.00          1          0
sdb              58.60         4.55         3.03         22         15
md0            1644.40         0.00         6.40          0         32
sdf              25.80         0.00         0.12          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              51.80         0.00         3.39          0         16
sdc              50.80         0.01         3.24          0         16
sdd              51.20         0.01         3.24          0         16
sde               3.20         0.38         0.00          1          0
sdb              52.20         0.00         3.37          0         16
md0            1679.40         0.00         6.54          0         32
sdf              18.80         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              52.60         0.00         3.40          0         17
sdc              47.20         0.00         3.28          0         16
sdd              47.60         0.00         3.28          0         16
sde               2.60         0.33         0.00          1          0
sdb              52.80         0.00         3.40          0         17
md0            1714.80         0.00         6.68          0         33
sdf              21.20         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              45.20         0.00         3.30          0         16
sdc              51.40         0.00         3.38          0         16
sdd              52.80         0.00         3.38          0         16
sde               2.80         0.35         0.00          1          0
sdb              47.60         0.00         3.30          0         16
md0            1715.60         0.00         6.68          0         33
sdf              25.40         0.03         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              48.80         0.00         3.34          0         16
sdc              50.60         0.00         3.40          0         17
sdd              53.00         0.00         3.40          0         17
sde               3.00         0.35         0.00          1          0
sdb              49.40         0.00         3.33          0         16
md0            1779.60         0.00         6.93          0         34
sdf              24.80         0.03         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              46.80         0.00         3.27          0         16
sdc              46.40         0.00         3.21          0         16
sdd              47.40         0.00         3.21          0         16
sde               2.80         0.35         0.00          1          0
sdb              48.20         0.00         3.27          0         16
md0            1614.00         0.00         6.28          0         31
sdf              23.20         0.01         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              55.80         0.00         3.60          0         18
sdc              54.00         0.00         3.44          0         17
sdd              53.80         0.00         3.46          0         17
sde               3.20         0.38         0.00          1          0
sdb              56.60         0.00         3.60          0         18
md0            1833.60         0.00         7.14          0         35
sdf              24.20         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              71.00         5.47         3.24         27         16
sdc              72.40         5.47         3.54         27         17
sdd              72.20         5.47         3.53         27         17
sde               2.40         0.30         0.00          1          0
sdb              70.80         5.47         3.24         27         16
md0            1741.60         0.00         6.78          0         33
sdf              19.00         0.00         0.10          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              55.00         0.00         3.86          0         19
sdc              53.80         0.00         3.72          0         18
sdd              54.00         0.00         3.73          0         18
sde               3.00         0.35         0.00          1          0
sdb              55.40         0.00         3.86          0         19
md0            1923.60         0.00         7.49          0         37
sdf              22.00         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              56.00         0.00         4.10          0         20
sdc              56.20         0.00         4.01          0         20
sdd              55.40         0.00         4.01          0         20
sde               2.80         0.35         0.00          1          0
sdb              57.20         0.00         4.10          0         20
md0            2081.80         0.00         8.11          0         40
sdf              16.40         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              49.40         0.00         3.72          0         18
sdc              56.40         0.00         3.87          0         19
sdd              56.00         0.00         3.87          0         19
sde               2.60         0.33         0.00          1          0
sdb              49.40         0.00         3.72          0         18
md0            1973.40         0.00         7.68          0         38
sdf              22.80         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              47.40         0.00         3.68          0         18
sdc              54.20         0.00         3.58          0         17
sdd              54.40         0.00         3.58          0         17
sde               3.20         0.33         0.00          1          0
sdb              48.40         0.00         3.68          0         18
md0            1865.60         0.00         7.26          0         36
sdf              21.40         0.01         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              60.20         0.00         3.91          0         19
sdc              52.40         0.00         3.87          0         19
sdd              51.60         0.00         3.87          0         19
sde               2.60         0.35         0.00          1          0
sdb              60.60         0.00         4.00          0         19
md0            2020.60         0.00         7.87          0         39
sdf              16.80         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              56.80         0.00         3.95          0         19
sdc              58.00         0.00         4.05          0         20
sdd              56.80         0.00         4.05          0         20
sde               3.00         0.35         0.00          1          0
sdb              58.20         0.00         3.87          0         19
md0            2032.40         0.00         7.91          0         39
sdf              21.60         0.01         0.10          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              58.40         4.28         3.57         21         17
sdc              66.60         4.30         3.60         21         18
sdd              65.60         4.30         3.60         21         18
sde               2.80         0.35         0.00          1          0
sdb              58.40         4.28         3.57         21         17
md0            1815.80         0.00         7.07          0         35
sdf              23.20         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              50.20         0.00         3.27          0         16
sdc              48.40         0.00         3.16          0         15
sdd              46.00         0.00         3.16          0         15
sde               2.40         0.30         0.00          1          0
sdb              51.80         0.00         3.27          0         16
md0            1653.20         0.00         6.44          0         32
sdf              26.80         0.00         0.09          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              54.60         0.00         3.45          0         17
sdc              52.20         0.00         3.44          0         17
sdd              53.00         0.00         3.44          0         17
sde               3.00         0.35         0.00          1          0
sdb              54.40         0.00         3.46          0         17
md0            1769.40         0.00         6.89          0         34
sdf              16.80         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              57.09         0.00         3.95          0         19
sdc              57.09         0.00         3.99          0         20
sdd              58.68         0.00         3.99          0         20
sde               2.99         0.37         0.00          1          0
sdb              57.29         0.00         3.95          0         19
md0            2039.32         0.00         7.94          0         39
sdf              20.36         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              51.80         0.00         3.62          0         18
sdc              52.80         0.00         3.70          0         18
sdd              54.60         0.00         3.70          0         18
sde               3.00         0.35         0.00          1          0
sdb              52.00         0.00         3.62          0         18
md0            1880.40         0.00         7.32          0         36
sdf              16.60         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              49.80         0.00         3.17          0         15
sdc              49.60         0.00         3.09          0         15
sdd              47.60         0.00         3.09          0         15
sde               2.80         0.35         0.00          1          0
sdb              49.20         0.00         3.16          0         15
md0            1608.00         0.00         6.26          0         31
sdf              23.20         0.01         0.10          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              59.80         0.00         3.70          0         18
sdc              55.60         0.00         3.58          0         17
sdd              56.40         0.00         3.59          0         17
sde               3.20         0.38         0.00          1          0
sdb              59.20         0.00         3.70          0         18
md0            1892.20         0.00         7.37          0         36
sdf              22.80         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              71.80         3.35         3.52         16         17
sdc              70.00         3.30         3.63         16         18
sdd              68.00         3.30         3.62         16         18
sde               2.60         0.33         0.00          1          0
sdb              70.40         3.35         3.52         16         17
md0            1812.60         0.00         7.06          0         35
sdf              27.00         0.00         0.09          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              47.20         0.00         3.09          0         15
sdc              52.00         0.00         3.19          0         15
sdd              52.80         0.00         3.19          0         15
sde               2.80         0.33         0.00          1          0
sdb              47.40         0.00         3.08          0         15
md0            1663.60         0.00         6.48          0         32
sdf              14.00         0.00         0.04          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              54.20         0.00         3.69          0         18
sdc              50.20         0.00         3.61          0         18
sdd              51.60         0.00         3.62          0         18
sde               2.80         0.35         0.00          1          0
sdb              55.20         0.00         3.69          0         18
md0            1826.60         0.00         7.11          0         35
sdf              26.60         0.00         0.08          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              50.80         0.00         3.60          0         18
sdc              48.60         0.00         3.52          0         17
sdd              49.80         0.00         3.50          0         17
sde               3.00         0.38         0.00          1          0
sdb              53.40         0.00         3.60          0         18
md0            1826.80         0.00         7.11          0         35
sdf              18.00         0.01         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              48.20         0.00         3.49          0         17
sdc              53.40         0.00         3.58          0         17
sdd              55.00         0.00         3.58          0         17
sde               2.80         0.33         0.00          1          0
sdb              49.40         0.00         3.49          0         17
md0            1815.60         0.00         7.07          0         35
sdf              20.80         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              54.60         0.00         3.63          0         18
sdc              57.80         0.00         3.70          0         18
sdd              59.00         0.00         3.70          0         18
sde               3.00         0.38         0.00          1          0
sdb              54.60         0.00         3.64          0         18
md0            1884.60         0.00         7.34          0         36
sdf              26.00         0.00         0.12          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              63.80         3.88         3.18         19         15
sdc              54.80         3.90         2.91         19         14
sdd              53.60         3.90         2.91         19         14
sde               2.60         0.30         0.00          1          0
sdb              65.00         3.88         3.07         19         15
md0            1588.00         0.00         6.18          0         30
sdf              17.80         0.01         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              40.80         0.03         3.01          0         15
sdc              49.40         0.00         3.28          0         16
sdd              51.20         0.00         3.28          0         16
sde               2.40         0.30         0.00          1          0
sdb              41.40         0.03         3.11          0         15
md0            1590.60         0.00         6.19          0         30
sdf              24.00         0.01         0.09          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              59.00         0.00         3.89          0         19
sdc              57.20         0.00         3.74          0         18
sdd              56.60         0.00         3.74          0         18
sde               2.80         0.35         0.00          1          0
sdb              59.00         0.00         3.89          0         19
md0            1983.60         0.00         7.72          0         38
sdf              18.00         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              57.00         0.00         3.70          0         18
sdc              53.00         0.00         3.69          0         18
sdd              51.80         0.00         3.69          0         18
sde               3.00         0.35         0.00          1          0
sdb              57.20         0.00         3.70          0         18
md0            1871.40         0.00         7.29          0         36
sdf              25.60         0.00         0.08          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              54.00         0.00         3.80          0         18
sdc              55.40         0.00         3.88          0         19
sdd              57.00         0.00         3.88          0         19
sde               2.80         0.35         0.00          1          0
sdb              53.80         0.00         3.81          0         19
md0            1973.80         0.00         7.69          0         38
sdf              20.60         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              50.80         0.00         3.61          0         18
sdc              54.80         0.00         3.68          0         18
sdd              54.20         0.00         3.68          0         18
sde               3.00         0.35         0.00          1          0
sdb              50.40         0.00         3.60          0         18
md0            1870.60         0.00         7.28          0         36
sdf              18.00         0.01         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              56.20         0.00         3.59          0         17
sdc              49.40         0.00         3.48          0         17
sdd              49.80         0.00         3.49          0         17
sde               2.60         0.33         0.00          1          0
sdb              57.40         0.00         3.59          0         17
md0            1818.20         0.00         7.08          0         35
sdf              22.40         0.01         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              52.40         4.19         2.70         20         13
sdc              60.00         4.20         2.74         21         13
sdd              58.60         4.20         2.73         21         13
sde               2.20         0.23         0.00          1          0
sdb              51.40         4.19         2.70         20         13
md0            1421.20         0.00         5.53          0         27
sdf              25.80         0.00         0.08          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              57.20         0.01         3.60          0         17
sdc              54.00         0.00         3.60          0         18
sdd              53.60         0.00         3.61          0         18
sde               3.20         0.40         0.00          2          0
sdb              57.40         0.01         3.60          0         17
md0            1825.40         0.00         7.11          0         35
sdf              19.80         0.00         0.10          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              59.40         0.00         4.00          0         19
sdc              55.80         0.00         4.02          0         20
sdd              55.80         0.00         4.01          0         20
sde               2.80         0.35         0.00          1          0
sdb              58.60         0.00         4.00          0         19
md0            2082.60         0.00         8.11          0         40
sdf              26.20         0.00         0.08          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              48.80         0.00         3.37          0         16
sdc              55.40         0.00         3.38          0         16
sdd              54.80         0.00         3.38          0         16
sde               2.80         0.33         0.00          1          0
sdb              48.00         0.00         3.37          0         16
md0            1710.00         0.00         6.66          0         33
sdf              21.60         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              50.40         0.00         3.43          0         17
sdc              53.80         0.00         3.38          0         16
sdd              54.40         0.00         3.38          0         16
sde               2.80         0.35         0.00          1          0
sdb              50.40         0.00         3.43          0         17
md0            1772.20         0.00         6.90          0         34
sdf              16.40         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              54.20         0.00         3.60          0         18
sdc              53.60         0.00         3.51          0         17
sdd              53.00         0.00         3.51          0         17
sde               3.00         0.35         0.00          1          0
sdb              55.60         0.00         3.60          0         18
md0            1826.40         0.00         7.11          0         35
sdf              16.80         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              46.60         0.00         3.13          0         15
sdc              45.20         0.00         3.21          0         16
sdd              46.80         0.00         3.21          0         16
sde               2.60         0.33         0.00          1          0
sdb              48.80         0.00         3.03          0         15
md0            1603.40         0.00         6.24          0         31
sdf              34.00         0.01         0.14          0          0
sdg               0.00         0.00         0.00          0          0


```

I can't see anything specific from hdparm, except the fact I already mentioned, that from 4 identical disks 2 has physical sector size 4096 and 2 has 512...

```

root@KURMIS:/home/jtupulis# hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       WDC WD20EARS-00MVWB0                    
	Serial Number:      WD-WCAZA8102165
	Firmware Revision:  51.0AB51
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors: 3907029168
	Logical  Sector size:                   512 bytes
	Physical Sector size:                  4096 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:     1907729 MBytes
	device size with M = 1000*1000:     2000398 MBytes (2000 GB)
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Power-Up In Standby feature set
	   *	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	NCQ priority information
	    	DMA Setup Auto-Activate optimization
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	380min for SECURITY ERASE UNIT. 380min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee25b4be176
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 25b4be176
Checksum: correct
root@KURMIS:/home/jtupulis# hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
	Model Number:       WDC WD20EARS-00MVWB0                    
	Serial Number:      WD-WCAZA8072325
	Firmware Revision:  51.0AB51
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors: 3907029168
	Logical  Sector size:                   512 bytes
	Physical Sector size:                  4096 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:     1907729 MBytes
	device size with M = 1000*1000:     2000398 MBytes (2000 GB)
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Power-Up In Standby feature set
	   *	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	NCQ priority information
	    	DMA Setup Auto-Activate optimization
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	398min for SECURITY ERASE UNIT. 398min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee2b0a19c57
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 2b0a19c57
Checksum: correct
root@KURMIS:/home/jtupulis# hdparm -I /dev/sdc

/dev/sdc:

ATA device, with non-removable media
	Model Number:       WDC WD20EARS-00MVWB0                    
	Serial Number:      WD-WCAZA7160082
	Firmware Revision:  51.0AB51
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors: 3907029168
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:     1907729 MBytes
	device size with M = 1000*1000:     2000398 MBytes (2000 GB)
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Power-Up In Standby feature set
	   *	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	NCQ priority information
	    	DMA Setup Auto-Activate optimization
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	384min for SECURITY ERASE UNIT. 384min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee205d1db48
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 205d1db48
Checksum: correct
root@KURMIS:/home/jtupulis# hdparm -I /dev/sdd

/dev/sdd:

ATA device, with non-removable media
	Model Number:       WDC WD20EARS-00MVWB0                    
	Serial Number:      WD-WCAZA7114977
	Firmware Revision:  51.0AB51
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors: 3907029168
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:     1907729 MBytes
	device size with M = 1000*1000:     2000398 MBytes (2000 GB)
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Power-Up In Standby feature set
	   *	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	NCQ priority information
	    	DMA Setup Auto-Activate optimization
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	382min for SECURITY ERASE UNIT. 382min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee25b270287
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 25b270287
Checksum: correct


```

No errors logged for all disks from smartctl -l errors /dev/sdX

No self-tests logged for all disks for first time of smartctl -l selftest /dev/sdX

Will post results after tests has ended.

---

### Post by jtupulis on 2011-09-14
I'm starting to get excited about this :) So, my non-expert conclusions:
- enough memory, not swapping in general
- CPU is busy waiting for io
- disks are busy but slow

wtf, a controller issue or what? But controller problem would be stable, shouldn't it?

Ok, after disk smart tests I'll review mounting options, let's see.

---

### Post by jchung on 2011-09-14
Hmm.... yeah. most everything looks good. But, you do have a 'cp' running at the same time as the 'dd'.

Do you know what is being copied by the 'cp' ?

You should test first with only ONE of those running. Only run 'dd' or only run 'cp' for these tests.

Also, you have a resync running. The log you posted previously from Ruby's request seems to indicate there was a resync going on too.

Run the following:

```

# cat /proc/mdstat
# mdadm --detail /dev/md0

```

It looks like you have THREE separate write processes, 'dd', 'cp', and the sync.

Did you let the raid array sync complete before starting the tests?

Joo

---

### Post by rubylaser on 2011-09-14
Yeah, the cp running and the resync make this tests not very accurate.  It looks like your array is still resyncing itself.  It would be nice to re-run this tests after the array is in a clean state, and only running the dd commands.

---

### Post by jtupulis on 2011-09-14
Yeah, resync is active. But, it was active when good array speeds was experienced also. You are right, for clean experiment, cp, dd and resync shouldn't run in parallel. I thought I had killed cp, but obviously not.

Ok, I'll:
* kill cp process anyway
* wait for smart tests to complete
* restart, just to be sure
* let the array to resync
* run dd and all the stats -> post the results
* change mount options -> post the results

---

### Post by jtupulis on 2011-09-14
And the results of what jchung asked for:

```

root@KURMIS:/home/jtupulis# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4] 
md0 : active raid10 sdb1[1] sda1[0] sdd1[3] sdc1[2]
      3907023872 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
      [=>...................]  resync =  6.8% (268578816/3907023872) finish=41859.1min speed=1448K/sec
      
unused devices: <none>
root@KURMIS:/home/jtupulis# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Sep 12 23:30:26 2011
     Raid Level : raid10
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Wed Sep 14 19:58:55 2011
          State : active, resyncing
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2
     Chunk Size : 512K

 Rebuild Status : 6% complete

           Name : KURMIS:0  (local to host KURMIS)
           UUID : 4e3c5b9d:fb3feac3:c476a0ca:a6ce2893
         Events : 5

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1



```

---

### Post by jchung on 2011-09-14
BTW, thats a VERY SLOW sync speed. It will take forever to finish. At that speed, it will take 30 days to finish.

If you want to speed up the array sync, run the following:

```

# echo 400000 > /proc/sys/dev/raid/speed_limit_max

```

Then check /proc/mdstat again to see the new speed and finish ETA.

Joo

---

### Post by rubylaser on 2011-09-14
Yeah, if you can't get that sync speed any higher as a result of increasing the sync_speed_max,  there's a hardware problem somewhere (probably a disk).  You should be able to sync at a minimum of about 40,000K/sec (mine normally goes between 80 and 100,000K/sec).

---

### Post by jtupulis on 2011-09-14
After killing cp and dd, the resync speed is 198922K/sec.

---

### Post by rubylaser on 2011-09-14
That's much better :)  Let the sync finish, then proceed.

---

### Post by jchung on 2011-09-14
> **jtupulis said:**
> After killing cp and dd, the resync speed is 198922K/sec.

Good deal. Thats looking much better.

Array will be resynced in no time. 

Joo

---

### Post by jtupulis on 2011-09-15
Strange thing, after running 
# smartctl --test=long /dev/sdX

there are no results in 
# smartctl -l selftest /dev/sdX

Restarted machine and started smart tests once more.

---

### Post by jchung on 2011-09-15
> **jtupulis said:**
> Strange thing, after running 
# smartctl --test=long /dev/sdX

there are no results in 
# smartctl -l selftest /dev/sdX

Restarted machine and started smart tests once more.

Thats probably ok. As long as there are no errors report. Did you check the error log too?

I take it the resync finished? did you start the 'dd' again?

Joo

---

### Post by jtupulis on 2011-09-15
Which error log, of smart?

Yes resync finished. I'll do dd+stats in evening.

---

### Post by jtupulis on 2011-09-15
# smartctl -l selftest /dev/sdX

shows no errors.

---

### Post by rubylaser on 2011-09-15
You ran that on each of your disks?

```
smartctl -l selftest /dev/sda
smartctl -l selftest /dev/sdb
smartctl -l selftest /dev/sdc
smartctl -l selftest /dev/sdd
```

If so, that's a good thing.

---

### Post by jtupulis on 2011-09-15
dd+stats

```

root@KURMIS:/home/jtupulis# top

top - 18:36:26 up 2 days, 19:02,  5 users,  load average: 3.98, 2.85, 2.51
Tasks: 181 total,   2 running, 179 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  2.5%sy,  0.0%ni, 71.7%id, 23.4%wa,  0.0%hi,  1.1%si,  0.0%st
Mem:   3876612k total,  3818988k used,    57624k free,   451364k buffers
Swap:  4011004k total,      148k used,  4010856k free,  2616340k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
22981 root      20   0 10944 1696  612 D    4  0.0   0:03.81 dd                 
20481 root      20   0     0    0    0 D    2  0.0   0:01.75 kworker/u:2        
  290 root      20   0     0    0    0 S    1  0.0 170:48.13 md0_raid10         
23408 nobody    20   0     0    0    0 D    1  0.0   0:00.02 vsftpd             
23411 root      20   0 36884 1968 1132 S    1  0.1   0:00.02 vsftpd             
    1 root      20   0 24116 1996 1104 S    0  0.1  15:21.78 init               
   34 root      20   0     0    0    0 S    0  0.0   1:39.58 kswapd0            
  393 root      20   0 17052  592  412 S    0  0.0  13:18.91 upstart-udev-br    
  399 root      16  -4 21224  796  372 S    0  0.0   8:25.21 udevd              
  789 root      20   0     0    0    0 D    0  0.0   6:31.76 jbd2/md0-8         
 1353 root      20   0 65916 1772  816 S    0  0.0   6:52.68 winbindd           
 1355 root      20   0 65976 1868  916 S    0  0.0   1:32.05 winbindd           
 1624 root      20   0 65948 1752  768 S    0  0.0   6:51.93 winbindd           
 4522 root      20   0     0    0    0 S    0  0.0   0:05.72 kworker/2:1        
 8864 root      20   0     0    0    0 S    0  0.0   0:03.12 kworker/0:2        


```


```

root@KURMIS:/home/jtupulis# vmstat 5
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1    148  34840 451644 2627936    0    0   257   343   23   30  1  3 78 17
 0  1    148  34140 451644 2627660    0    0    30 12187  793 1612  1  2 73 23
 0  1    148  34964 451684 2628216    0    0    73 13214  826 1631  1  4 72 23
 0  1    148  37260 451712 2625980    0    0    47 13837  817 1606  1  2 74 23
 0  1    148  31816 451692 2631456    0    0     0 13234  815 1587  1  3 73 24
 0  1    148  34964 451688 2628476    0    0     7 11908  778 1614  1  3 73 23
 0  1    148  40364 451712 2623728    0    0     0 14109  843 1650  1  3 73 23
 0  1    148  37916 451696 2626340    0    0     0 12895  778 1566  1  3 73 23
 1  1    148  43128 451800 2620788    0    0    18 13061  812 1623  1  4 72 23
 0  1    148  52272 451768 2612972    0    0     8 12231  810 1641  1  3 73 23
 0  1    148 419768 451772 2252452    0    0     2 13271  814 1592  1  3 73 23
 1  1    148 361708 451804 2309640    0    0     0 11802  766 1586  1  3 73 23
 0  1    148 305796 451804 2366068    0    0     0 11606  769 1537  1  3 73 24
 0  1    148 242324 451808 2429588    0    0     0 13082  767 1548  1  2 73 24
 0  1    148 179900 451808 2490988    0    0     0 12642  801 1587  1  3 73 23
 0  1    148 119772 451812 2551520    0    0     0 12430  809 1577  1  3 73 23
 1  1    148  66604 451816 2604724    0    0     0 10969  771 1546  1  3 73 23
 2  1    148  54212 451556 2617728    0    0     1 12645  802 1568  1  3 73 24
 0  1    148  56792 451364 2616972    0    0     0 13678  827 1652  1  3 72 23
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1    148  57244 451324 2615988    0    0    24 13954  839 1658  1  3 73 23
 0  1    148  58152 450848 2615136    0    0     1 13058  806 1603  1  3 73 23
 0  1    148  57308 450812 2617484    0    0    14 12638  803 1566  1  3 73 23
 0  1    148  56740 450744 2617648    0    0    14 13278  814 1686  1  3 73 23
 0  1    148  53912 450652 2621468    0    0     6 12229  792 1607  1  2 73 24
 0  1    148  52424 450612 2622700    0    0     9 11578  729 1506  1  3 73 23
 0  1    148  53240 450588 2621064    0    0     2 13074  779 1632  1  2 73 24
 0  1    148  52932 450584 2622684    0    0     0 12907  802 1568  1  3 73 23
 0  1    148  66116 450696 2609788    0    0   148 10607  816 2094  4  3 68 25
 1  1    148  50264 450668 2624688    0    0     4 12646  800 1579  1  3 73 23
 0  1    148  49088 450624 2625092    0    0     0 12848  799 1567  1  3 72 23
 0  1    148  48228 450616 2623932    0    0     0 12438  808 1609  1  3 73 24
 0  1    148  48136 450592 2623368    0    0     6 11382  770 1554  1  3 73 24
 0  1    148  45368 450524 2624928    0    0     1 11382  756 1539  1  3 72 23
 1  1    148  43952 450468 2625828    0    0    13 12243  793 1547  1  2 73 24
 0  1    148  73752 450384 2595580    0    0     0 12274  787 1567  1  3 72 24
 1  1    148  46412 450348 2622120    0    0     5 12649  801 1659  1  2 70 26
 0  1    148  43616 450388 2623972    0    0    13 12018  784 1567  1  3 73 23
 0  1    148  43848 450152 2635940    0    0     3 11601  779 1567  1  3 72 23
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1    148  35256 450064 2645760    0    0     0 12641  795 1598  1  2 73 24
 0  1    148  32368 450036 2645432    0    0    32 12426  792 1580  1  3 73 23
 0  1    148  37492 449940 2641416    0    0     6 11814  787 1572  1  3 73 23
 0  1    148  34868 427072 2667276    0    0     4 13311  829 1648  1  3 73 23



```

```

root@KURMIS:/home/jtupulis# sar -P ALL 5
Linux 2.6.38-11-server (KURMIS) 	09/15/2011 	_x86_64_	(4 CPU)

06:35:05 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:35:10 PM     all      1.05      0.00      2.50     23.56      0.00     72.89
06:35:10 PM       0      1.60      0.00      4.60     80.00      0.00     13.80
06:35:10 PM       1      0.60      0.00      0.60      0.00      0.00     98.80
06:35:10 PM       2      0.20      0.00      2.98     14.29      0.00     82.54
06:35:10 PM       3      1.80      0.00      1.80      0.00      0.00     96.40

06:35:10 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:35:15 PM     all      0.85      0.00      2.54     23.41      0.00     73.21
06:35:15 PM       0      0.40      0.00      4.80     89.60      0.00      5.20
06:35:15 PM       1      0.80      0.00      0.40      0.00      0.00     98.81
06:35:15 PM       2      0.20      0.00      3.17      4.16      0.00     92.48
06:35:15 PM       3      2.00      0.00      1.80      0.20      0.00     96.00

06:35:15 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:35:20 PM     all      0.90      0.00      3.14     23.36      0.00     72.61
06:35:20 PM       0      0.40      0.00      6.57     89.64      0.00      3.39
06:35:20 PM       1      0.00      0.00      0.60      0.00      0.00     99.40
06:35:20 PM       2      0.20      0.00      3.58      3.78      0.00     92.45
06:35:20 PM       3      2.99      0.00      1.79      0.00      0.00     95.22

06:35:20 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:35:25 PM     all      1.05      0.00      2.69     23.13      0.00     73.13
06:35:25 PM       0      1.00      0.00      5.60     83.60      0.00      9.80
06:35:25 PM       1      1.00      0.00      0.20      0.00      0.00     98.80
06:35:25 PM       2      0.20      0.00      3.75      9.09      0.00     86.96
06:35:25 PM       3      2.00      0.00      1.20      0.00      0.00     96.80

06:35:25 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:35:30 PM     all      1.20      0.00      2.36     23.93      0.00     72.50
06:35:30 PM       0      0.20      0.00      4.19     90.02      0.00      5.59
06:35:30 PM       1      0.62      0.00      1.03      0.00      0.00     98.36
06:35:30 PM       2      0.40      0.00      2.97      5.15      0.00     91.49
06:35:30 PM       3      3.60      0.00      1.20      0.00      0.00     95.20

06:35:30 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:35:35 PM     all      0.89      0.00      3.27     22.77      0.00     73.07
06:35:35 PM       0      0.40      0.00      6.79     83.43      0.00      9.38
06:35:35 PM       1      0.58      0.00      0.19      0.00      0.00     99.22
06:35:35 PM       2      0.60      0.00      4.38      8.37      0.00     86.65
06:35:35 PM       3      1.99      0.00      1.79      0.00      0.00     96.22

06:35:35 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:35:40 PM     all      1.25      0.00      3.30     22.94      0.00     72.51
06:35:40 PM       0      1.40      0.00      6.00     88.20      0.00      4.40
06:35:40 PM       1      0.00      0.00      1.00      0.00      0.00     99.00
06:35:40 PM       2      1.00      0.00      4.39      3.59      0.00     91.02
06:35:40 PM       3      2.60      0.00      1.80      0.00      0.00     95.60

06:35:40 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:35:45 PM     all      1.25      0.00      3.30     23.23      0.00     72.23
06:35:45 PM       0      1.00      0.00      5.20     87.40      0.00      6.40
06:35:45 PM       1      0.00      0.00      0.60      0.00      0.00     99.40
06:35:45 PM       2      0.20      0.00      5.53      5.53      0.00     88.74
06:35:45 PM       3      3.81      0.00      1.80      0.00      0.00     94.39

06:35:45 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:35:50 PM     all      0.80      0.00      2.99     22.89      0.00     73.33
06:35:50 PM       0      0.40      0.00      7.00     87.80      0.00      4.80
06:35:50 PM       1      0.79      0.00      0.59      0.00      0.00     98.61
06:35:50 PM       2      0.00      0.00      3.78      4.17      0.00     92.05
06:35:50 PM       3      1.99      0.00      0.60      0.00      0.00     97.41

06:35:50 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:35:55 PM     all      0.95      0.00      2.69     23.48      0.00     72.88
06:35:55 PM       0      0.20      0.00      5.19     90.82      0.00      3.79
06:35:55 PM       1      0.80      0.00      0.40      0.00      0.00     98.80
06:35:55 PM       2      0.20      0.00      3.57      3.17      0.00     93.06
06:35:55 PM       3      2.60      0.00      1.60      0.00      0.00     95.80

06:35:55 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:00 PM     all      0.95      0.00      2.75     23.29      0.00     73.01
06:36:00 PM       0      0.20      0.00      4.99     87.82      0.00      6.99
06:36:00 PM       1      1.80      0.00      0.20      0.00      0.00     98.00
06:36:00 PM       2      0.20      0.00      5.20      5.20      0.00     89.40
06:36:00 PM       3      1.60      0.00      0.60      0.00      0.00     97.80

06:36:00 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:05 PM     all      0.65      0.05      2.50     23.50      0.00     73.30
06:36:05 PM       0      0.00      0.00      4.60     88.60      0.00      6.80
06:36:05 PM       1      0.80      0.00      0.80      0.20      0.00     98.20
06:36:05 PM       2      0.20      0.20      3.78      5.37      0.00     90.46
06:36:05 PM       3      1.60      0.00      0.80      0.00      0.00     97.60

06:36:05 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:10 PM     all      1.00      0.00      3.34     23.16      0.00     72.51
06:36:10 PM       0      0.00      0.00      6.57     89.64      0.00      3.78
06:36:10 PM       1      1.20      0.00      0.80      0.00      0.00     98.00
06:36:10 PM       2      0.60      0.00      4.17      2.98      0.00     92.26
06:36:10 PM       3      2.20      0.00      1.80      0.00      0.00     96.01

06:36:10 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:15 PM     all      1.05      0.00      2.74     23.55      0.00     72.65
06:36:15 PM       0      0.00      0.00      4.80     88.40      0.00      6.80
06:36:15 PM       1      1.20      0.00      1.00      0.00      0.00     97.80
06:36:15 PM       2      0.00      0.00      3.58      5.96      0.00     90.46
06:36:15 PM       3      3.00      0.00      1.60      0.00      0.00     95.40

06:36:15 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:20 PM     all      0.95      0.00      2.50     23.70      0.00     72.85
06:36:20 PM       0      0.80      0.00      3.80     92.40      0.00      3.00
06:36:20 PM       1      0.20      0.00      0.80      0.00      0.00     99.00
06:36:20 PM       2      0.20      0.00      3.17      2.57      0.00     94.06
06:36:20 PM       3      2.60      0.00      2.20      0.00      0.00     95.20

06:36:20 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:25 PM     all      1.25      0.00      3.29     23.17      0.00     72.30
06:36:25 PM       0      0.40      0.00      5.20     85.60      0.00      8.80
06:36:25 PM       1      1.00      0.00      0.80      0.00      0.00     98.21
06:36:25 PM       2      0.40      0.00      5.15      7.33      0.00     87.13
06:36:25 PM       3      3.20      0.00      2.00      0.00      0.00     94.80

06:36:25 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:30 PM     all      1.05      0.05      3.69     23.12      0.00     72.10
06:36:30 PM       0      0.20      0.00      7.20     85.40      0.00      7.20
06:36:30 PM       1      1.40      0.00      0.40      0.00      0.00     98.20
06:36:30 PM       2      0.40      0.20      4.76      7.34      0.00     87.30
06:36:30 PM       3      2.19      0.00      2.39      0.00      0.00     95.43

06:36:30 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:35 PM     all      0.85      0.00      2.84     23.35      0.00     72.95
06:36:35 PM       0      0.20      0.00      4.59     91.42      0.00      3.79
06:36:35 PM       1      0.80      0.00      0.60      0.00      0.00     98.60
06:36:35 PM       2      0.40      0.00      4.18      1.99      0.00     93.43
06:36:35 PM       3      2.00      0.00      2.00      0.00      0.00     96.01

06:36:35 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:40 PM     all      0.95      0.00      3.15     22.88      0.00     73.03
06:36:40 PM       0      0.60      0.00      7.00     89.60      0.00      2.80
06:36:40 PM       1      0.00      0.00      0.80      0.00      0.00     99.20
06:36:40 PM       2      0.40      0.00      3.59      1.80      0.00     94.21
06:36:40 PM       3      2.79      0.00      1.20      0.20      0.00     95.81

06:36:40 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:45 PM     all      1.10      0.00      3.20     22.98      0.00     72.71
06:36:45 PM       0      0.80      0.00      7.00     87.80      0.00      4.40
06:36:45 PM       1      1.21      0.00      1.01      0.00      0.00     97.78
06:36:45 PM       2      0.40      0.00      3.39      3.98      0.00     92.23
06:36:45 PM       3      2.00      0.00      1.40      0.00      0.00     96.60

06:36:45 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:50 PM     all      0.94      0.00      2.43     23.29      0.00     73.34
06:36:50 PM       0      1.80      0.00      5.19     90.02      0.00      2.99
06:36:50 PM       1      0.59      0.00      0.40      0.00      0.00     99.01
06:36:50 PM       2      0.79      0.00      2.96      3.56      0.00     92.69
06:36:50 PM       3      0.60      0.00      1.20      0.00      0.00     98.21

06:36:50 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:36:55 PM     all      1.10      0.00      2.45     23.51      0.00     72.94
06:36:55 PM       0      1.00      0.00      4.00     89.00      0.00      6.00
06:36:55 PM       1      1.20      0.00      0.80      0.00      0.00     98.00
06:36:55 PM       2      0.20      0.00      3.98      5.18      0.00     90.64
06:36:55 PM       3      2.00      0.00      1.00      0.00      0.00     97.00

06:36:55 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:00 PM     all      1.05      0.05      2.15     23.60      0.00     73.15
06:37:00 PM       0      0.60      0.00      3.81     85.17      0.00     10.42
06:37:00 PM       1      0.60      0.00      0.60      0.00      0.00     98.80
06:37:00 PM       2      0.40      0.20      3.00      9.40      0.00     87.00
06:37:00 PM       3      2.60      0.00      1.20      0.00      0.00     96.20

06:37:00 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:05 PM     all      0.70      0.00      2.89     23.49      0.00     72.92
06:37:05 PM       0      0.40      0.00      4.99     90.42      0.00      4.19
06:37:05 PM       1      0.60      0.00      1.20      0.00      0.00     98.20
06:37:05 PM       2      0.20      0.00      3.56      3.75      0.00     92.49
06:37:05 PM       3      1.60      0.00      1.80      0.00      0.00     96.61

06:37:05 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:10 PM     all      3.44      0.00      3.64     25.29      0.00     67.63
06:37:10 PM       0      6.20      0.00      5.80     65.60      0.00     22.40
06:37:10 PM       1      1.39      0.00      1.79      1.20      0.00     95.62
06:37:10 PM       2      2.58      0.00      3.58     26.24      0.00     67.59
06:37:10 PM       3      3.60      0.00      3.40      8.20      0.00     84.80

06:37:10 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:15 PM     all      1.34      0.00      2.94     23.21      0.00     72.51
06:37:15 PM       0      2.20      0.00      5.59     86.83      0.00      5.39
06:37:15 PM       1      1.20      0.00      1.60      0.00      0.00     97.20
06:37:15 PM       2      0.40      0.00      3.95      6.13      0.00     89.53
06:37:15 PM       3      1.60      0.00      0.60      0.00      0.00     97.80

06:37:15 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:20 PM     all      1.20      0.00      3.19     22.98      0.00     72.63
06:37:20 PM       0      0.40      0.00      6.79     90.02      0.00      2.79
06:37:20 PM       1      2.59      0.00      0.40      0.00      0.00     97.01
06:37:20 PM       2      0.20      0.00      4.17      1.99      0.00     93.64
06:37:20 PM       3      1.60      0.00      1.40      0.00      0.00     97.01

06:37:20 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:25 PM     all      1.30      0.00      3.19     23.39      0.00     72.12
06:37:25 PM       0      1.20      0.00      5.00     87.00      0.00      6.80
06:37:25 PM       1      1.40      0.00      1.60      0.00      0.00     97.01
06:37:25 PM       2      0.20      0.00      4.17      6.75      0.00     88.89
06:37:25 PM       3      2.40      0.00      2.00      0.00      0.00     95.60

06:37:25 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:30 PM     all      0.90      0.00      2.34     23.72      0.00     73.04
06:37:30 PM       0      0.40      0.00      3.61     90.18      0.00      5.81
06:37:30 PM       1      0.80      0.00      0.20      1.20      0.00     97.80
06:37:30 PM       2      0.20      0.00      3.15      3.94      0.00     92.72
06:37:30 PM       3      2.20      0.00      2.40      0.00      0.00     95.40

06:37:30 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:35 PM     all      1.00      0.00      3.23     23.23      0.00     72.54
06:37:35 PM       0      0.40      0.00      5.17     90.46      0.00      3.98
06:37:35 PM       1      1.00      0.00      1.20      0.00      0.00     97.80
06:37:35 PM       2      0.00      0.00      4.14      2.17      0.00     93.69
06:37:35 PM       3      2.60      0.00      2.40      0.20      0.00     94.80

06:37:35 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:40 PM     all      0.95      0.05      2.76     23.66      0.00     72.58
06:37:40 PM       0      0.20      0.20      4.80     91.20      0.00      3.60
06:37:40 PM       1      1.21      0.00      0.00      0.00      0.00     98.79
06:37:40 PM       2      0.00      0.00      4.00      3.00      0.00     93.00
06:37:40 PM       3      2.41      0.00      2.21      0.00      0.00     95.37

06:37:40 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:45 PM     all      1.24      0.05      2.49     23.56      0.00     72.66
06:37:45 PM       0      0.20      0.00      4.40     86.60      0.00      8.80
06:37:45 PM       1      0.99      0.00      0.20      0.00      0.00     98.82
06:37:45 PM       2      0.40      0.20      3.98      8.17      0.00     87.25
06:37:45 PM       3      3.38      0.00      1.39      0.00      0.00     95.23

06:37:45 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:50 PM     all      1.25      0.00      2.35     25.96      0.00     70.44
06:37:50 PM       0      0.00      0.00      4.40     90.80      0.00      4.80
06:37:50 PM       1      1.60      0.00      0.80      0.00      0.00     97.60
06:37:50 PM       2      0.00      0.00      2.39     13.12      0.00     84.49
06:37:50 PM       3      3.41      0.00      1.80      0.00      0.00     94.79

06:37:50 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:37:55 PM     all      0.90      0.00      2.60     23.56      0.00     72.94
06:37:55 PM       0      0.60      0.00      5.20     89.20      0.00      5.00
06:37:55 PM       1      1.20      0.00      0.60      0.00      0.00     98.20
06:37:55 PM       2      0.20      0.00      3.19      5.18      0.00     91.43
06:37:55 PM       3      1.60      0.00      1.40      0.00      0.00     97.01

06:37:55 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:00 PM     all      1.20      0.05      3.04     23.30      0.00     72.41
06:38:00 PM       0      0.60      0.00      5.60     88.20      0.00      5.60
06:38:00 PM       1      0.20      0.20      0.60      0.00      0.00     99.01
06:38:00 PM       2      0.40      0.00      4.60      5.00      0.00     90.00
06:38:00 PM       3      3.59      0.00      1.40      0.20      0.00     94.81

06:38:00 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:05 PM     all      1.35      0.00      2.55     23.39      0.00     72.71
06:38:05 PM       0      1.00      0.00      4.00     91.00      0.00      4.00
06:38:05 PM       1      2.20      0.00      1.00      0.00      0.00     96.80
06:38:05 PM       2      0.60      0.00      4.19      2.59      0.00     92.61
06:38:05 PM       3      1.60      0.00      1.00      0.00      0.00     97.40

06:38:05 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:10 PM     all      0.55      0.00      2.44     23.58      0.00     73.43
06:38:10 PM       0      0.20      0.00      3.79     86.83      0.00      9.18
06:38:10 PM       1      0.80      0.00      0.80      0.00      0.00     98.40
06:38:10 PM       2      0.00      0.00      3.95      5.93      0.00     90.12
06:38:10 PM       3      1.20      0.00      1.20      1.60      0.00     96.00

06:38:10 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:15 PM     all      0.90      0.05      2.64     23.42      0.00     72.99
06:38:15 PM       0      0.60      0.00      4.99     88.62      0.00      5.79
06:38:15 PM       1      1.20      0.20      0.80      0.00      0.00     97.81
06:38:15 PM       2      0.20      0.00      3.37      5.16      0.00     91.27
06:38:15 PM       3      1.60      0.00      1.40      0.00      0.00     97.00

06:38:15 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:20 PM     all      1.10      0.00      2.64     23.33      0.00     72.93
06:38:20 PM       0      1.00      0.00      4.39     88.42      0.00      6.19
06:38:20 PM       1      0.80      0.00      0.20      0.00      0.00     99.00
06:38:20 PM       2      0.40      0.00      3.78      4.97      0.00     90.85
06:38:20 PM       3      2.20      0.00      2.20      0.00      0.00     95.61

06:38:20 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:25 PM     all      0.90      0.10      3.64     22.83      0.00     72.53
06:38:25 PM       0      0.20      0.00      7.20     87.80      0.00      4.80
06:38:25 PM       1      1.39      0.40      0.60      0.00      0.00     97.61
06:38:25 PM       2      0.00      0.00      4.57      3.78      0.00     91.65
06:38:25 PM       3      2.00      0.00      2.20      0.00      0.00     95.81

06:38:25 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:30 PM     all      0.80      0.00      2.75     23.51      0.00     72.94
06:38:30 PM       0      0.20      0.00      5.40     91.00      0.00      3.40
06:38:30 PM       1      0.40      0.00      0.00      0.00      0.00     99.60
06:38:30 PM       2      0.00      0.00      3.39      3.19      0.00     93.43
06:38:30 PM       3      2.59      0.00      2.20      0.00      0.00     95.21

06:38:30 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:35 PM     all      0.70      0.00      2.50     23.70      0.00     73.10
06:38:35 PM       0      0.20      0.00      4.19     91.02      0.00      4.59
06:38:35 PM       1      1.00      0.00      0.40      0.00      0.00     98.60
06:38:35 PM       2      0.20      0.00      3.94      3.55      0.00     92.31
06:38:35 PM       3      1.42      0.00      1.42      0.00      0.00     97.16

06:38:35 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:40 PM     all      0.75      0.00      2.80     23.63      0.00     72.83
06:38:40 PM       0      0.40      0.00      4.99     91.02      0.00      3.59
06:38:40 PM       1      0.40      0.00      0.60      0.00      0.00     99.01
06:38:40 PM       2      0.00      0.00      3.59      3.39      0.00     93.03
06:38:40 PM       3      2.22      0.00      2.02      0.00      0.00     95.77

06:38:40 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:45 PM     all      1.04      0.00      3.18     22.96      0.00     72.81
06:38:45 PM       0      1.60      0.00      6.00     86.40      0.00      6.00
06:38:45 PM       1      0.40      0.00      0.80      0.00      0.00     98.80
06:38:45 PM       2      0.20      0.00      4.19      5.99      0.00     89.62
06:38:45 PM       3      1.96      0.00      1.76      0.00      0.00     96.28

06:38:45 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:50 PM     all      0.75      0.00      2.55     23.56      0.00     73.14
06:38:50 PM       0      0.80      0.00      4.80     90.40      0.00      4.00
06:38:50 PM       1      0.20      0.00      1.00      0.00      0.00     98.80
06:38:50 PM       2      0.20      0.00      2.98      3.98      0.00     92.84
06:38:50 PM       3      1.80      0.00      1.40      0.00      0.00     96.80

06:38:50 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:38:55 PM     all      1.25      0.00      3.04     22.95      0.00     72.75
06:38:55 PM       0      1.80      0.00      5.60     85.60      0.00      7.00
06:38:55 PM       1      0.60      0.00      0.80      0.00      0.00     98.60
06:38:55 PM       2      0.40      0.00      4.37      6.35      0.00     88.89
06:38:55 PM       3      2.20      0.00      1.40      0.00      0.00     96.40

06:38:55 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:39:00 PM     all      1.20      0.00      2.99     23.33      0.00     72.48
06:39:00 PM       0      0.60      0.00      5.19     90.22      0.00      3.99
06:39:00 PM       1      1.40      0.00      1.20      0.00      0.00     97.40
06:39:00 PM       2      0.99      0.00      4.55      3.17      0.00     91.29
06:39:00 PM       3      1.80      0.00      1.00      0.00      0.00     97.20

06:39:00 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:39:05 PM     all      0.95      0.00      2.46     25.39      0.00     71.20
06:39:05 PM       0      1.00      0.00      4.60     87.60      0.00      6.80
06:39:05 PM       1      0.82      0.00      0.20      0.00      0.00     98.98
06:39:05 PM       2      0.20      0.00      3.78     13.32      0.00     82.70
06:39:05 PM       3      1.80      0.00      1.20      0.20      0.00     96.80

06:39:05 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:39:10 PM     all      0.95      0.05      3.33     22.90      0.00     72.77
06:39:10 PM       0      1.20      0.20      5.00     87.20      0.00      6.40
06:39:10 PM       1      1.18      0.00      1.18      0.00      0.00     97.63
06:39:10 PM       2      0.40      0.00      5.18      4.78      0.00     89.64
06:39:10 PM       3      1.00      0.00      2.00      0.00      0.00     97.00

06:39:10 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:39:15 PM     all      0.80      0.00      2.84     23.54      0.00     72.82
06:39:15 PM       0      0.20      0.00      6.00     89.40      0.00      4.40
06:39:15 PM       1      0.00      0.00      0.40      0.00      0.00     99.60
06:39:15 PM       2      0.40      0.00      3.59      4.98      0.00     91.04
06:39:15 PM       3      2.60      0.00      1.40      0.00      0.00     96.00

06:39:15 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:39:20 PM     all      0.85      0.00      2.55     23.54      0.00     73.06
06:39:20 PM       0      0.60      0.00      4.60     84.60      0.00     10.20
06:39:20 PM       1      1.00      0.00      0.40      0.00      0.00     98.61
06:39:20 PM       2      0.00      0.00      3.78      9.56      0.00     86.65
06:39:20 PM       3      1.81      0.00      1.41      0.00      0.00     96.78

06:39:20 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:39:25 PM     all      1.10      0.00      2.89     23.22      0.00     72.80
06:39:25 PM       0      0.40      0.00      6.40     89.20      0.00      4.00
06:39:25 PM       1      1.60      0.00      0.00      0.00      0.00     98.40
06:39:25 PM       2      0.40      0.00      3.78      3.98      0.00     91.85
06:39:25 PM       3      1.98      0.00      1.39      0.00      0.00     96.63

06:39:25 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:39:30 PM     all      0.80      0.00      2.99     23.33      0.00     72.88
06:39:30 PM       0      0.80      0.00      5.20     89.40      0.00      4.60
06:39:30 PM       1      0.60      0.00      0.80      0.00      0.00     98.60
06:39:30 PM       2      0.40      0.00      4.74      4.15      0.00     90.71
06:39:30 PM       3      1.40      0.00      1.20      0.00      0.00     97.40

06:39:30 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
06:39:35 PM     all      1.04      0.00      3.18     23.02      0.00     72.75
06:39:35 PM       0      0.60      0.00      6.39     85.03      0.00      7.98
06:39:35 PM       1      1.80      0.00      0.20      0.00      0.00     98.00
06:39:35 PM       2      0.59      0.00      5.29      7.25      0.00     86.86
06:39:35 PM       3      1.20      0.00      0.80      0.00      0.00     98.00



```

iostat
```

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              66.60         0.00         5.24          0         26
sdc              57.80         0.00         5.20          0         26
sdd              49.80         0.00         5.20          0         26
sde               0.00         0.00         0.00          0          0
sdb              56.20         0.00         5.24          0         26
md0            2672.60         0.00        10.44          0         52
sdf              20.60         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              72.40         0.00         5.91          0         29
sdc              74.80         0.00         5.97          0         29
sdd              64.80         0.00         5.97          0         29
sde               0.00         0.00         0.00          0          0
sdb              61.00         0.00         5.91          0         29
md0            3039.80         0.00        11.87          0         59
sdf              26.80         0.01         0.08          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              77.00         0.00         5.94          0         29
sdc              69.20         0.00         5.93          0         29
sdd              59.00         0.00         5.93          0         29
sde               0.00         0.00         0.00          0          0
sdb              64.80         0.00         5.94          0         29
md0            3039.20         0.00        11.87          0         59
sdf              21.80         0.00         0.11          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              76.80         0.00         5.96          0         29
sdc              66.40         0.00         5.91          0         29
sdd              57.40         0.00         5.91          0         29
sde               0.00         0.00         0.00          0          0
sdb              66.60         0.00         5.96          0         29
md0            3039.20         0.00        11.87          0         59
sdf              22.80         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              68.40         0.00         5.80          0         29
sdc              75.20         0.00         5.87          0         29
sdd              63.80         0.00         5.87          0         29
sde               0.00         0.00         0.00          0          0
sdb              58.00         0.00         5.80          0         29
md0            2986.80         0.00        11.67          0         58
sdf              22.60         0.01         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              75.20         0.00         5.85          0         29
sdc              68.20         0.00         5.82          0         29
sdd              58.60         0.00         5.82          0         29
sde               0.00         0.00         0.00          0          0
sdb              64.60         0.00         5.85          0         29
md0            2986.80         0.00        11.67          0         58
sdf              22.80         0.01         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              75.60         0.00         6.15          0         30
sdc              69.80         0.00         6.13          0         30
sdd              60.60         0.00         6.13          0         30
sde               0.00         0.00         0.00          0          0
sdb              65.40         0.00         6.15          0         30
md0            3144.00         0.00        12.28          0         61
sdf              22.40         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              68.60         0.00         5.90          0         29
sdc              73.80         0.00         5.97          0         29
sdd              63.60         0.00         5.97          0         29
sde               0.00         0.00         0.00          0          0
sdb              59.60         0.00         5.90          0         29
md0            3039.20         0.00        11.87          0         59
sdf              25.60         0.03         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              80.40         0.00         5.97          0         29
sdc              64.60         0.00         5.90          0         29
sdd              57.60         0.00         5.90          0         29
sde               0.00         0.00         0.00          0          0
sdb              67.80         0.00         5.97          0         29
md0            3039.80         0.00        11.87          0         59
sdf              23.60         0.01         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              77.20         0.00         6.13          0         30
sdc              74.40         0.00         6.15          0         30
sdd              65.80         0.00         6.15          0         30
sde               0.00         0.00         0.00          0          0
sdb              67.20         0.00         6.13          0         30
md0            3144.00         0.00        12.28          0         61
sdf              21.60         0.00         0.10          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              77.40         0.00         6.24          0         31
sdc              73.00         0.00         6.25          0         31
sdd              64.40         0.00         6.25          0         31
sde               0.00         0.00         0.00          0          0
sdb              66.40         0.00         6.24          0         31
md0            3196.40         0.00        12.49          0         62
sdf              21.00         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              79.20         0.00         5.86          0         29
sdc              63.40         0.00         5.81          0         29
sdd              57.00         0.00         5.81          0         29
sde               0.00         0.00         0.00          0          0
sdb              67.80         0.00         5.86          0         29
md0            2987.00         0.00        11.67          0         58
sdf              20.40         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              68.60         0.00         5.70          0         28
sdc              71.60         0.00         5.76          0         28
sdd              63.60         0.00         5.76          0         28
sde               0.00         0.00         0.00          0          0
sdb              59.00         0.00         5.70          0         28
md0            2934.40         0.00        11.46          0         57
sdf              22.60         0.01         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              75.00         0.00         6.04          0         30
sdc              69.00         0.00         6.03          0         30
sdd              59.20         0.00         6.03          0         30
sde               0.00         0.00         0.00          0          0
sdb              64.80         0.00         6.04          0         30
md0            3091.60         0.00        12.08          0         60
sdf              22.80         0.01         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              77.60         0.00         6.06          0         30
sdc              67.00         0.00         6.02          0         30
sdd              57.20         0.00         6.02          0         30
sde               0.00         0.00         0.00          0          0
sdb              66.80         0.00         6.06          0         30
md0            3091.60         0.00        12.08          0         60
sdf              27.20         0.04         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              69.80         0.00         5.92          0         29
sdc              73.80         0.00         6.07          0         30
sdd              64.80         0.00         6.07          0         30
sde               0.00         0.00         0.00          0          0
sdb              60.60         0.00         5.98          0         29
md0            3091.00         0.00        12.07          0         60
sdf              23.60         0.00         0.11          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              86.20         0.00         6.68          0         33
sdc              69.60         0.00         6.51          0         32
sdd              60.20         0.00         6.51          0         32
sde               0.00         0.00         0.00          0          0
sdb              74.60         0.00         6.62          0         33
md0            3354.80         0.00        13.10          0         65
sdf              27.80         0.06         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              71.00         0.00         6.20          0         31
sdc              77.80         0.00         6.28          0         31
sdd              68.20         0.00         6.28          0         31
sde               0.00         0.00         0.00          0          0
sdb              60.40         0.00         6.20          0         31
md0            3196.40         0.00        12.49          0         62
sdf              22.40         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              75.20         0.00         6.16          0         30
sdc              66.00         0.00         6.12          0         30
sdd              58.40         0.00         6.12          0         30
sde               0.00         0.00         0.00          0          0
sdb              62.60         0.00         6.16          0         30
md0            3144.00         0.00        12.28          0         61
sdf              31.80         0.41         0.06          2          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              68.00         0.00         6.04          0         30
sdc              66.00         0.00         6.04          0         30
sdd              58.60         0.00         6.04          0         30
sde               0.00         0.00         0.00          0          0
sdb              57.40         0.00         6.04          0         30
md0            3091.60         0.00        12.08          0         60
sdf              20.00         0.01         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              72.40         0.00         6.12          0         30
sdc              73.80         0.00         6.16          0         30
sdd              64.40         0.00         6.16          0         30
sde               0.00         0.00         0.00          0          0
sdb              62.80         0.00         6.12          0         30
md0            3144.00         0.00        12.28          0         61
sdf              17.40         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              72.20         0.00         5.55          0         27
sdc              58.80         0.00         5.50          0         27
sdd              52.40         0.00         5.50          0         27
sde               0.00         0.00         0.00          0          0
sdb              62.80         0.00         5.55          0         27
md0            2829.60         0.00        11.05          0         55
sdf              19.80         0.01         0.09          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              72.60         0.00         5.83          0         29
sdc              70.00         0.00         5.84          0         29
sdd              60.40         0.00         5.84          0         29
sde               0.00         0.00         0.00          0          0
sdb              61.80         0.00         5.83          0         29
md0            2987.60         0.00        11.67          0         58
sdf              25.80         0.01         0.08          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              72.40         0.00         6.02          0         30
sdc              72.40         0.00         6.06          0         30
sdd              63.40         0.00         6.06          0         30
sde               0.00         0.00         0.00          0          0
sdb              61.80         0.00         6.02          0         30
md0            3091.60         0.00        12.08          0         60
sdf              20.60         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              86.40         0.00         6.48          0         32
sdc              68.60         0.00         6.41          0         32
sdd              60.20         0.00         6.41          0         32
sde               0.00         0.00         0.00          0          0
sdb              73.80         0.00         6.48          0         32
md0            3301.20         0.00        12.90          0         64
sdf              20.60         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              70.60         0.00         6.00          0         30
sdc              76.00         0.00         6.08          0         30
sdd              67.00         0.00         6.08          0         30
sde               0.00         0.00         0.00          0          0
sdb              61.80         0.00         6.00          0         30
md0            3091.60         0.00        12.08          0         60
sdf              21.00         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              73.80         0.00         5.96          0         29
sdc              64.80         0.00         5.91          0         29
sdd              57.00         0.00         5.91          0         29
sde               0.00         0.00         0.00          0          0
sdb              62.80         0.00         5.96          0         29
md0            3039.20         0.00        11.87          0         59
sdf              16.40         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              79.20         0.00         6.44          0         32
sdc              76.60         0.00         6.46          0         32
sdd              66.60         0.00         6.46          0         32
sde               0.00         0.00         0.00          0          0
sdb              69.60         0.00         6.44          0         32
md0            3301.20         0.00        12.90          0         64
sdf              22.60         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              74.60         0.00         6.03          0         30
sdc              67.40         0.00         6.04          0         30
sdd              60.20         0.00         6.04          0         30
sde               0.00         0.00         0.00          0          0
sdb              64.00         0.00         6.03          0         30
md0            3091.60         0.00        12.08          0         60
sdf              25.40         0.04         0.11          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              81.60         0.00         6.07          0         30
sdc              66.60         0.00         6.01          0         30
sdd              58.00         0.00         6.01          0         30
sde               0.00         0.00         0.00          0          0
sdb              69.40         0.00         6.07          0         30
md0            3092.20         0.00        12.08          0         60
sdf              24.80         0.00         0.08          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              71.80         0.00         6.00          0         30
sdc              74.80         0.00         6.08          0         30
sdd              67.00         0.00         6.08          0         30
sde               0.00         0.00         0.00          0          0
sdb              60.80         0.00         6.00          0         30
md0            3091.60         0.00        12.08          0         60
sdf              16.00         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              84.60         0.00         6.27          0         31
sdc              69.00         0.00         6.21          0         31
sdd              59.80         0.00         6.21          0         31
sde               0.00         0.00         0.00          0          0
sdb              71.20         0.00         6.27          0         31
md0            3196.40         0.00        12.49          0         62
sdf              20.20         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              69.00         0.00         5.53          0         27
sdc              64.00         0.00         5.53          0         27
sdd              56.00         0.00         5.53          0         27
sde               0.00         0.00         0.00          0          0
sdb              59.20         0.00         5.53          0         27
md0            2829.60         0.00        11.05          0         55
sdf              20.80         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              67.60         0.00         5.92          0         29
sdc              73.40         0.00         6.02          0         30
sdd              65.20         0.00         5.98          0         29
sde               0.00         0.00         0.00          0          0
sdb              58.60         0.00         5.95          0         29
md0            3090.60         0.00        12.07          0         60
sdf              20.20         0.02         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              85.20         0.00         6.37          0         31
sdc              67.80         0.00         6.26          0         31
sdd              58.40         0.00         6.29          0         31
sde               0.00         0.00         0.00          0          0
sdb              73.00         0.00         6.34          0         31
md0            3197.60         0.00        12.49          0         62
sdf              19.80         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              67.00         0.00         5.59          0         27
sdc              66.40         0.00         5.64          0         28
sdd              58.00         0.00         5.64          0         28
sde               0.00         0.00         0.00          0          0
sdb              57.80         0.00         5.55          0         27
md0            2880.80         0.00        11.25          0         56
sdf              22.60         0.03         0.10          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              74.20         0.00         6.04          0         30
sdc              73.60         0.00         6.06          0         30
sdd              64.60         0.00         6.06          0         30
sde               0.00         0.00         0.00          0          0
sdb              64.00         0.00         6.09          0         30
md0            3093.40         0.00        12.08          0         60
sdf              25.00         0.01         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              85.40         0.00         6.48          0         32
sdc              70.20         0.00         6.42          0         32
sdd              60.60         0.00         6.42          0         32
sde               0.00         0.00         0.00          0          0
sdb              73.60         0.00         6.48          0         32
md0            3301.20         0.00        12.90          0         64
sdf              21.60         0.01         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              57.20         0.00         5.50          0         27
sdc              65.40         0.00         5.55          0         27
sdd              58.60         0.00         5.55          0         27
sde               0.00         0.00         0.00          0          0
sdb              48.60         0.00         5.50          0         27
md0            2829.60         0.00        11.05          0         55
sdf              21.60         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              75.40         0.00         5.94          0         29
sdc              67.80         0.00         5.93          0         29
sdd              59.20         0.00         5.93          0         29
sde               0.00         0.00         0.00          0          0
sdb              65.60         0.00         5.94          0         29
md0            3039.20         0.00        11.87          0         59
sdf              18.20         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              75.60         0.00         5.78          0         28
sdc              64.40         0.00         5.71          0         28
sdd              56.60         0.00         5.71          0         28
sde               0.00         0.00         0.00          0          0
sdb              66.60         0.00         5.76          0         28
md0            2985.60         0.00        11.66          0         58
sdf              24.40         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              69.80         0.00         6.08          0         30
sdc              74.80         0.00         6.18          0         30
sdd              66.00         0.00         6.18          0         30
sde               0.00         0.00         0.00          0          0
sdb              59.60         0.00         6.10          0         30
md0            3092.80         0.00        12.08          0         60
sdf              23.00         0.03         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              85.60         0.00         6.38          0         31
sdc              68.00         0.00         6.31          0         31
sdd              59.20         0.00         6.31          0         31
sde               0.00         0.00         0.00          0          0
sdb              74.40         0.00         6.38          0         31
md0            3248.80         0.00        12.69          0         63
sdf              25.60         0.04         0.11          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              70.80         0.00         5.62          0         28
sdc              65.00         0.00         5.64          0         28
sdd              58.40         0.00         5.64          0         28
sde               0.00         0.00         0.00          0          0
sdb              59.40         0.00         5.62          0         28
md0            2882.60         0.00        11.26          0         56
sdf              17.60         0.00         0.05          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              82.20         0.00         6.75          0         33
sdc              81.40         0.00         6.76          0         33
sdd              70.40         0.00         6.76          0         33
sde               0.00         0.00         0.00          0          0
sdb              72.00         0.00         6.75          0         33
md0            3458.40         0.00        13.51          0         67
sdf              20.00         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              79.20         0.00         5.96          0         29
sdc              67.60         0.00         5.92          0         29
sdd              58.20         0.00         5.92          0         29
sde               0.00         0.00         0.00          0          0
sdb              67.00         0.00         5.96          0         29
md0            3039.20         0.00        11.87          0         59
sdf              22.60         0.00         0.07          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              69.00         0.00         5.80          0         29
sdc              71.60         0.00         5.87          0         29
sdd              63.40         0.00         5.87          0         29
sde               0.00         0.00         0.00          0          0
sdb              58.60         0.00         5.80          0         29
md0            2986.80         0.00        11.67          0         58
sdf              20.40         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda              76.60         0.00         6.06          0         30
sdc              64.20         0.00         6.02          0         30
sdd              55.40         0.00         6.02          0         30
sde               0.00         0.00         0.00          0          0
sdb              64.00         0.00         6.06          0         30
md0            3091.60         0.00        12.08          0         60
sdf              18.80         0.00         0.06          0          0
sdg               0.00         0.00         0.00          0          0

De

```

---

### Post by jtupulis on 2011-09-15
So, basically, the same - enough memory, not swapping, CPU less busy, but still busy just with waiting for io, array slow.

Will try different mount options now.

---

### Post by jtupulis on 2011-09-15
Yeah, smartctl -l for all disks.

---

### Post by rubylaser on 2011-09-15
Good, when you have a chance to run the dd tests, let use know how it goes.  Also, maybe try it with a smaller testfile, so you can see higher speeds as well.
```
dd if=/dev/zero of=/media/V_data_3000/testfile.out bs=1M count=10000
```
```
dd if=/media/V_data_3000/testfile.out of=/dev/null bs=1M count=10000
```

---

### Post by jtupulis on 2011-09-15
Guys, seem that mount options are the cause. Just umount-ed and mounted manually, wo any options and array speed is rocking again. Will wait for some time if it persists, then dig into options.

---

### Post by jtupulis on 2011-09-15
Hey, I already did the tests - see my previous posts.

---

### Post by jtupulis on 2011-09-15
Left just rw option in /etc/fstab for an array, restarted, speeds are good :)

Any suggestions which option made all the fuss?

```

/dev/md0		/media/V_data_3000	ext4	rw,group,owner,users,exec,auto,sync,user	0	0

```

---

### Post by jchung on 2011-09-15
> **jtupulis said:**
> Left just rw option in /etc/fstab for an array, restarted, speeds are good :)

Any suggestions which option made all the fuss?

```

/dev/md0		/media/V_data_3000	ext4	rw,group,owner,users,exec,auto,sync,user	0	0

```

Glad you got it figured out! 

Sorry... I've never used the other options you have listed there other than 'sync'. You might try using 'async' and see if it helps. Otherwise I can't comment on the others. 


Joo

---

### Post by rubylaser on 2011-09-15
I always just use defaults with my mount options.  Everything works well and I can saturate a gigabit connection.  I'm glad you got it working, you can mark the thread as solved under the thread tools.

---

### Post by jeremiamorling on 2013-01-15
I love you guys!
Mounting without options.
Went from local write speed at 17 MB/s to around 170 MB/s. Ten times the speed when mounting raid 1 without options.:popcorn:

---

### Post by rubylaser on 2013-01-15
Glad that this old post helped you out :)

---

