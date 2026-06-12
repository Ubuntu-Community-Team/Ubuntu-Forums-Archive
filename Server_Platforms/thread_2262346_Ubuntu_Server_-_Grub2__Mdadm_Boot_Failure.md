---
title: "Ubuntu Server - Grub2 / Mdadm Boot Failure"
date: 2015-01-24
forum: Server Platforms
---

### Post by ian77 on 2015-01-24
Hello and thank you in advance for any assistance with this problem I am experiencing.

I made the switch to Linux a few years ago and I am comfortable with the basics and can muddle my way through more complex tasks with the help of this excellent forum and its members. This is the first real issue I have expereinced as a Linux user that I am really struggling to resolve.

I think the issue is do with GRUB. I struggle to understand GRUB and the way Linux boots so hopefully I will learn something off the back of this problem. :)

[SIZE=4]**System Overview**[/SIZE]

Home server running Ubuntu Server 14.04. Main usage is a file server.
Running a software RAID 5 configuration using mdadm.
File system is btfs (can't recall exact version, but believe it's v3.x)

Had been working flawlessly untill I expanded my RAID array

[SIZE=4]**Problem Overview**[/SIZE]

I believe I have caused this issue by incorrectly expanding my RAID capacity by adding an extra disk to the array.

I originally built the server with 3 x 1TB drives in a raid 5 config, and it had been working for 6 months with no issues.
I needed extra capacity, so I decided to expand my array to 4 disks (adding an extra 1TB disk).

I followed a guide (on here I believe) but I didn't take into account the fact that I booted from my raid array.

- I formatted the disk
- I added the disk to the array (/dev/sdc)
- I expanded the file system onto the disk

All appeared fine with an extra 1TB or so, of storage.
[I]
**The server was working fine till I rebooted my server (for a separate reason) and now it won't boot correctly.**[/I]

It falls into a Grub Rescue> console complaining of:

> error: disk 'mduuid/3a42b2e9:3a1c1fd3:29475f88:aa4aafd3' not found

[B][SIZE=4]Assumed Cause[/SIZE]
[/B]
I assume I have caused this problem by two possible reasons:

- I have not ran a Grub-Update or installed grub to the new hard drive in the array
- I did not partition the new disk the same as the existing disk; i.e there's no swap partition on the new disk. (i forgot all about it)

[SIZE=4]**Troubleshooting**[/SIZE]

I am able to boot into a live-CD and I am able to bring the array online, and access the data:

