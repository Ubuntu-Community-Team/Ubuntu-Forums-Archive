---
title: "raid5 array keeps losing disks"
date: 2011-10-04
forum: Server Platforms
---

### Post by davidmaxwaterman on 2011-10-04
it was fine for a while, but it has started losing track of its disks again.

it always happens at boot time, and it seems like they aren't there when the array assembly is attempted.

well, it has happened twice recently, first it lost two disks, and most recently lost all three. each time, i stop the array and reassemble the array. this means i have to wait while it sorts out the third one which takes ages. from experience, if i don't wait, and it fails again at the next boot, i'll have lost the array.

yes, a month or so ago, i lost the contents and had to restore from backup, which meant losing some recent stuff - nothing huge, but anyway...so there is something basically wrong.

i'm using 11.04, and the system is on a two disk raid1, which isn't having any trouble.

the blkids of the disks look fine.

any clues?

max.

---

### Post by Vegan on 2011-10-04
by any chance are you using the low cost eco-green type disks?

---

### Post by davidmaxwaterman on 2011-10-04
> **Vegan said:**
> by any chance are you using the low cost eco-green type disks?

Hrm, I think I might be. These are the models from Disk Utility :

WDC WD10EACS
WDC WD10EARS
WDC WD10EARS

Why?

Hrm, perhaps this : [http://wdc.custhelp.com/app/answers/detail/a_id/1397](http://wdc.custhelp.com/app/answers/detail/a_id/1397)

---

### Post by davidmaxwaterman on 2011-10-04
> **Vegan said:**
> by any chance are you using the low cost eco-green type disks?

Wow. Taking your post as a prompt, I did an internet search and it turned up all this stuff about TLER :/

Seems I'm quite screwed, but perhaps one sign of hope is the WDTLER utility - if I can find a copy, I'll give it a try.

---

### Post by a2j on 2011-10-05
1. make sure that disks are healthy
2. there is nothing wrong with using "low cost eco-green type" disks. Its not the disks, its the user.

ps: my wd15ears working fine in raid10 and raid6 for while now.

---

### Post by rubylaser on 2011-10-05
What do you have in your /etc/mdadm/mdadm.conf file
```
cat /etc/mdadm/mdadm.conf
```
and what's the output of
```
cat /proc/mdstat
```

---

### Post by davidmaxwaterman on 2011-10-06
> **a2j said:**
> 1. make sure that disks are healthy
2. there is nothing wrong with using "low cost eco-green type" disks. Its not the disks, its the user.

ps: my wd15ears working fine in raid10 and raid6 for while now.

While it's more than likely that "it's the user", note that I've been running a RAID5 array for several years with no problems - it's only when I switch to using these disks that I see this odd problem. Also, the symptoms are just too spot on to ignore. Also, it is clear to me from my searches on the internet that there are many others with this same problem, so I'm not sure how it can be said that they don't exist...

Still, I'm having problem creating a bootable DOS usb disk in order to run the WDTLER command, so perhaps checking 'user' error is a good way to go for now.

---

### Post by a2j on 2011-10-06
some of mine I got used, some new. I just made sure that they are formatted to match their advanced format feature and they been rocking and/or rolling without any issues. Can't complain. I actually do get good read/write speeds for those 5400rpm drives.

---

### Post by davidmaxwaterman on 2011-10-06
> **a2j said:**
> some of mine I got used, some new. I just made sure that they are formatted to match their advanced format feature and they been rocking and/or rolling without any issues. Can't complain. I actually do get good read/write speeds for those 5400rpm drives.

could you elaborate on this 'advanced format feature'?

Max.

---

### Post by davidmaxwaterman on 2011-10-06
> **rubylaser said:**
> What do you have in your /etc/mdadm/mdadm.conf file
```
cat /etc/mdadm/mdadm.conf
```
and what's the output of
```
cat /proc/mdstat
```

Here you go. Let me know if you can see anything wrong.

FWIW, I have the mount commented out of /etc/fstab, and also from mdadm.conf. I only uncomment it once the system has booted, since the only failures occur during boot time (from experience).

The relevant devices are md0 and sd[cde]1

```

root@jeeves:~# cat /etc/mdadm/mdadm.conf 
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR davidmaxwaterman@localhost

# definitions of existing MD arrays
ARRAY /dev/md0 metadata=1.2 name=jeeves:0 UUID=8c393e41:9a601b0f:16a001d4:3ea08c15
ARRAY /dev/md1 metadata=1.2 name=ubuntu:1 UUID=cf7dc75b:2960d15c:cfa04014:63e1c0a4

root@jeeves:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda1[2] sdb1[0]
      78147065 blocks super 1.2 [2/2] [UU]
      
md0 : active raid5 sde1[3] sdd1[1] sdc1[4]
      1953389568 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
root@jeeves:~# blkid
/dev/sda1: UUID="cf7dc75b-2960-d15c-cfa0-401463e1c0a4" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/sdc1: UUID="8c393e41-9a60-1b0f-16a0-01d43ea08c15" LABEL="jeeves:0" TYPE="linux_raid_member" 
/dev/sdb1: UUID="cf7dc75b-2960-d15c-cfa0-401463e1c0a4" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/sdd1: UUID="8c393e41-9a60-1b0f-16a0-01d43ea08c15" LABEL="jeeves:0" TYPE="linux_raid_member" 
/dev/sde1: UUID="8c393e41-9a60-1b0f-16a0-01d43ea08c15" LABEL="jeeves:0" TYPE="linux_raid_member" 
/dev/md0: LABEL="array" UUID="4854a251-7e33-437f-9875-d87eb08cd52b" TYPE="ext4" 
/dev/md1: UUID="2Zxdfy-pQOv-tuFl-beGD-3QqZ-NyJW-NPWGQW" TYPE="LVM2_member" 
/dev/mapper/server-root: UUID="8deb8591-2ffb-4fbc-9953-692ae284d34a" TYPE="ext4" 
/dev/mapper/server-swap: UUID="90e8572f-07f5-4163-9beb-18b945932ebc" TYPE="swap" 
root@jeeves:~# 

```

---

### Post by davidmaxwaterman on 2011-10-06
> **davidmaxwaterman said:**
> Wow. Taking your post as a prompt, I did an internet search and it turned up all this stuff about TLER :/

Seems I'm quite screwed, but perhaps one sign of hope is the WDTLER utility - if I can find a copy, I'll give it a try.

FWIW, I have been informed :

"NOTE: the WDTLER.EXE tool is no longer available from Western Digital. WD phone support confirmed that new disks cannot have the TLER setting changed, i.e. RE disks are only suitable for RAID arrays and Caviar are only suitable for non-RAID use. WD also say that using the WDTLER.EXE tool on newer drives can damage the firmware and make the disk unusable."

I'm not entirely sure if my disks qualify as 'new' or not, but I guess so :/

---

### Post by a2j on 2011-10-07
> **davidmaxwaterman said:**
> could you elaborate on this 'advanced format feature'?

Max.

[Advanced_Format]("http://en.wikipedia.org/wiki/Advanced_Format")

by default, Linux will format drives starting at block 63, all you have to do is format those drives starting at block 64.

---

### Post by davidmaxwaterman on 2011-10-08
> **a2j said:**
> [Advanced_Format]("http://en.wikipedia.org/wiki/Advanced_Format")

by default, Linux will format drives starting at block 63, all you have to do is format those drives starting at block 64.

Here are my disks :

```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000baad0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               9      121602   976696320   fd  Linux RAID autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0002df6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               9      121602   976696320   fd  Linux RAID autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000762f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               9      121602   976696320   fd  Linux RAID autodetect


```

The partitions are all the same, but I notice the 'Sector size' lines have some differences - ie sdc has physical sector size of 512, while sd[de] have physical sector size of 4096.

Do you recommend me to change the partitions to start at 64 then? I have a backup going at the moment in anticipation.

One other thing - does anyone know how to stop the OS attempting to start an array when it boots? I had thought that taking it out of mdadm.conf and fstab would be enough, but it seems not. I only have a problem at boot time, so I would like to make sure I stop it trying to do that.

---

### Post by davidmaxwaterman on 2011-10-08
> **davidmaxwaterman said:**
> 
Do you recommend me to change the partitions to start at 64 then? I have a backup going at the moment in anticipation.


Backup is done, so I figured I'd have a play.

fdisk complains if I use '64' as the 'Start'. Anyway, I noticed that you said 'Block 64', while fdisk says 'cylinder', but I don't see any way to specify it in blocks.

So, I tried some other values and ended up with 513 - that stopped it from complaining that it was 512 bytes offset (or something like that) :

```
/dev/sdc1             513      121601   972647392+  fd  Linux RAID autodetect
```

This seems to be working for the most part. I did the 'mdadm --create', 'mkfs.ext4', 'update-initramfs -u' and updated mdadm.conf and fstab accordingly.

It was, of course, rebuilding the array, but I've rebooted several times and it seems to hold together just fine.

I've not copied anything onto the array from backup yet.

Let me know if you have any other suggestions...

---

### Post by rubylaser on 2011-10-08
Here's an article by IBM that shows you how to get proper alignment on an Advanced Format drive.
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-twtr4KB-Disksdth-LX]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-twtr4KB-Disksdth-LX")

