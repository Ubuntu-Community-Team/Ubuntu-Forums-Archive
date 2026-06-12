---
title: "I need advice on RAID 0 setup (mdadm)"
date: 2011-01-27
forum: Server Platforms
---

### Post by effenberg0x0 on 2011-01-27
Hi, I have a server than runs most of my Home-office needs: DHCP3-server, UFW, Squid, DNS Server, FTPd, LAMP, Samba, cups, etc. 

/dev/sda (160GB disk) is the Ubuntu operating system:
```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19084   153283584   83  Linux
/dev/sda2           19084       19458     3004417    5  Extended
/dev/sda5           19084       19458     3004416   82  Linux swap / Solaris

```

/dev/sdb (1.5TB) are all my work files, mounted on /**media/NAS**. The disk is 96% full **and this is my main problem right now.**
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   83  Linux

```

/dev/sdc (250GB)is /home
```

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

```

[B]The problem is: I need /media/NAS to grow immediately and without loosing a single work file in the process.
[/B]

**Here's the plan:**
**Step 1:** I have **only one extra 1.5TB HDD**, same vendor/model/specs as /dev/sdb. I want to, firstly, RAID 0 them to 3TB without loosing any of the data on /dev/sdb. Possible?

**Step 2:** If Step 1 goes ok, I will put my hands on two other 1.5TB HDD (again, same vendor/model/specs) in a couple months. From that point on, I can move to better RAID than 0.

From all I have read so far, it seems that I would be obligated to format /dev/sdb and /dev/sdd before creating the RAID array device with mdadm --create /dev/md0 ----level=0 --raid-devices=2 /dev/sdb1 /dev/sdd1. I would loose all the data at /dev/sdb this way. There has to be other way.

**Questions are:** 
a) What if I create a "wrong" RAID 0, with only one disk (the new, empty HDD /dev/sdd), specify missing 1 disk (/dev/sdb) and then plug /dev/sdb. Would I still loose all the data or would the two HDD sync as RAID 0?

b) Seriously, what is the right way to do it. I am very confused right now.

Thanks,
Effenberg

---

### Post by YesWeCan on 2011-01-28
Good question. I just set up a RAID 10 so I am interested in this topic. mdadm never ceases to surprise me with it's cleverness so it wouldn't surprise me if it were able to construct a RAID 0 starting from a degraded state.

I think your proposal is on the right lines. I image you would need to use the new drive to make a degraded RAID 0 and then copy all your files on to it before reformatting the old drive and adding it to the array. if this works at all that is.

One way to test this would be to install VirtualBox somewhere with Ubuntu as guest and create a couple of virtual disks to trial your proposal. I may try this and get back to you with the result unless someone provides an answer first.

---

### Post by YesWeCan on 2011-01-28
[COLOR=Navy]mdadm: This level does not support missing devices[/COLOR]

[SIZE=2]Sorry, [/SIZE][SIZE=2]it seems mdadm will not permit a missing device for a RAID 0.
You may have to buy another 1.5TB disk (or two for RAID 10) and set the RAID 0 up on blank disks.[/SIZE]

---

### Post by psusi on 2011-01-28
Create a single disk raid1.  You can turn a normal disk into that without data loss.  Then you can reshape that into a raid0 with the second disk.

---

### Post by psusi on 2011-01-28
Darn... it looks like it won't reshape from raid 1 to raid 0, nor create a single disk raid 0, nor a raid10 with only 1 near copy.

---

### Post by effenberg0x0 on 2011-01-28
Thanks foir your replies guys. Tried both suggestions with no luck. Damnned... It's really getting complicated.

What I did so far:

$sudo umount /dev/sdb1 #old full HDD
$sudo mdadm --create --force --verbose /dev/md0 --level=0 --raid-devices=1 /dev/sdd1 #As funny as it seems, it worked LOL
$cat /proc/mdstat
$sudo mkfs.ext4 /dev/md0
$cat /proc/mdstat
$sudo mkdir /media/RAID && sudo mount /dev/md0 -fs ext4 /media/RAID
$cat /proc/mdstat
$sudo mount /media/nas #old full HD
$cp -axv /media/nas/* /media/RAID #This is whats going on for hours. I can see the files are beeing moved successfully, of course.

Ok, but how in hell am I gonna add the old disk to the RAID after the copy process...Yeah, back to the start point. Great.

---

### Post by dtfinch on 2011-01-28
Two alternative non-raid options I can think of:

1: Create LVM volume on new disk. Move files from old to new. Unmount both and grow the new LVM volume onto the new disk (destroying the old in the process). Resize the filesystem to fill up the new space. And remount. The result will be comparable to a RAID 0, but growable and without striping. More of a JBOD.

2: Use UnionFS so that the old disk becomes read-only, and all changes are written to the new disk. This is less risky with regards to existing data, but will slower be less space efficient in the future.

To reclaim some space immediately, if your drive is formatted ext3/4, you could use "tune2fs -m0 /dev/sdb1" to reduce the reservation from 5% to 0%.

---

### Post by psusi on 2011-01-28
Right... it won't let you add a disk to a raid0, only raid1, 4 and 5.

Apparently the ability to reshape raid 0 and 10 will be added to an upcoming release of mdadm.

---

### Post by YesWeCan on 2011-01-28
Here's an idea.
Format the new HD with 2 equal sized partitions.
Copy half your data to one partition and half to the other.
Then reformat the old HD into 2 equal sized partitions.
Copy the contents of the first partition of the new HD to the second partition of the old HD.
You should now have your work data split between the 2nd partitions of the two HDs.
Then create a RAID0 using the 1st partitions of both HDs.
Copy all your data into the new RAID0 partition.
Then delete the 2nd partitions on both HDs and expand the 1st partitions to full size.
You should now have a 3TB RAID0

---

### Post by effenberg0x0 on 2011-01-28
YesWeCan => Thanks, it sounds fun :) Another thing I am gonna try tonight is creating a degraded RAID 4. I should end up with a 3GB RAID without the parity disk, which is just as insecure as RAID 0 anyway. When the two new disks arrive in a couple weeks, it would be easy to add them to the array. (they are 2TB, not 1,5TB thou...). 

I'll post my results here in a couple hours. Sleeping is overrated anyway.

---

### Post by YesWeCan on 2011-01-28
Sleep when yur dead. ;)
Do be very careful when you are resizing partitions. This is the sort of stuff you are not supposed to do unless you have backed your data up. Plenty of web sites explaining all the steps.
Go for it!

BTW I read somewhere that RAID10 may be faster than the other redundancy methods because there are no checksum/parity calculations consuming processor bandwidth. Other RAIDs are more space-efficient.

---

### Post by YesWeCan on 2011-01-28
[http://www.pcguide.com/ref/hdd/perf/raid/levels/comp.htm](http://www.pcguide.com/ref/hdd/perf/raid/levels/comp.htm)

---

### Post by effenberg0x0 on 2011-01-28
Thanks! Very interesting info. 

I had never tried to tar + gzip 1.5TB before. It feels like slow painful death. Hopefully my grandchildren will be able to tar -xvpzf nas_backup.gz. It's been two hours and the backup file is still 50GB.

---

### Post by psusi on 2011-01-28
I don't think you can expand a raid partition, but I did not try raid4.  Will it let you create a single disk raid 4?  Probably not, so that won't work either.

---

### Post by effenberg0x0 on 2011-01-29
I'm not there yet, still moving the files.

But I am thinking that instead or resizing the RAID 0, I could go for a degraded RAID 4 missing 2 disks. Once all files are moved from the non-RAID partitions to the RAID ones, I format the non-RAID partitions and add them as the two missing disks to RAID 4.

---

### Post by effenberg0x0 on 2011-01-29
**Update**

- Dividing the files of one entire 1.5TB HDD (the old one) between the 2nd partitions of the two 1.5TB HDDs took one entire day. I had decided to compact the entire old HDD with tar + gzip and then use split, to make things as bulletproof as possible. Slow, but worked anyway.

- I managed to create a degraded RAID 5 using the first partitions of the two 1.5TB HDDs and ended up with a 1.5TB /dev/md0. It was not necessary to use --force or other resource. The RAID has full 1,5TB available (no parity is being done so).

- Right now I am extracting && moving back the data from the two second partitions to the RAID.

- Once that is finished, probably in a couple years, I'll format the two second partitions and attempt to resize the first ones (RAID) to take over the entire disks. I did saw some posts on the net saying it is possible to resize a RAID partition. Too tired right now to find the urls. Lets hope so. I'll post the answer here as soon as I find it out.

---

### Post by YesWeCan on 2011-01-30
You are getting there.

In brief, you will need to unmount the RAID and unmount the two 1.5TB drives. Then use Gparted on each drive in turn to delete the 2nd partition and grow the first partition to the full size. You do not need to do any reformatting. Then use the grow option on mdadm to increase the size of the RAID partition and then resize the filesystem using resize2fs.

You'll need to google for details on doing these steps.

---

### Post by effenberg0x0 on 2011-01-30
Actually I am glad you mentioned this method (Gparted to increase partitions and mdadm --grow). I was kind of scared of using Gparted and messing up with the raid...

I'm on e2fsck for some hours. as soon as I get to boot and play with the partitions I'll post updates.

Thanks

---

### Post by YesWeCan on 2011-01-30
Be scared...be very scared. :)
Don't take my word for this because I have not done this particular thing before either. I have some experience with Gparted and mdadm and have read some on line tutorials. So I expect this to work but I am in no position to offer guarantees.
So do your own research of Gparted and mdadm and satisfy yourself that your data will be safe. Like I said before, one would normally back ones data up when undertaking partition resizing, not so much because the tools are unreliable but more because it is easy to make a mistake.

---

### Post by psusi on 2011-01-30
> **YesWeCan said:**
> You are getting there.

In brief, you will need to unmount the RAID and unmount the two 1.5TB drives. Then use Gparted on each drive in turn to delete the 2nd partition and grow the first partition to the full size. You do not need to do any reformatting. Then use the grow option on mdadm to increase the size of the RAID partition and then resize the filesystem using resize2fs.

You'll need to google for details on doing these steps.

This won't work.  Even if gparted does not refuse to resize the partition because it does not know about raid, it will break the raid because the raid superblock is at a fixed offset from the end of the partition.

I posted this question to the linux-raid mailing list and got a reply from Neil Brown that might just work.  It needs tested first though:

> 

You need to use the RAID5 personality to do the re-striping.

You should absolutely test out any procedure you end up with to make sure it
actually works.  e.g. with a couple of USB drives or something like that.
Maybe just a couple of loop-back devices on mostest sized files (100Meg would
be plenty for testing).

Firstly you need to convert the single device into a 2-device RAID4.
Something like:
 
  mdadm -C /dev/md0 -l4 -n2 -e 1.0 /dev/sda missing

The '-e 1.0'. will make sure the metadata goes at the end
of the device.
Note that this will DESTROY the last 8K or so of the device.  And will round
the remaining size down to the chuck size (which might be 512K by default).
You should check that the filesystem doesn't extend that far.  If it does,
you might need to resize the filesystem to be smaller.

Alternately you could create this md0 on the new device, and then
copy the original device onto the new md0 (mkfs, then "cp -a" or similar).

Once you have a degraded 2-drive RAID4 (i.e. with only one drive)  that
contains your data you are ready for step 2.
mdadm-3.2 might do this for you, but it isn't released yet and I haven't
tested so it probably doesn't.
You need to add the second device and then reshape to be a 3-drive RAID4
without the second device being recovered first.
So:

  echo frozen > /sys/block/md0/md/sync_action
  mdadm /dev/md0 --add /dev/the-other-device
  mdadm --grow --force /dev/md0 --raid-disks=2

You will of course test this before trying it on live data.
And you need a fairly recent kernel.

If/when the above works you will have a degraded 3-drive RAID4
which is much like a 2-drive RAID0 except that it does lots of pointless
parity calculations.
You can convert it to RAID0 with the command:

  echo raid0 > /sys/block/md0/md/level

and (drum roll) you have your RAID0 all configured.

You may decide that this isn't worth the effort and that you want to
wait for mdadm to support it natively.  The choice is yours.
But you will need to wait for at least 3.2.1.

If you do experiment with this, please report any success or failure.


---

### Post by YesWeCan on 2011-01-30
[QUOTE=psusi]This won't work.  Even if gparted does not refuse to resize the partition because it does not know about raid, it will break the raid because the raid superblock is at a fixed offset from the end of the partition.

I posted this question to the linux-raid mailing list and got a reply from Neil Brown that might just work.  It needs tested first though:[/QUOTE]

Good call. I just tried a simulation in VirtualBox and Gparted won't allow the first partitions to be resized because it's filesystem check considers the drive to be reserved by another process. So luckily Gparted won't try to resize.

I'll try out the method you posted and see if it works.

---

### Post by YesWeCan on 2011-01-30
I get this far and then an error

root@pc:/sys/block/md0/md# echo frozen > sync_action
bash: echo: write error: Invalid argument


root@pc:/sys/block/md0/md# cat sync_action 
idle

---

### Post by YesWeCan on 2011-01-30
root@pc:/sys/block/md0/md# mdadm -V
mdadm - v2.6.7.1 - 15th October 2008


> What you want is "frozen" which is only available since 2.6.31.
from: [http://www.issociate.de/board/post/502427/MD:_%22sync_action%22_issues:_pausing_resync/recovery_automatically_restarts..html](http://www.issociate.de/board/post/502427/MD:_%22sync_action%22_issues:_pausing_resync/recovery_automatically_restarts..html)

So I'm using Ubuntu 9.04 in VB with kernel 2.6.28-19
Tedious. I'll install Ubuntu 10.04 in VB and try again.

---

### Post by YesWeCan on 2011-01-30
```
root@pc:~# echo frozen > /sys/block/md0/md/sync_action 
root@pc:~# mdadm /dev/md0 --add /dev/sdc
mdadm: added /dev/sdc
root@pc:~# mdadm --grow --force /dev/md0 --raid-disks=2
mdadm: /dev/md0: Cannot reshape array without increasing size (yet).
root@pc:~# echo raid0 > /sys/block/md0/md/level 
bash: echo: write error: Invalid argument
root@pc:~# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [raid0] 
md0 : active raid4 sdc[2](S) sdb[0]
      104384 blocks super 1.0 level 4, 64k chunk, algorithm 0 [2/1] [U_]
      
unused devices: <none>
root@pc:~# mdadm -V
mdadm - v2.6.7.1 - 15th October 2008
root@pc:~# uname -r
2.6.32-28-generic
root@pc:~# 
```

Now fails at the adding the second HD stage. I started with 2 unformatted HDs, sdb and sdc. Created the degraded RAID 4 on sdb and formatted it ext4. Then the above.

---

### Post by psusi on 2011-01-30
He said you need a recent kernel, so probably need Maverick.

---

### Post by ThelenShar on 2011-02-07
I have also tried this but it gets stuck on the:
raid:~# echo raid0 > /sys/block/md1/md/level
-bash: echo: write error: Invalid argument


I had wondered if he made a typo when he did the grow, raid-devices=2 so I tried 3, didn't seem to matter. I've also tried with and without paritioning the raid device (md1), ie md1p1 or just plain md1. Doesn't seem to matter, when I try mount says no FS.

I've got:
raid:~# uname -a
Linux raid 2.6.32-5-amd64 #1 SMP Wed Jan 12 03:40:32 UTC 2011 x86_64 GNU/Linux
raid:~# mdadm -V
mdadm - v3.1.4 - 31st August 2010

so pretty recent, not sure what the issue is. I also had toyed with the idea of using RAID5, that would work, however we don't want to loose all the extra storage :(

Oh and it is on debian not that that should matter.

---

### Post by ThelenShar on 2011-02-07
Got a reply :D

> Not quite new enough.

You need 2.6.35 to allow conversion between RAID4 and RAID0,
and 2.6.38 to allow conversion from RAID1 to RAID0.

But my notes in the link you give don't mention RAID1 at all, so may they
aren't appropriate for what you are trying to do...

What *are* you trying to do??

So I'll try upgrade to .38 and go from there :)

---

### Post by ThelenShar on 2011-02-09
Finally got it to work:
before: Array Size : 2096116 (2047.33 MiB 2146.42 MB)
after: Array Size : 4192256 (4.00 GiB 4.29 GB)

It was a beautiful thing after doing the reshape and starting the array and then doing "fsck /dev/md0" and seeing "clean" :D

I'll write up a full guide at some point, however most of the props goes to NeilBrown who helped me through the intricate parts of mdadm :D

---

