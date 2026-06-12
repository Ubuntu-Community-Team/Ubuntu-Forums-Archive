---
title: "Problem with nested RAID"
date: 2012-09-14
forum: Server Platforms
---

### Post by asyr on 2012-09-14
Hi there.

I'm using Kubuntu 12.04 (but I think that the problem I had is for all ubuntu variants).

I had 3x 500 GB that had some partitions each. My main partitions was:
/dev/sda2 for /home (~450 GB)
/dev/sdb2 for /home/store (~450 GB)
/dev/sdc2 for /home/store2 (~450 GB)

I had no redundancy and I got a new 2TB disk. I decide to use softraid to protect my /home partition and my /...store partitions.

So I create the following partitions to the new disk sdd:
/dev/sdd1 : 900 GB
/dev/sdd2 : 450 GB

I created (with mdadm) a RAID1 ARRAY /dev/md/store:
```
 mdadm --create /dev/md/store --level=1 --raid-devices=2 /dev/sdd1 missing
```I created a filesystem to the new partition (/dev/md/store) and I copied all contains from /home/store and /home/store2 to this filesystem. After this, I created a RAID0 ARRAY /dev/md/store_m:
```
 mdadm --create /dev/md/store_m --level=0 --raid-devices=2 /dev/sdb2 /dev/sdc2
```The ARRAY created OK and I added to the RAID1 ARRAY:
```
 mdadm --manage /dev/md/store --add /dev/md/store_m
```Synchronization started and finished (after ~3 hours) without problems.

In the mean time I created another RAID1 ARRAY:
```
 mdadm --create /dev/md/home --level=1 --raid-devices=2 /dev/sdd2 missing
```I created a filesystem to the new partition (/dev/md/home) and I copied  all contains from /home to this filesystem.  After this, I added the original /home partition as a copy to the new RAID1 ARRAY:
```
 mdadm --manage /dev/md/home --add /dev/sda2
```Synchronization started and finished (after ~1,5 hours) without problems.

I fixed the mount point and the /etc/fstab file, and I rebooted the server.

Now the problems begins: The system does not start because of a degraded array (the /dev/md/store). I added the 'bootdegraded=true' flag to the kernel and the system restarted, but the /dev/md/store it was degraded. 
I tried to re-add the /dev/md/store_m, but mdadm said that was not possible, so I added it again and a new synchronization started.

When finished I rebooted the server, but the /dev/md/store was degraded again. I tried to re-add the /dev/md/store_m, but mdadm said that was not  possible, so I added it again and a new synchronization started.

In order to control the order of the ARRAY creation (as I hopped) I added the propper ARRAY entries to the /etc/mdadm/mdadm.conf file:
```
ARRAY /dev/md/store_m metadata=1.2 name=yoda:store_m UUID=48bcf81c:b21fb2ad:f1734a2e:150f77cd
ARRAY /dev/md/home metadata=1.2 name=yoda:home UUID=45d224dc:9b6f7982:bde27a0c:25027c70
ARRAY /dev/md/store metadata=1.2 name=yoda:store UUID=7bb74d32:70dbc793:8b12b2d3:ec47a6b2
```I recreate initramfs and reboot the server.

Once again /dev/md/store was degraded, no re-add, new synch. I added 'device=' option to /etc/mdadm/mdadm.conf to force device ordering:
```
ARRAY /dev/md/store_m metadata=1.2 name=yoda:store_m UUID=48bcf81c:b21fb2ad:f1734a2e:150f77cd devices=/dev/sda2,/dev/sdc2
ARRAY /dev/md/home metadata=1.2 name=yoda:home UUID=45d224dc:9b6f7982:bde27a0c:25027c70 devices=/dev/sdd2,/dev/sdb2
ARRAY /dev/md/store metadata=1.2 name=yoda:store UUID=7bb74d32:70dbc793:8b12b2d3:ec47a6b2 devices=/dev/sdd1,/dev/md/store_m

```I recreate initramfs and reboot the server.

Again  /dev/md/store was degraded, no re-add, new synch. I added 'DEVICE'  option to /etc/mdadm/mdadm.conf with a hope that will help:
```
DEVICE /dev/sda2
DEVICE /dev/sdb2
DEVICE /dev/sdc2
DEVICE /dev/sdd[12]
DEVICE /dev/md[1-9]*
```I recreate initramfs and reboot the server.

Again  /dev/md/store was degraded!!!!

Now I'm stuck ! Any help will be useful...

---

### Post by asyr on 2012-09-17
No one?       Seems to be tough...

I performed some additional tries, putting the /dev/md/store_m as the first device of the /dev/md/store array (by reconstructing all arrays), to "force" this as the first device, without luck...

Could be problem the slightly different size of the /dev/md/store_m and /dev/sdd1 devices? (sdd1 is bigger for 186 blocks)

How I can create the /dev/md/store_m (that is a RAID-0 of sda2 and sdc2) to be the same size of sdd1?
I have to "reduce" sdd1? How (without repartitioning sdd)?

---

### Post by asyr on 2012-09-18
I'm still trying configurations, without luck !!!

Now I have the RAID-1 /dev/md/store array to have just one part (the /dev/md/store_m RAID-0 array) and a 'missing' part. When the system boots, just recognizes the 'store_m' (RAID-0) array and not the higher level 'store' RAID-1 array.

Do any one knows why is that?

Additionally I got the following (from dmesg):
```
[    1.831468] md: RAID0 configuration for md126 - 2 zones
[    1.831470] md: zone0=[sda2/sdc2]
[    1.831474]       zone-offset=         0KB, device-offset=         0KB, size= 879092736KB
[    1.831475] md: zone1=[sdc2]
[    1.831478]       zone-offset= 879092736KB, device-offset= 439546368KB, size=  38347200KB
```and I do not know what means.