> mint ~ # mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu Jun 12 20:23:34 2014
     Raid Level : raid5
     Array Size : 2923430400 (2788.00 GiB 2993.59 GB)
  Used Dev Size : 974476800 (929.33 GiB 997.86 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Sat Jan 24 11:55:05 2015
          State : clean, degraded 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : biscuit:0
           UUID : 3a42b2e9:3a1c1fd3:29475f88:aa4aafd3
         Events : 4628

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1
       2       8       49        2      active sync   /dev/sdd1
       3       0        0        3      removed



As you can see, the array is degraded and the new disk I added (/dev/sdc) has been removed.

Verbose output from when I assembled the array:

> mint ~ # mdadm --assemble --scan -v
mdadm: looking for devices for /dev/md/0
mdadm: no RAID superblock on /dev/sde1
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd2 has wrong uuid.
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb2 has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sr0
mdadm: /dev/sda2 has wrong uuid.
mdadm: no RAID superblock on /dev/sda
mdadm: no RAID superblock on /dev/loop0
mdadm: /dev/sdd1 is identified as a member of /dev/md/0, slot 2.
mdadm: /dev/sdb1 is identified as a member of /dev/md/0, slot 0.
mdadm: /dev/sda1 is identified as a member of /dev/md/0, slot 1.
mdadm: added /dev/sda1 to /dev/md/0 as 1
mdadm: added /dev/sdd1 to /dev/md/0 as 2
mdadm: no uptodate device for slot 3 of /dev/md/0
mdadm: added /dev/sdb1 to /dev/md/0 as 0
mdadm: /dev/md/0 has been started with 3 drives (out of 4).
mdadm: looking for devices for /dev/md/1
mdadm: no RAID superblock on /dev/md/0
mdadm: no RAID superblock on /dev/sde1
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sr0
mdadm: /dev/sda1 has wrong uuid.
mdadm: no RAID superblock on /dev/sda
mdadm: no RAID superblock on /dev/loop0
mdadm: /dev/sdd2 is identified as a member of /dev/md/1, slot 2.
mdadm: /dev/sdb2 is identified as a member of /dev/md/1, slot 0.
mdadm: /dev/sda2 is identified as a member of /dev/md/1, slot 1.
mdadm: added /dev/sda2 to /dev/md/1 as 1
mdadm: added /dev/sdd2 to /dev/md/1 as 2
mdadm: added /dev/sdb2 to /dev/md/1 as 0
mdadm: /dev/md/1 has been started with 3 drives

You can see how /dev/sdc is not partitioned correctly and mdadm doesn't like it.

[B]Hard Disk Paritioning
[/B]
This is how everything is partitioned. sda,sdb and sdd  are all original array members.
md0 is the root partition and md1 is the swap partition.

> mint ~ # lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda       8:0    0 931.5G  0 disk  
&#9500;&#9472;sda1    8:1    0 929.5G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   2.7T  0 raid5 
&#9492;&#9472;sda2    8:2    0   2.1G  0 part  
  &#9492;&#9472;md1   9:1    0   4.1G  0 raid5 
sdb       8:16   0 931.5G  0 disk  
&#9500;&#9472;sdb1    8:17   0 929.5G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   2.7T  0 raid5 
&#9492;&#9472;sdb2    8:18   0   2.1G  0 part  
  &#9492;&#9472;md1   9:1    0   4.1G  0 raid5 
sdc       8:32   0 931.5G  0 disk  
sdd       8:48   0 931.5G  0 disk  
&#9500;&#9472;sdd1    8:49   0 929.5G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   2.7T  0 raid5 
&#9492;&#9472;sdd2    8:50   0   2.1G  0 part  
  &#9492;&#9472;md1   9:1    0   4.1G  0 raid5 
sde       8:64   0 465.8G  0 disk  
&#9492;&#9472;sde1    8:65   0 465.8G  0 part  
sr0      11:0    1   1.4G  0 rom   /cdrom
loop0     7:0    0   1.4G  1 loop  /rofs

output from blkid:

> /dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="**3a42b2e9-3a1c-1fd3-2947-****5f88aa4aafd3**" UUID_SUB="2fbabaae-a94d-22c6-7fd3-56dd5153867e" LABEL="biscuit:0" TYPE="linux_raid_member" 
/dev/sda2: UUID="d51dfead-4362-67e5-e2b7-a5d0c26fcee8" UUID_SUB="472d3163-fc34-e721-3027-abedcb24dc08" LABEL="biscuit:1" TYPE="linux_raid_member" 
/dev/sr0: LABEL="Linux Mint 17 KDE 64-bit" TYPE="iso9660" 
/dev/sdb1: UUID="**3a42b2e9-3a1c-1fd3-2947-5f88aa4aafd3**" UUID_SUB="3609e1f8-f606-f581-0404-87bf57fed3ea" LABEL="biscuit:0" TYPE="linux_raid_member" 
/dev/sdb2: UUID="d51dfead-4362-67e5-e2b7-a5d0c26fcee8" UUID_SUB="1d55c4ff-be0c-e175-d233-df3c18918715" LABEL="biscuit:1" TYPE="linux_raid_member" 
/dev/sdc: UUID="8e184084-7a9d-4b95-8b5d-afc7d5d81217" UUID_SUB="5033d062-d30e-4fc3-9ad1-b03c386e7e59" TYPE="btrfs" 
/dev/sdd1: UUID="**3a42b2e9-3a1c-1fd3-2947-5f88aa4aafd3**" UUID_SUB="5acf048f-020a-27da-64ae-02f7deba80c0" LABEL="biscuit:0" TYPE="linux_raid_member" 
/dev/sdd2: UUID="d51dfead-4362-67e5-e2b7-a5d0c26fcee8" UUID_SUB="7dce9754-6e03-406f-6b78-031b24c5a23f" LABEL="biscuit:1" TYPE="linux_raid_member" 
/dev/sde1: UUID="0a2e8147-f55e-4879-a78c-e8906c67e446" TYPE="ext4" 
/dev/md0: UUID="01277aba-2d4f-4bb5-bb11-b47c8d74194f" UUID_SUB="ac6b9a83-be75-4444-9d3d-3c8607b5df11" TYPE="btrfs" 
/dev/md1: UUID="84e2659e-f35f-4ed6-a846-fbb6e85f93bb" TYPE="swap" 



So, I interpret this as GRUB trying to boot from the root partition of any of the member disks. Which is what I would expect. 
But obviosuly it's failing and I don't understand why

**Grub Config**

I wont' paste the full file, but looking at the grub config all the UUID's are like this:

> set root='mduuid/3a42b2e93a1c1fd329475f88aa4aafd3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='**mduuid/3a42b2e93a1c1fd329475f88aa4aafd3**'  01277aba-2d4f-4bb5-bb11-b47c8d74194f
else
  search --no-floppy --fs-uuid --set=root 01277aba-2d4f-4bb5-bb11-b47c8d74194f
fi
    font="/@/usr/share/grub/unicode.pf2"



**Disk Removal**

Even if I unplug the new hard drive from the machine and try and boot, I get the same error.
I assumed it would be resilient and boot in degraded mode.
[B][SIZE=4]
Summary[/SIZE][/B]


- The filesystem is btrfs
- Recently added new disk (/dev/sdc) to existing RAID 5 array
- 3 disks to 4 disks
- Working until reboot
- new disk not formatted the same as existing disks (my fault)
- grub update or install not ran after inclusion of new disk
- I can boot into live-cd, install mdadm and assemble the array in a degraded state
- the array doesn't like /dev/sdc 


I have clearly made some kind of mistake here and my lack of knowledge around GRUB and mdadm is preventing me from fixing it.


Hope someone can assist.

Cheers,

Ian

---

### Post by darkod on 2015-01-24
First, don't make any rush decisions. Few wrong moves could possibly destroy your data. On that subject, do you have a recent full backup of the whole 2TB (raid5 of 3x1TB gives 2TB total usable)?

Then, I noticed you said you formatted the disk and added it to the array. Do you mean really formatted or just created partition(s)? There is a difference.

To add a new disk (eaither to expand array or replace failed disk), you simply create the needed partitions on it. Ideally the partition sizes would be identical to the other array disks but it's not necessary. So, forgetting the swap plays no issue in this. Rule that out.

But you DO NOT format the partitions with a filesystem and then adding them to the array. In theory, it shouldn't hurt.

What you format is the /dev/mdX device, of course only the first time. The /dev/mdX holds the filesystem, not the /dev/sdXY.

Let me read some more of your post...

---

### Post by darkod on 2015-01-24
The fact that it refuses sdc right now is not worrying. The array is still clean, degraded.

What I am worried about is whether the reconfiguration from 3-disk raid5 to 4-disk raid5 was a success. But you say you can read the data. Reconfiguration changing the number of disks is always risky. And a lot of work for the OS rearranging the data, because the blocks split over 3 disks it has to rearrange over 4 disks now.

What is getting me worried is this part:
```
[COLOR=#000000]*mint ~ # mdadm --detail /dev/md0*[/COLOR]
[COLOR=#000000]*/dev/md0:*[/COLOR]
[COLOR=#000000]*Version : 1.2*[/COLOR]
[COLOR=#000000]*Creation Time : Thu Jun 12 20:23:34 2014*[/COLOR]
[COLOR=#000000]*Raid Level : raid5*[/COLOR]
[COLOR=#000000]*Array Size : 2923430400 (*[/COLOR][COLOR=#ff0000]*2788.00 GiB*[/COLOR][COLOR=#000000]* 2993.59 GB)*[/COLOR]
[COLOR=#000000]*Used Dev Size : 974476800 (*[/COLOR][COLOR=#ff0000]*929.33 GiB*[/COLOR][COLOR=#000000][I] 997.86 GB)
```

[/I][/COLOR]It seems your array is only using 1TB from the available 3TB. It shouldn't be like that.

Can you post the partitions of one old disk, and the new one. For example, the result of:
```
parted /dev/sda print
parted /dev/sdc print
```

---

### Post by ian77 on 2015-01-24
> **darkod said:**
> On that subject, do you have a recent full backup of the whole 2TB (raid5 of 3x1TB gives 2TB total usable)?

Only around 250GB is unique irreplacable data. All backed up onto /dev/sde.

> **darkod said:**
> 
Then, I noticed you said you formatted the disk and added it to the array. Do you mean really formatted or just created partition(s)? There is a difference.


/dev/sdc used to be my original backup drive with an ext4 file system. After transferring the data I just changed the filesystem from ext4 to btrfs (as you said, not necessary for RAID)
I can't recall the exact steps I performed.


**Update-Grub**

What I have been trying to do since I posted is update or re-install GRUB.

I booted to live-CD, assembled the array /dev/md0 and /dev/md1. 
- Then mounted /dev/md0 to /mnt. 
- Then mounted the virtual filesystem. 
- Then chroot /mnt.

At this point I tried a "update-grub" but i fails with an error:

> /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)

