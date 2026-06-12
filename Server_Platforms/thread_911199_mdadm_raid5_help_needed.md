---
title: "mdadm raid5 help needed"
date: 2008-09-05
forum: Server Platforms
---

### Post by trmentry on 2008-09-05
Hello Forums,

I have an issue that I'm hitting a brick wall on and hope that someone here can help me out.

I have 2 servers.   Hoth v2  and Hoth v3   v3 being the new better faster server. :)

Hoth v2 = Gutsy 
Hoth v3 = Hardy

Broght up v3 and added in the new hard drvies for the array  8x500 with 1 more for a spare (9 total).  

rsynced the data from v2 to v3.  

After 4 days of rsync... I did the following.

o removed the partitions on the drvies in v2.  
o shut the box down and gutted it.
o put the 8x 400 w/ 1 spare (9 total) from v2 itno v3.

Turned on v3.  v3 FREAKED.  wouldn't bring up /dev/md0 which was the original 500s it was built with.  Figured out that it was b/c drive assignments changed.  Fixed that

v3 sees the follwoing for the 400s.
```

root@hoth:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : inactive sdi1[0](S) sdp1[8](S) sdo1[6](S) sdn1[5](S) sdm1[4](S) sdl1[3](S) sdk1[2](S) sdj1[1](S)
      3125669888 blocks

```

they all spares.  

so I did a 

```

mdadm --examine --scan /dev/sd[ijklmnop]1  

```
then did a 
```

mdadm --assemble --uuid=<string> /dev/md1

```
Said not enough devices.  So tried this.
```

root@hoth:~# mdadm --assemble --run /dev/md1
mdadm: failed to RUN_ARRAY /dev/md1: Input/output error
mdadm: Not enough devices to start the array.

```

dmesg is showing the follwoing now..

```

[  412.949638] md: md1 stopped.
[  412.949649] md: unbind<sdi1>
[  412.949653] md: export_rdev(sdi1)
[  412.949693] md: unbind<sdp1>
[  412.949696] md: export_rdev(sdp1)
[  412.949713] md: unbind<sdo1>
[  412.949715] md: export_rdev(sdo1)
[  412.949743] md: unbind<sdn1>
[  412.949746] md: export_rdev(sdn1)
[  412.949762] md: unbind<sdm1>
[  412.949764] md: export_rdev(sdm1)
[  412.949780] md: unbind<sdl1>
[  412.949782] md: export_rdev(sdl1)
[  412.949798] md: unbind<sdk1>
[  412.949800] md: export_rdev(sdk1)
[  412.949815] md: unbind<sdj1>
[  412.949818] md: export_rdev(sdj1)
[  413.053861] md: bind<sdl1>
[  413.053978] md: bind<sdn1>
[  413.054097] md: bind<sdo1>
[  413.054245] md: bind<sds1>
[  413.054393] md: bind<sdj1>
[  413.054417] md: kicking non-fresh sds1 from array!
[  413.054422] md: unbind<sds1>
[  413.054425] md: export_rdev(sds1)
[  413.054428] md: kicking non-fresh sdo1 from array!
[  413.054431] md: unbind<sdo1>
[  413.054434] md: export_rdev(sdo1)
[  413.054436] md: kicking non-fresh sdn1 from array!
[  413.054439] md: unbind<sdn1>
[  413.054442] md: export_rdev(sdn1)
[  413.054444] md: kicking non-fresh sdl1 from array!
[  413.054447] md: unbind<sdl1>
[  413.054449] md: export_rdev(sdl1)
[  413.079463] raid5: device sdj1 operational as raid disk 1
[  413.079467] raid5: not enough operational devices for md1 (7/8 failed)
[  413.079514] RAID5 conf printout:
[  413.079516]  --- rd:8 wd:1
[  413.079517]  disk 1, o:1, dev:sdj1
[  413.079518] raid5: failed to run raid set md1
[  413.079554] md: pers->run() failed ...

```

so now 

```

root@hoth:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : inactive sdj1[1]
      390708736 blocks

```


What I'm wanting to do is to wipe md1 off the earth and rebuild it from scratch with /dev/sd[ijklmnop]1  