This wouldn't be causing the disks to dropout though.  It only makes them perform slower.

---

### Post by a2j on 2011-10-10
was issue there from the beginning (fresh install)? or just started happening? 
have you tried this?
```
mdadm --detail --scan > /etc/mdadm.conf
```

---

### Post by Krupski on 2011-10-10
> **davidmaxwaterman said:**
> it was fine for a while, but it has started losing track of its disks again.

it always happens at boot time, and it seems like they aren't there when the array assembly is attempted.

I had all kinds of grief with a 6 drive, RAID-6 server using 6 WD green 2TB drives.

But it wasn't the drives that were the problem. My clue came from DMESG entries where sometimes the same two drives would only come up at 1.5 speed instead of 3.0 (I suspected the SATA cables).

I bought 6 new SATA cables (super duper ones... shielded, with metal latches, ad-nauseaum) and all my problems went away.

Each drive is detected at full speed and drives are no longer falling off the array.

For what it's worth..... check the SATA cables.

-- Roger

---

### Post by davidmaxwaterman on 2011-10-11
> **Krupski said:**
> I had all kinds of grief with a 6 drive, RAID-6 server using 6 WD green 2TB drives.

But it wasn't the drives that were the problem. My clue came from DMESG entries where sometimes the same two drives would only come up at 1.5 speed instead of 3.0 (I suspected the SATA cables).