I can ls on the entire / partition and permissions are all normal. Similar error when I try an install too,
Should I be trying to install grub on the individual drives rather than the md0?

I'm out ideas and out of my depth here. (I'm a network guy :p)

I'll wait for someone more qualified to suggest an approach instead of trying to guess my way though.

Cheers

---

### Post by darkod on 2015-01-24
I guess you didn't see my last post. Please post the parted results.

---

### Post by ian77 on 2015-01-24
> **darkod said:**
> [COLOR=#000000][/COLOR]It seems your array is only using 1TB from the available 3TB. It shouldn't be like that.

Can you post the partitions of one old disk, and the new one. For example, the result of:
```
parted /dev/sda print
parted /dev/sdc print
```

Thanks. My filesystem can definately see 3TB

partitions:

> 

root@mint:/# parted /dev/sda print
Model: ATA Hitachi HUA72201 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  998GB   998GB   primary               raid
 2      998GB   1000GB  2204MB  primary               raid

> 
root@mint:/# parted /dev/sdc print
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB  btrfs



---

### Post by darkod on 2015-01-24
Well, I think you can see the difference yourself. Since sdc is not in the array currently and you don't need the data on it (you said it is already on sde so you changed filesystem on sdc), I suggest to make a new msdos table and identical partitions as on sda. After that to join it to the array. In fact, the current sdc table says loop device, you can see that clearly in the parted details.

I don't know how experienced you are with parted, but it should be like:
```
parted /dev/sda   (this will open the parted> prompt, the following commands are in that prompt)
unit MiB   (to change the units to MiB, I prefer working with them)
print   (to print the actual table of sda in MiB, note down the start and end of the partitions 1 and 2)
select /dev/sdc   (change the disk you are working with to /dev/sdc)
print   (CONFIRM it is sdc you are working with, from the data printed, if it is not the correct disk DO NOT continue with anything because you can mess up partitions on another array disk)
mklabel msdos   (new blank msdos partition table)
mkpart primary X Y   (create new primary partition starting at X ending at Y, use the start/end values of partition 1 of sda)
mkpart primary X Y   (the same for partition 2)
set 1 raid on   (set the raid flag on part. 1)
set 2 raid on   (same on 2)
quit   (quit parted)
```

Now sdc should be identical to the other array disks.

md0 seems already to be configured for 4 devices, after the reshape you did. So simply adding new partition (device) should make it start syncing.
```
mdadm /dev/md0 --add /dev/sdc1
```

Now check again the details of md0. If it says 4 disks and sdc1 syncing, let it finish.

---

### Post by ian77 on 2015-01-24
Cheers darkod. It's looking good.

> 
Update Time : Sat Jan 24 22:20:58 2015
          State : clean, degraded, recovering


Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1
       2       8       49        2      active sync   /dev/sdd1
       4       8       33        3      spare rebuilding   /dev/sdc1


cat /proc/mdstat:

> 
md0 : active raid5 sdc1[4] sdb1[0] sdd1[2] sda1[1]
      2923430400 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UUU_]
      [>....................]  recovery =  0.7% (7017408/974476800) finish=372.3min speed=43301K/sec