I tried to --zero-superblock --force /dev/md1  but that didn't work either.

Can someone please help?

Thanks

---

### Post by fjgaude on 2008-09-05
From my experience you don't -zero-superblock of an array, but to each drive in the array.

To re-use a drive coming from an array, I've always had to **stop** the array, **unmount** it, and then then **fail** and **remove** the drive... this likely has to be done for each drive in an array.

So much to learn about using **mdadm** when going from beginning to end, covering all the possibilities of use, eh?

---

### Post by trmentry on 2008-09-05
> **fjgaude said:**
> From my experience you don't -zero-superblock of an array, but to each drive in the array.

To re-use a drive coming from an array, I've always had to **stop** the array, **unmount** it, and then then **fail** and **remove** the drive... this likely has to be done for each drive in an array.

So much to learn about using **mdadm** when going from beginning to end, covering all the possibilities of use, eh?

thanks for that... i was able to get the array restarted... but I now have a very curious thing.

I stopped the array and then zero'ed each drive

```

mdadm --zero-superblock /dev/sd[ijklmnops]1

```

then recreated fresh.

```

root@hoth:~# mdadm --create --verbose /dev/md1 --level=5 --raid-devices=8 /dev/sd[ijklmnop]1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: size set to 390708736K
mdadm: array /dev/md1 started.
root@hoth:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdp1[8] sdo1[6] sdn1[5] sdm1[4] sdl1[3] sdk1[2] sdj1[1] sdi1[0]
      2734961152 blocks level 5, 64k chunk, algorithm 2 [8/7] [UUUUUUU_]
      [>....................]  recovery =  0.0% (56108/390708736) finish=463.4min speed=14027K/sec

md0 : active raid5 sdb1[0] sdf1[8](S) sdh1[7] sdg1[6] sde1[5] sdr1[4] sdc1[3] sdd1[2] sda1[1]
      3418687552 blocks level 5, 64k chunk, algorithm 2 [8/8] [UUUUUUUU]

unused devices: <none>
root@hoth:~# mdadm --add /dev/md1 /dev/sds1
mdadm: added /dev/sds1
root@hoth:~#
root@hoth:~#
root@hoth:~# mdadm --examine --scan
ARRAY /dev/md0 level=raid5 num-devices=7 UUID=c08f16fe:f0fb7dec:44e33c5a:20ebc66f
   spares=1
ARRAY /dev/md0 level=raid5 num-devices=8 UUID=a3ea7714:de2bf962:98512988:9ff2ba5b
   spares=1
ARRAY /dev/md1 level=raid5 num-devices=8 UUID=e0fccd56:52b6dfc6:98512988:9ff2ba5b
   spares=2

```

but what i find odd is i have 2 /dev/md0 which is odd, as the a3ea7714:de2bf962:98512988:9ff2ba5b is the right one and is online fine.  

but /dev/md1 is showing up w/ 2 spares, and should only have 1. 

So any pointers? 

Thanks again

---

### Post by trmentry on 2008-09-05
just in case it's needed

```

root@hoth:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Aug 31 23:51:50 2008
     Raid Level : raid5
     Array Size : 3418687552 (3260.31 GiB 3500.74 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 8
  Total Devices : 9
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Sep  5 09:27:10 2008
          State : clean
 Active Devices : 8
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : a3ea7714:de2bf962:98512988:9ff2ba5b (local to host hoth)
         Events : 0.82

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1
       2       8       49        2      active sync   /dev/sdd1
       3       8       33        3      active sync   /dev/sdc1
       4      65       17        4      active sync   /dev/sdr1
       5       8       65        5      active sync   /dev/sde1
       6       8       97        6      active sync   /dev/sdg1
       7       8      113        7      active sync   /dev/sdh1

       8       8       81        -      spare   /dev/sdf1
root@hoth:~# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Fri Sep  5 09:26:28 2008
     Raid Level : raid5
     Array Size : 2734961152 (2608.26 GiB 2800.60 GB)
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
   Raid Devices : 8
  Total Devices : 9
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri Sep  5 09:26:52 2008
          State : clean, degraded, recovering
 Active Devices : 7
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : e0fccd56:52b6dfc6:98512988:9ff2ba5b (local to host hoth)
         Events : 0.2

    Number   Major   Minor   RaidDevice State
       0       8      129        0      active sync   /dev/sdi1
       1       8      145        1      active sync   /dev/sdj1
       2       8      161        2      active sync   /dev/sdk1
       3       8      177        3      active sync   /dev/sdl1
       4       8      193        4      active sync   /dev/sdm1
       5       8      209        5      active sync   /dev/sdn1
       6       8      225        6      active sync   /dev/sdo1
       9       8      241        7      spare rebuilding   /dev/sdp1

       8      65       33        -      spare   /dev/sds1

```