I bought 6 new SATA cables (super duper ones... shielded, with metal latches, ad-nauseaum) and all my problems went away.

Each drive is detected at full speed and drives are no longer falling off the array.

For what it's worth..... check the SATA cables.

-- Roger

OK, thanks! I have plenty of sata cables, so I'll try some different ones.

I don't suppose you have an example of the dmesg output?

Max.

---

### Post by davidmaxwaterman on 2011-10-18
> **davidmaxwaterman said:**
> OK, thanks! I have plenty of sata cables, so I'll try some different ones.


I tried some different ones, but it still fails.

It is a 3 disk RAID5. When on disk fails, I have trouble re-adding it to the array without it having to rebuild, which is painfully slow, but when two disks fail, I can assemble the array immediately after rebooting. So, somewhat ironically, it is better when more disks fail (none failing works too, of course).

> 
I don't suppose you have an example of the dmesg output?


I suppose these are the relevant lines in dmesg :

```
[    3.615805] md: bind<sde1>
[    3.694614] md: raid6 personality registered for level 6
[    3.694667] md: raid5 personality registered for level 5
[    3.694715] md: raid4 personality registered for level 4
[    3.703061] md: raid10 personality registered for level 10
[    3.788653] md/raid:md0: device sde1 operational as raid disk 2
[    3.789059] md/raid:md0: allocated 3179kB
[    3.789385] md/raid:md0: not enough operational devices (2/3 failed)
[    3.789677] md/raid:md0: failed to run raid set.
[    3.789725] md: pers->run() failed ...
[  119.244203] md: md0 stopped.
[  119.244222] md: unbind<sde1>
[  119.256081] md: export_rdev(sde1)
[  127.583467] md: md0 stopped.
[  127.592414] md: bind<sdd1>
[  127.592634] md: bind<sde1>
[  127.592823] md: bind<sdc1>
[  127.619271] md/raid:md0: device sdc1 operational as raid disk 0
[  127.619271] md/raid:md0: device sde1 operational as raid disk 2
[  127.619271] md/raid:md0: device sdd1 operational as raid disk 1
[  127.619271] md/raid:md0: allocated 3179kB
[  127.619271] md/raid:md0: raid level 5 active with 3 out of 3 devices, algorithm 2
[  127.619271] md0: detected capacity change from 0 to 1993832660992
[  127.655497]  md0: unknown partition table

```

Note at 127..that's where I manually stopped the array (though it was already stopped, it seems), and then did an --assemble --scan, and the array came up normally.

Is there no way to make mdadm just wait longer?

---

### Post by davidmaxwaterman on 2012-07-09
> **davidmaxwaterman said:**
> 
Is there no way to make mdadm just wait longer?

FWIW, I ended up taking the mount out of fstab, and then, after booting, manually checking the array, and if it had missing devices just stopping and starting it again would make it complete, and I would then mount it manually.

However, since upgrading to Ubuntu 12.04, every time I have manually checked the array, it has had all three devices on it - ie it hasn't ever seen the same problem. So, I think I'm ready to re-add it to fstab and see how we go.

I wonder what changed from 11.10 to 12.04 :/ I can't think it was anything that *I* did, though it might have been, of course.

---