Any help will be useful.

---

### Post by rubylaser on 2012-09-19
This setup with RAID0 nested in a RAID1 is definitely not the ideal way to set this up.  If you just wanted to provide a backup to your single disk setup, you could have used your 2TB drive as a backup.  All that being said,  it sounds like you're running [into this bug]("http://ubuntuforums.org/showpost.php?p=11388915&postcount=18").

---

### Post by asyr on 2012-09-19
**rubylaser**,  first of all thanks for the reply, but I have already read for this bug and I tried the workaround, without success.
I think that this bug has more to do with external devices that are not (totally) ready during boot.

I have something new in my mind now. I'll create 2 partitions in sdd disk equal with the 2 from the old disks and I'll create a RAID 10 (1+0) ARRAY. In order to do this I have to move the data to an external disk temporarily (I borrowed an external disk from a friend).

I'll post the results to this thread ...

---

### Post by rubylaser on 2012-09-19
Just so you know, an mdadm RAID10 array is not expandable in the future like RAID5/6 arrays are, so you wanted be able to add another RAID1 to the stripe download the line.

---

### Post by darkod on 2012-09-19
Also, while this new setup will allow you to use the disks in somewhat more optimal way, have in mind that having two partitions which are part of arrays with partitions on other disk will make the bigger disk a bottle neck.

For every write the data on the smaller disks is written but on the larger disk it will have to be written to both partitions at the same time, which will make it slower I guess.

Not a deal breaker, but just a thought.

---

### Post by asyr on 2012-09-20
**rubylaser**, thanks for the comment. I know that the array that I'm trying to create is not (easily) expandable, but it's for my home server where I'm keeping our photos/videos/etc, so I do not plan (in the near future) to expand it. As for the backup, I do not have a backup media and for that reason I decide to have some redundancy for my data that are unique. 

**darkod**, thank you also for your note. Maybe I'll have a small performance problem, but as I said above, this is for my home server and the high performance is not my first target; the redundancy is.

Now I'm copying the data to an external USB disk in order to be free to create the array(s) without the fear that my data will be lost. I'll post here my results.

---

### Post by asyr on 2012-09-20
[B]FAILED FAILED FAILED !!!

[/B]I'm very confused. I repartitioned my new sdd disk and created a perfect RAID 10 (1+0) ARRAY :```

mdadm --create /dev/md/store1 --level=1 --raid-devices=2 /dev/sda2 /dev/sdd5
mdadm --create /dev/md/store2 --level=1 --raid-devices=2 /dev/sdc2 /dev/sdd6
...wait for the syncing of both arrays...
mdadm --create /dev/md/store --level=0 --chunk-size=64 --raid-devices=2 /dev/md/store1 /dev/md/store2
```The arrays created successfully. I created an ext4 fs into /dev/md/store and I was able to save files there.
I performed ```

mdadm -E --scan >> /dev/mdadm/mdadm.cong
update-initramfs -u
update-grub
```I updated the /etc/fstab (using UUID of the /dev/md/store -> /dev/md124) and I rebooted the server.

AGAIN THE FILESYSTEM OF THE /dev/md/store DID NOT MOUNTED !!!

I check the partition types of the partitions, were 'Linux' instead of 'Linux Auto Raid' (fd). I changed the partition types of all involved partitions, update initramfs and grub, and reboot.

THE FILESYSTEM OF THE /dev/md/store DID NOT MOUNTED !!!

If I'll put:```

mdadm -A -a yes /dev/md/store
mount /dev/md/store /home/STORE
```into /etc/rc.local I'll by pass my problem, but this is not a fix.

Seems that the system recognizes the not-nested RAID arrays (my /home RAID-1 array mounted OK) but not the nested RAID arrays.

Any help ?

---

### Post by rubylaser on 2012-09-20
The proper way to make an mdadm RAID10 is buy passing the level=raid10, like this (it will setup everything, properly for you automatically).
```
mdadm --create /dev/store -v --raid-devices=4 --chunk-size=64 --level=raid10 /dev/sda2 /dev/sdd5 /dev/sdc2 /dev/sdd6
```
^ You need to make sure that the /dev/sdd partitions end up in opposite mirrors, or the loss of that drive will kill everything.

Wait for this to finish syncing, and then name of the file that you need to create is /etc/mdadm/mdadm.conf.  You can do that like this.

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR youruser@gmail.com" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Update the initramfs
```
update-initramfs -u
```

Then, create a filesystem on the array, and an /etc/fstab entry. Finally, reboot.

---

### Post by asyr on 2012-09-21
**rubylaser**, thanks for the advice. I followed and worked !

The only issue was that the partitions of the RAID-10 must be all of the same size or the size of the smaller one is used. So I need to make some re-partitioning to my environment to gain the maximum space.

Question: How I can determine which partition is mirrored with which (in order to avoid partition mirroring on the same physical disk) ?

_**EDIT:**_
I found the answer into [this article]("http://www.linuxquestions.org/questions/linux-server-73/software-raid10-does-the-disk-order-in-mdadm-matter-671016/").

---

### Post by asyr on 2012-09-21
Finally I created a RAID10 array with 4 same size partitions and the system now can mount this device at boot without problem.

I marked this thread as SOLVED because I manage to reach my target (redundancy for my valuable data) but the problem remains: the system did not recognizes at boot time the nested RAIDs.

Any way, thanks a lot **rubylaser** and **darkod** for your help.

---