---

### Post by fjgaude on 2008-09-05
The only thing I wouldn't have done was to add a drive into /dev/md1 while it is creating itself...

---

### Post by trmentry on 2008-09-05
> **fjgaude said:**
> The only thing I wouldn't have done was to add a drive into /dev/md1 while it is creating itself...

yeah... I'm thinking that as well. :(

any ideas on the 'phantom' md0?

```

root@hoth:~# mdadm --examine --scan
ARRAY /dev/md0 level=raid5 num-devices=7 UUID=c08f16fe:f0fb7dec:44e33c5a:20ebc66f
   spares=1
ARRAY /dev/md0 level=raid5 num-devices=8 UUID=a3ea7714:de2bf962:98512988:9ff2ba5b
   spares=1
ARRAY /dev/md1 level=raid5 num-devices=8 UUID=e0fccd56:52b6dfc6:98512988:9ff2ba5b
   spares=2

```
thanks

---

### Post by fjgaude on 2008-09-05
Not really... but after all is done with sync-up, I'd delete the mdadm.conf file, uninstall mdadm, reboot the machine, and then re-install mdadm. Then run this command:

```
sudo mdadm --assemble --scan
```

Then look at the auto created mdadm.conf file.

---

### Post by trmentry on 2008-09-05
> **fjgaude said:**
> Not really... but after all is done with sync-up, I'd delete the mdadm.conf file, uninstall mdadm, reboot the machine, and then re-install mdadm. Then run this command:

```
sudo mdadm --assemble --scan
```

Then look at the auto created mdadm.conf file.

*cough*  is this safe?  I hate to ask, as I have no where to back up all my data to now that I've put it all on this server... i really dont' want the arrays to go POOF

---

### Post by fjgaude on 2008-09-05
Yes, it is safe... I've done it a dozen or more times.

If you wish you can instead of deleting the mdadm.conf file just rename it, or move it to your home directory.

What you never wish to do is --build or --create a good array. Or fsck a mounted array or drive of an array.

Remember the UUID of an array you see in the .config file is the same for all the UUIDs of each drive in the array. So if you know the UUID of the drives in your good array, then you can delete or comment-out the line in the ARRAY file you know that is not the good array.

What I suggested is a quick way to see what is really good, the new .config file will show this.

Do what you are confortable doing... but I tell you like so many others, always have at least two full backups of important data. I have three, online, near-line, and off-line, it's that important.

---

### Post by trmentry on 2008-09-05
> **fjgaude said:**
> Yes, it is safe... I've done it a dozen or more times.

If you wish you can instead of deleting the mdadm.conf file just rename it, or move it to your home directory.

What you never wish to do is --build or --create a good array. Or fsck a mounted array or drive of an array.

Remember the UUID of an array you see in the .config file is the same for all the UUIDs of each drive in the array. So if you know the UUID of the drives in your good array, then you can delete or comment-out the line in the ARRAY file you know that is not the good array.

What I suggested is a quick way to see what is really good, the new .config file will show this.

Do what you are confortable doing... but I tell you like so many others, always have at least two full backups of important data. I have three, online, near-line, and off-line, it's that important.


these are the 2 statements in my mdadm.conf file but I put these here.

```

ARRAY /dev/md0 level=raid5 num-devices=8 spares=1 UUID=a3ea7714:de2bf962:98512988:9ff2ba5b
ARRAY /dev/md1 level=raid5 num-devices=8 spares=1 UUID=e0fccd56:52b6dfc6:98512988:9ff2ba5b

```

