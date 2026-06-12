---
title: "mdadm: 3 drive RAID5 Intermittent degrade state"
date: 2014-02-25
forum: Server Platforms
---

### Post by tylersontag on 2014-02-25
I've had an eSATA2 connected external enclosure that i've been running an mdadm managed RAID 5 on for the past 2 years.  I've always had issues with the RAID entering a DEGRADED state every so often... no real estimate of the frequency.  Sometimes it will stay active for a week or more, some times it will go down after only a few days.   In each case, rebooting the box and re-assembling the RAID will bring it back up.  I'll usually run a check on the RAID after one of these events and notice that, that will usually cause it to stay up longer than had i not done a check.

Ive been running the following script after assembling the RAID.  I found it after i had one of these events and the assembly action looked to be taking an unreasonably long amount of time (assembly check was running at <1kb/s on a 3-2TB array)   It looks like all its doing is setting some block sizes but i thought i'd put it in here.

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
CHUNKSIZE=512          # in kb
BLOCKSIZE=4             # of file system in kb
NCQ=disable             # disable, enable. ath. else keeps current setting
NCQDEPTH=31             # 31 should work for almost anyone
FORCECHUNKSIZE=true     # force max sectors kb to chunk size > 512
DOTUNEFS=false           # run tune2fs, ONLY SET TO true IF YOU USE EXT[34]
RAIDLEVEL=raid5         # raid5, raid6


## code ##
# test for priviledges
if [ "$(whoami)" != 'root' ]
then
  echo $(date): Need to be root >> /data51/smbshare1/#tuneraid.log
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
echo $(date): Success >> /home/USER/Programs/#tuneraid.log
exit 0
```

I can pull some other statistics if anyone needs them, but i didn't want to flood the initial post with a bunch of logs that may or may not be germane.  

I'm tossing a line out here because, while i've been just "living" with the situation, i've been doing alot more traveling and since i'm unable to do alot of the assembly steps remotely, this has become a bigger issue.  I wrote a script that uses smartctl to log the temperature of the drives to a file while there up and stop when they go down, suspecting that heat may be a factor but i don't believe that to be the case.  So i'm back to the drawing board, any suggestion for things to look into would be appreciated.

I'm running the following version, which i realize isn't Ubuntu Server, but it looked like more mdadm traffic went on here.

istributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise

---

