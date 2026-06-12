---
title: "MDADM and RAID Question"
date: 2009-11-14
forum: Server Platforms
---

### Post by Krupski on 2009-11-14
Hi all, hope this is the right place to ask...


I'm running a home file server with Ubuntu 64 bit Server v9.04 - works great.

Until yesterday, I was running a 3 disk RAID-5 system. I added a fourth drive to the system.

The way I did it was to backup all the data on it, then zero the superblocks of the 3 drives, then add the fourth, then recreate the array using the MDADM -C etc, etc.... command.

It all worked fine.

My question is, I know that the size of a RAID-5 array is N-1 where "N" is the number of drives.

There are 4 one terabyte drives in the server, and the RAID drive (/dev/md0) correctly shows as a 3 TB drive.

What I don't understand is the result of the 'MDADM --detail --scan' command which yields this:

```

root@storage:~# mdadm --detail --scan
ARRAY /dev/md0 level=raid5 num-devices=4 **[COLOR="Red"]spares=1[/COLOR]** UUID=d843258a:5f2a488e:2e29483d:f114274d

```

What the heck does "spares=1" mean?

Of course, I don't want a TWO terabyte array with a "spare", and indeed the /md0 device correctly shows as 3 TB.

What does "spares=1" mean and should I worry about it and/or can I fix it?

Thanks!

-- Roger

---

### Post by fjgaude on 2009-11-14
Hmmm... interesting! What does this show:

```
sudo mdadm -D /dev/md0
```

This is always the acid test of an array.

---

### Post by Krupski on 2009-11-14
> **fjgaude said:**
> Hmmm... interesting! What does this show:

```
sudo mdadm -D /dev/md0
```

This is always the acid test of an array.

Did it... here's the result:


```

root@storage:/# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Nov 13 19:13:33 2009
     Raid Level : raid5
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Nov 14 11:11:02 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : d843258a:5f2a488e:2e29483d:f114274d (local to host storage)
         Events : 0.67

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd

```


By the way, my boot drive is /dev/sde (a compact flash card). The RAID array only holds data.

-- Roger

---

### Post by Krupski on 2009-11-14
> **fjgaude said:**
> Hmmm... interesting! What does this show:

```
sudo mdadm -D /dev/md0
```

This is always the acid test of an array.

Something else I noticed... the "spares=1" thing is gone now:

```

root@storage:/# mdadm --detail --scan
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=00.90 UUID=d843258a:5f2a488e:2e29483d:f114274d

```


Last night (when I first rebuilt the array) it was doing a re-sync (I watched it from '/proc/mdstat').

This morning, of course, the array is finished syncing. Could that be the difference?

(edit to add): The "metadata=00.90" thing was also in the line last night... I took it out because '/etc/mdadm/mdadm.conf' seems to choke on it. In the original, it was there.

---

### Post by fjgaude on 2009-11-14
Well, I usually don't do anything with an array when it is building or re-building... this spare thing does come up from time to time. Can't say if it does any harm, likely the scan is in error when a re-building is occurring.

The metadata thing has off-and-on been an issue depending on which version of mdadm you use. The newer versions don't show it and if the tag is not exact you will get an error from something.

Since the -D command shows all is well then you are go to go. Mount it, put a line in the /etc/fstab file and it assembles automatically during boot time.

---

### Post by Krupski on 2009-11-14
> **fjgaude said:**
> Well, I usually don't do anything with an array when it is building or re-building... this spare thing does come up from time to time.

Agreed.... I started the new array with the intention of letting it do it's rebuild / resync thing overnight and not even use the drive until it was done.

The only thing I did while the array was rebuilding was the 'mdadm --detail --scan' command to get the new "ARRAY...." line that goes into the mdadm.conf file since obviously the old one was now invalid.

THAT was when I saw the strange "spares=1" thing.

This morning when the array was done, all 4 drives were active and the "spares" thing was gone.

And since you say my array looks OK, I think I'll just not worry about it for now and run the server.

I'm tempted to zero the superblocks and remake the array again just to see if the "spares" thing is just an "artifact" of the rebuild process, but I don't have another overnight to waste right now.

Maybe another time!  :)

Thanks for all your input!

-- Roger

---