I got this by doing the --examine --scan thing.  But then verified with the

mdadm --detail /dev/md$x  

So I know that phantom uuid isn't valid... jsut wasn't sure how it was picking that up or why.

I'm guessing this wont' affect LVM2 that I have running as well on the these arrays.

Each array is a pv.

```

root@hoth:/etc/mdadm# pvs
  PV         VG       Fmt  Attr PSize PFree
  /dev/md0   hoth-vg0 lvm2 a-   3.18T      0
  /dev/md1   hoth-vg1 lvm2 a-   2.55T 584.26G

```

I'm guessing that by purging mdadm and reboot, obviously the lvm2 mounts won't mount as they aren't there.  Then put mdadm back in and start the arrays back up, lvm should be happy once again.

---

### Post by fjgaude on 2008-09-05
I'm no user of LVMs... so good luck.

---

### Post by trmentry on 2008-09-10
Ok... I completed screwed up and borked my arrays.  Oh well, at least I had things moved over to another machine that looks like Frankenstein.  LOL

Anyway... I still get this 'phantom' array.

I used DBAN to DoD wipe all hard drives for 1 hour.  Granted that wouldn't get all of the space on them but would at least get the MBRs and other info up there.

I then did a complete fresh install of 8.04.1 server.  I installed mdadm and it sees this:

```

root@hoth:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdi[0] sdk[7](S) sdo[6] sdn[5] sdp[4] sdm[3] sdl[2] sdj[1]
      2344267776 blocks level 5, 64k chunk, algorithm 2 [7/7] [UUUUUUU]

unused devices: <none>
root@hoth:~#
root@hoth:~# mdadm --examine --scan
ARRAY /dev/md0 level=raid5 num-devices=7 UUID=c08f16fe:f0fb7dec:44e33c5a:20ebc66f
   spares=1

```


I've not done anything to get this array going... so it's picking it up from somewhere.

I've tried to mdadm --stop /dev/md0 and then mdadm --zero-superblock --force /dev/sd[ijklmnop]  
but it says it can't open the drive to write.  

I'm really at a loss as to where this superblock is coming from and why DBAN didn't wipe it out.  And why --zero-superblock isn't working either.


I'm not against using this array as is.  I can just add the missing 8th drive into the mix.. er... 9th... but i've been told using the drive itself instead of a partition is bad.  ie
/dev/sda = bad  /dev/sda1 = good.  but not exactly sure on that.

Any ideas why I can't destroy this superblock that seems to be very persistent in sticking around?

Thanks

---

### Post by trmentry on 2008-09-10
whoohoo!  Got it wiped out.  

So the phantom array came up with 7 devices and 1 spare.  I added that spare in as a drive in the array.  

It started to grow the array.

About 30 min later... I stopped the array and did a --zero-superblock --force on all the drives.

This time it took, and wiped out all blocks.  I rebooted my server and when I do a mdadm --examine --scan... it comes up with no blocks found.  

Now to get the arrays rebuilt.

---

### Post by fjgaude on 2008-09-10
Go for it, man!

Let the array finish building before you install a filesystem to it.

---

### Post by trmentry on 2008-09-11
> **fjgaude said:**
> Go for it, man!

Let the array finish building before you install a filesystem to it.

Yup.  Array finished building and I put a FS on it.  I'm giving up on the LVM stuff, added too much to worry about, but was slick and worked well.  

So now I just have my 2 big ol' arrays.  And I have robocopy going from my frankenstein gaming rig to get the data back.  But I did lose some data, but that is why I bought [Crashplan](http://www.crashplan.com).  Crashplan rocks!  It's restoring my missing stuff that was in my /home directory from my buddies server in MO. :)

```

/dev/md0              3.2T  442G  2.8T  14% /raid/md0
/dev/md1              2.6T   12G  2.6T   1% /raid/md1

```

It's kinda zen like to lose the data.  I get to arrange things in a better way, better organized. :)

---

### Post by fjgaude on 2008-09-12
As we live each day, we learn something new, eh?

---