Will leave it to run over night and try and boot it tomorrow.

I am assuming I can also add the /dev/sdc2 device to /dev/md1 later?

---

### Post by darkod on 2015-01-24
Yes, add the sdc2 to md1 later. That will finish fast.

Note that the system might still not boot after this, but at least the array will be raid5 with all 4 members present. It's dangerous to keep it with a missing member for long since if something happens to another member, the array will fail.

Part of the problem might be that you decided to leave root on raid5 array which splits the files over disks. In the future try always using a smaller raid1 array for root. That way the files are not getting split. I remember reading somewhere that [COLOR=#ff0000]the boot files do not handle splitting well[/COLOR].

But in this case, to redo the whole thing you will need to copy root and the whole data, destroy current arrays, and create for example md0 of 15-20GB for root, bigger md1 for data, and md2 for swap (or you can have swap unraided, doesn't matter).

In case the synced array doesn't boot, we can try again reinstalling grub. The commands you did earlier are not exactly correct. But we will talk about that if and when needed.

PS. I searched little on google and it seems these days ubuntu has no problem booting from raid5 mdadm array. So the fact that you have such setup should not be a problem to boot.

---

### Post by darkod on 2015-01-24
Also, I just remembered that during mdadm initial configuration you can select whether to boot or not in degraded mode. If you selected not to boot the system in degraded, as soon as it went to degraded it stopped booting because of that. If that is the only issue, it should boot after it finishes the resync.

---

### Post by ian77 on 2015-01-25
Thanks for all your help so far!

I can confirm both /dev/md0 and /dev/md1 are fully rebuilt with 4 disks each.

However, when I try and boot the system I encounter the same error:

> error: disk 'mduuid/3a42b2e9:3a1c1fd3:29475f88:aa4aafd3' not found

:(


**Grub**

I have had a bit of a read of the Grub manual to try and further my limited understanding. It says "GRUB 2 can read files directly from LVM and RAID devices" so it should be able to read the /boot folder from my /dev/md0 disk.

It also says installing grub is as simple as:

```

grub-install /dev/hda

```

I followed this guide [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd) and mounted my file systems properly ready to repair or re-install grub.

After reading the man page, I assumed that a simple 


```

grub-install /dev/md0

```

would suffice, but this is what happens:

> 
root@mint:/# grub-install /dev/md0
Installing for i386-pc platform.
grub-install: error: cannot find a device for /boot/grub (is /dev mounted?)


but I can see my /boot folder fine
> 
root@mint:/# ls /boot/grub
fonts  gfxblacklist.txt  grub.cfg  grubenv  i386-pc  locale  unicode.pf2


Similar for an update
> 
root@mint:/# update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
root@mint:/#



I'm clearly guessing here. I await some further wisdom to be imparted :-)

---

### Post by darkod on 2015-01-25
You install grub on the physical disk MBR, not on the array device. So it would be like:
grub-install /dev/sda

The same for the other three disks, one by one. Better to have grub on all disks in raid because you never know which one will fail. And then you do the update-grub.

In the procedure you linked for chroot you did the --bind for /dev, /proc and /sys right? That is needed before you do the chroot.

Try again and post back.

---

### Post by ian77 on 2015-01-25
Yeah, done all the --bind bits before the chroot.

I tried to install grub on all of my disks as you described and I get the same error:

> 
grub-install: error: cannot find a device for /boot/grub (is /dev mounted?)


Everything appears mounted fine to me and the permissions seem fine too.

Cheers,

Ian

---

### Post by darkod on 2015-01-26
There is another shorter way to reinstall grub without the full chroot. You might give that a shot too.
You do it from the live mode only mounting root (in your case md0). You are using Mint live mode but it should still work I guess. The commands are:
```
mount /dev/md0 /mnt
grub-install --root-directory=/mnt /dev/sda
```

Try if that helps. Of course you need to assemble md0 first but you already know how to do that.

---

### Post by ian77 on 2015-01-26
Thanks darkod.

I was able to install grub as you described on every RAID disk apart from (you guessed it) /dev/sdc...

spits out this error:

> 
grub-install: warning: Attempting to install GRUB to a disk with multiple partition labels. This is not supported yet..
grub-install: error: embedding is not possible, but this is required for RAID and LVM install.


When I look at the partitions for all disks, they are all identical. 

I don't know what I've done to /dev/sdc to deserve this!! :mad: haha

---

### Post by darkod on 2015-01-26
Ok, leaving the issue with sdc aside, does the server boot by itself now after the grub reinstall? Or it still gives the uuid error?

---

### Post by ian77 on 2015-01-26
I am still running into the same error.

---

### Post by darkod on 2015-01-26
I am worried since the uuid seems correct, but grub is reporting the device missing. It might be only that the array is assembled delayed so grub doesn't find it on time. Sometimes introducing small delay in booting is enough for that.

But lets try completely removing and reinstalling grub first, as a desperate move. :)

I assume you have working internet connection in live mode. Do the bind chroot procedure again, and once in the chroot completely remove grub-pc and grub-common (to delete existing config), then reinstall grub-pc (grub-common should be installed automatically as dependency), and just in case run update-grub. If that works without errors, try installing it on all disks again too. So, in the chroot the commands would be:

```
apt-get purge grub-pc grub-common
apt-get install grub-pc
update-grub
grub-install /dev/sda
grub-install /dev/sdb
...
```

Close the chroot and reboot. Keep fingers crossed. :)

---

### Post by ian77 on 2015-01-26
Ok - done all that.

Grub was kicking out the same errors when I tried to re-install it under chroot. Telling me /dev isn't mounted, when it clearly is.

Installed via the other method which you suggested. As before, worked one every disk apart from /dev/sdc - giving me the same error as before.

I tried a reboot anyway. Same error on booting...


The system clearly doesn't like /dev/sdc for some reason. Do you think it's worth me failing and removing /dev/sdc from /dev/md0 and zeroing the disk, and then re-adding the disk as before, then try and re-install grub again?

Cheers


Ian

---

### Post by darkod on 2015-01-26
You can try fail remove and zeroing, but not sure it would help. In theory the new partition table you wrote before making the partitions should have done the same. And by removing it you will leave your array in degraded state. If another disk goes while you are "playing" with sdc you are in trouble. Although it helps that you have a full backup as you said you did.

I am starting to fish in the dark here, but we never tried updating the initramfs. You would have to do that from chroot though:
```
update-initramfs -u
update-grub
```

The decision about sdc I leave to you. See if initramfs helps first.

PS. Also you should try to run a filesystem check on md0. With ext4 you would use fsck (unmounted). Like:
```
fsck /dev/md0
```

I don't know how filesystem check works on btrfs.

---

### Post by ian77 on 2015-01-26
I don't think we are going to win this battle....

The system spits out yet another error when trying to run "update-initramfs -u"

> 
mdadm: cannot open /dev/md/0: No such file or directory



This time, it has a point. /dev/md/0 doesn't exist. I assume it should be a symlink to /dev/md0.

In the mdadm.conf file it specifies the array as /dev/md/0, so getting desperate a I changed it to /dev/md0 hoping it would be more accurate when trying to run the above command.
No luck.

I'm not sure how I would make a symlink in the /dev/ directory for /dev/md/0 - any ideas?


It's time like these I wish I had the time and money for a test rig :p

---

### Post by darkod on 2015-01-27
Hmmm, you shouldn't need to symlink that manually. I don't know why but when you create an array mdadm puts /dev/md/X in mdadm.conf even though you created the device /dev/mdX. But that is not stopping you use /dev/mdX and it works.
I am beginning to think the reshape/grow might have gone bad and that is the reason for all this. Do you remember if the reshape finished without any issues when growing to 4 disks? When exactly did sdc go missing, after the first reboot? Was it part of the array until then?

---

### Post by ian77 on 2015-01-27
> **darkod said:**
> Hmmm, you shouldn't need to symlink that manually. I don't know why but when you create an array mdadm puts /dev/md/X in mdadm.conf even though you created the device /dev/mdX. But that is not stopping you use /dev/mdX and it works.
I am beginning to think the reshape/grow might have gone bad and that is the reason for all this. Do you remember if the reshape finished without any issues when growing to 4 disks? When exactly did sdc go missing, after the first reboot? Was it part of the array until then?

The reshape seemed fine to me. No errors reported and no unusual activity.
SDC was dropped from the array when I re-assembled it when in a live-cd. Mdadm seemed to take it upon itself to do this automatically. Yes it was working as part of the array until this point.

Evidence from the logs suggest the mdadm expansion and btrfs expansion went without a hitch:

Disk added and detected on the evening of the 19th January.

> 
Jan 19 22:06:20 biscuit kernel: [    8.323658] sd 4:1:0:0: [sdc] Attached SCSI disk


Original RAID array comes up fine.

> Jan 19 22:06:20 biscuit kernel: [    9.246149] md/raid:md0: device sdb1 operational as raid disk 0
Jan 19 22:06:20 biscuit kernel: [    9.267187] md/raid:md0: device sdd1 operational as raid disk 2
Jan 19 22:06:20 biscuit kernel: [    9.287874] md/raid:md0: device sda1 operational as raid disk 1
Jan 19 22:06:20 biscuit kernel: [    9.309206] md/raid:md0: allocated 0kB
Jan 19 22:06:20 biscuit kernel: [    9.329286] md/raid:md0: raid level 5 active with 3 out of 3 devices, algorithm 2

This was reported, but Iassume this is normal? Obviously was working fine

> Jan 19 22:06:20 biscuit kernel: [    9.413761]  md0: unknown partition table

################################################################################
# Next morning I decide to grow the array before work, and allow it to resync during the day.##
################################################################################

I prepare the disk and mistakenly apply a btrfs filesystem to the disk. Which shouldn't hurt?

> Jan 20 08:09:13 biscuit kernel: [31625.795753] btrfs: device fsid 8e184084-7a9d-4b95-8b5d-afc7d5d81217 devid 1 transid 4 /dev/sdc

Looks like sdc is incorporated into the array here

> Jan 20 08:11:44 biscuit kernel: [31776.634378] md: bind<sdc1>



Re-shape takes place throughout the day and seems ok. All disks seen and capacity is expanded.
It complains about the reshape being interrupted, but doesn't seem bothered.

> Jan 20 08:12:21 biscuit kernel: [31813.900086]  --- level:5 rd:4 wd:4
Jan 20 08:12:21 biscuit kernel: [31813.900093]  disk 0, o:1, dev:sdb1
Jan 20 08:12:21 biscuit kernel: [31813.900097]  disk 1, o:1, dev:sda1
Jan 20 08:12:21 biscuit kernel: [31813.900102]  disk 2, o:1, dev:sdd1
Jan 20 08:12:21 biscuit kernel: [31813.900107]  disk 3, o:1, dev:sdc1
Jan 20 08:12:21 biscuit kernel: [31813.900261] md: reshape of RAID array md0
Jan 20 08:12:21 biscuit kernel: [31813.900275] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Jan  20 08:12:21 biscuit kernel: [31813.900281] md: using maximum available  idle IO bandwidth (but not more than 200000 KB/sec) for reshape.
Jan 20 08:12:21 biscuit kernel: [31813.900295] md: using 128k window, over a total of 974476800k.
Jan 20 08:12:21 biscuit kernel: [31813.982179] btrfs: device fsid 01277aba-2d4f-4bb5-bb11-b47c8d74194f devid 1 transid 491278 /dev/md0
**Jan 20 08:12:22 biscuit kernel: [31814.844500] md: md0: reshape interrupted.**
Jan 20 08:12:22 biscuit kernel: [31814.869507] md: reshape of RAID array md0
Jan 20 08:12:22 biscuit kernel: [31814.869517] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Jan  20 08:12:22 biscuit kernel: [31814.869523] md: using maximum available  idle IO bandwidth (but not more than 200000 KB/sec) for reshape.
Jan 20 08:12:22 biscuit kernel: [31814.869537] md: using 128k window, over a total of 974476800k.
Jan 20 18:02:57 biscuit kernel: [67249.846237] perf samples too long (10001 > 10000), lowering kernel.perf_event_max_sample_rate to 12500
Jan 20 19:49:14 biscuit kernel: [73627.008200] md: md0: reshape done.
Jan 20 19:49:15 biscuit kernel: [73628.097437] RAID conf printout:
Jan 20 19:49:15 biscuit kernel: [73628.097449]  --- level:5 rd:4 wd:4
Jan 20 19:49:15 biscuit kernel: [73628.097456]  disk 0, o:1, dev:sdb1
Jan 20 19:49:15 biscuit kernel: [73628.097460]  disk 1, o:1, dev:sda1
Jan 20 19:49:15 biscuit kernel: [73628.097465]  disk 2, o:1, dev:sdd1
Jan 20 19:49:15 biscuit kernel: [73628.097469]  disk 3, o:1, dev:sdc1
Jan 20 19:49:15 biscuit kernel: [73628.097480] md0: detected capacity change from 1995728486400 to 2993592729600


I then expand the btrfs filesystem to the size of the array. This was completed whilst the filesystem was online.

> Jan 20 20:10:09 biscuit kernel: [74881.992230] btrfs: new size for /dev/md0 is 2993592729600
Jan 20 20:15:26 biscuit kernel: [75198.687320] btrfs: relocating block group 1991820443648 flags 1
Jan 20 20:15:55 biscuit kernel: [75227.378305] btrfs: found 7 extents
Jan 20 20:15:58 biscuit kernel: [75230.419781] btrfs: found 7 extents
Jan 20 20:15:58 biscuit kernel: [75230.799069] btrfs: relocating block group 1990746701824 flags 1
... 

Then the system works fine till I shut it down on the evening of the 23rd

> Jan 23 20:16:52 biscuit kernel: [334484.551655] init: tty1 main process (1722) killed by TERM signal


Would not boot after this. And this post created on the 24th.
Nothing else reported in the kernel logs or syslogs. Boot.log doesn't complain of anything. Can't see any logs in /boot/grub.

Is there any other logs I can check apart from kernel, syslog, dmesg and boot in /var/log ?

The logs suggest the array and filesystem expansion went without a hitch. So I'm kind of leaning more towards the idea that I caused this by not installing grub on sdc (or run a grub update) properly before the reboot. But, I will wait to hear you wisdom before making any final judgements :)

Cheers,

Ian

---

### Post by darkod on 2015-01-27
Hmmm... Not only did you format sdc with btrfs which was not needed, it seems you did it on the whole disk, not a partition (like /dev/sdc1). There is definitely confusion between the results/logs. What you posted now from Jan 20th after the reshape says /dev/sdc1 is the fourth member (disk slot 3). But if you go back to your first post and the blkid results, they show only /dev/sdc and with btrfs filesystem on it. No mention of /dev/sdc1 like a partition at all.

If you applied filesystem on the whole disk as a device it might explain why parted reported the partition table as loop, not as msdos or gpt. Also it might be a reason why grub gets confused now, but I wouldn't know to explain that with facts. Just a hunch...

So your idea about zeroing sdc might actually help because it should wipe all "damage" previously done on the disk.

Another idea, depends if you like it, is simply redoing the whole setup. You said you had full backup of all important data. If that is really so, consider destroying this raid5 and installing from scratch with mirror raid1 for OS and raid5 for data. That way for the future at least your data is separate from your OS. But of course that depends how much configuration you would need to do if you reinstall. There is an option to copy the / now (without your big data that you already have backed up), and restore it on the newly created raid1. But that way it can carry over something from the old system and it might give you issues in future. Clean install avoids that.

---

### Post by ian77 on 2015-01-28
Firstly, I would like to sincerly thank you for your help with trying to resolve this issue. But I am going to admit defat in trying to repair the system.

I removed sdc from the array last night and zeroed it. This morning I partitioned the disk as we done previously, and grub installed without a hitch. 
I got really excited and then added the disk back into the array this morning and allowed it to rebuild during the day.

Returned home from work and everything looked fine.

I tried to run a grub-update (using the chroot method like before) but this failed with the same error. Complaining of dev not being mounted.....

Anyway, I was hopeful and rebooted the system.

But still did not not boot. Exact same error....


Oh well. Now rebuilding the server and will configure raid1 mirroring for the root partition and keep data on a seperate raid 5 or raid 4.

Cheers

Ian

---

### Post by slow2anger on 2015-12-09
I encountered this exact same error while trying to migrate a pre-existing non-RAID Ubuntu 14.04 system to software RAID with mdadm from a Ubuntu live CD.

The entire mdadm setup and Ubuntu migration have been successful until the very last step when I was trying to [FONT=courier new]grub-install /dev/sde[/FONT] and [FONT=courier new]grub-install /dev/sdf[/FONT].  (/dev/sde and /dev/sdf are my RAID hard disks.)

I turns out that I needed to zero-superblock /dev/sde and /dev/sdf.  This is probably due to previously installed mdadm RAID on these disks that somehow tenaciously sticks even after I created a new partition table and reformatted the disks.

In short, here was my fix. Of course change your /dev/sdX.  Hope it helps.

1. Create a dummy raid on /dev/sde and /dev/sdf with mdadm.
2. Stop the dummy raid.
3. madam --zero-superblock these two disks.  See [here]("http://ubuntuforums.org/showthread.php?t=884556") for details.
4. Create again a raid on /dev/sde and /dev/sdf with mdadm.  Move your actual OS and data onto this raid.
5. Now I was able to grub-install /dev/sd[ef] and update-grub without errors.

---

