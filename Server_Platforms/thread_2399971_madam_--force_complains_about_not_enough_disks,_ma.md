---
title: "madam --force complains about not enough disks, maybe event counter too far apart?"
date: 2018-08-31
forum: Server Platforms
---

### Post by lilrabbit129 on 2018-08-31
Hi Everyone,

I've done some searching, and haven't found anything exactly the same, and with this amount of data in jeopardy, I'd rather not just try some stuff without some question asking. 

So I have a 7-disk RAID5. Its a bit of a Frankenstein setup. Recently my SATA card decided it didnt want to work anymore and kicked out 2 of the HDs attached to it. The ones attached to the SATA ports on the MB were fine. But this caused my RAID5 to become unhappy. This has happened before and usually an --assemble --force would do the trick, but this time its complaining with "not enough disks". The output below:

```

sudo mdadm --verbose --assemble --force /dev/md127 /dev/sdf1 /dev/sdc1 /dev/sdb1 /dev/sdd1 /dev/sdg1 /dev/sde1 /dev/sdh1 

mdadm: looking for devices for /dev/md127
mdadm: /dev/sdf1 is identified as a member of /dev/md127, slot 0.
mdadm: /dev/sdc1 is identified as a member of /dev/md127, slot 1.
mdadm: /dev/sdb1 is identified as a member of /dev/md127, slot 2.
mdadm: /dev/sdd1 is identified as a member of /dev/md127, slot 3.
mdadm: /dev/sdg1 is identified as a member of /dev/md127, slot 4.
mdadm: /dev/sde1 is identified as a member of /dev/md127, slot 5.
mdadm: /dev/sdh1 is identified as a member of /dev/md127, slot 6.
mdadm: added /dev/sdc1 to /dev/md127 as 1
mdadm: added /dev/sdb1 to /dev/md127 as 2
mdadm: added /dev/sdd1 to /dev/md127 as 3
mdadm: added /dev/sdg1 to /dev/md127 as 4 (possibly out of date)
mdadm: added /dev/sde1 to /dev/md127 as 5
mdadm: added /dev/sdh1 to /dev/md127 as 6 (possibly out of date)
mdadm: added /dev/sdf1 to /dev/md127 as 0
mdadm: /dev/md127 assembled from 5 drives - not enough to start the array.

```

I'm thinking its because the Event counters are too far apart? 

```
         
         Events : 120796
         Events : 120796
         Events : 120796
         Events : 120796
         Events : 120796
         Events : 120788
         Events : 120788

```

The two lower ones being the drives kicked out. 

Here is a sample of a drive that wasn't kicked out:

```

/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : f21f5306:c8a07e60:fad3a920:52a40d5b
  Creation Time : Tue Dec 21 20:21:48 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 11721071616 (11178.09 GiB 12002.38 GB)
   Raid Devices : 7
  Total Devices : 5
Preferred Minor : 127

    Update Time : Thu Aug  9 23:39:20 2018
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 2
  Spare Devices : 0
       Checksum : ce567320 - correct
         Events : 120796

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       17        2      active sync   /dev/sdb1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       0        0        4      faulty removed
   5     5       8       65        5      active sync   /dev/sde1
   6     6       0        0        6      faulty removed

```

and one that was:

```

/dev/sdh1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : f21f5306:c8a07e60:fad3a920:52a40d5b
  Creation Time : Tue Dec 21 20:21:48 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 11721071616 (11178.09 GiB 12002.38 GB)
   Raid Devices : 7
  Total Devices : 7
Preferred Minor : 127

    Update Time : Thu Aug  9 23:31:29 2018
          State : clean
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0
       Checksum : ce567281 - correct
         Events : 120788

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8      113        6      active sync   /dev/sdh1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8       65        5      active sync   /dev/sde1
   6     6       8      113        6      active sync   /dev/sdh1

```

I have backups, but as is always the case, the backups filled up before the raid and so its a bit out of date. 

Any help would be greatly appreciated!

-Me

---

### Post by darkod on 2018-08-31
Hmmm, the events are so close that it should assemble. When the --assemble --force is not working (as you tried), the next thing to try is adding --run. Just run the same command adding the option --run too. Lets see if that helps.

---

### Post by lilrabbit129 on 2018-08-31
I just tried with --run and this was the output:

```

sudo mdadm --verbose --assemble --force --run /dev/md127 /dev/sdf1 /dev/sdc1 /dev/sdb1 /dev/sdd1 /dev/sdg1 /dev/sde1 /dev/sdh1
mdadm: looking for devices for /dev/md127
mdadm: /dev/sdf1 is identified as a member of /dev/md127, slot 0.
mdadm: /dev/sdc1 is identified as a member of /dev/md127, slot 1.
mdadm: /dev/sdb1 is identified as a member of /dev/md127, slot 2.
mdadm: /dev/sdd1 is identified as a member of /dev/md127, slot 3.
mdadm: /dev/sdg1 is identified as a member of /dev/md127, slot 4.
mdadm: /dev/sde1 is identified as a member of /dev/md127, slot 5.
mdadm: /dev/sdh1 is identified as a member of /dev/md127, slot 6.
mdadm: added /dev/sdc1 to /dev/md127 as 1
mdadm: added /dev/sdb1 to /dev/md127 as 2
mdadm: added /dev/sdd1 to /dev/md127 as 3
mdadm: added /dev/sdg1 to /dev/md127 as 4 (possibly out of date)
mdadm: added /dev/sde1 to /dev/md127 as 5
mdadm: added /dev/sdh1 to /dev/md127 as 6 (possibly out of date)
mdadm: added /dev/sdf1 to /dev/md127 as 0
mdadm: failed to RUN_ARRAY /dev/md127: Input/output error
mdadm: Not enough devices to start the array.

```

Sadly no joy

---

### Post by darkod on 2018-08-31
But if you notice the message has changed. In your first attempt it directly said it tried assembling from 5 drives which of course fails. In the second it tries to assemble them but giving I/O error.

Try googling that mdadm message "failed to RUN_ARRAY Input/output error".

Is it possible that some SATA controller is still giving you I/O issues?

---

### Post by lilrabbit129 on 2018-08-31
Hmm I had assumed that was because there wasn't enough drives ( so it couldn't start the array). I can try to check to makes sure each drive is still accessible. Any suggestions on how to do that? dmesg isn't spitting out any errors, and I have another disk (not in the array) off the same SATA card that I'm transferring stuff to ( not at the same time) to test and there's been no errors. 

Is there a more comprehensive way to test to make sure one of the drives isn't causing the Input/Output error?

I will do some googling for the RUN_ARRARY error. 

Thanks!

---

### Post by lilrabbit129 on 2018-09-04
Unfortunately I haven't made any progress. The individual drives check out fine with hdparm, and fdisk ( -l ). I'm not sure how else to check if they're "good". 

Are there any other options I can try?

Thanks.

---

### Post by darkod on 2018-09-04
The last thing is to try re-creating the array... You have the disk order in the output of the above assemble commands. Just be careful, you HAVE to use the parameter --assume-clean otherwise a new blank array will be created. With --assume-clean it doesn't delete the data.

You also have to use identical parameters as when creating the array. And the order of the disks in the --create command has to match the disk order (but you already know it from above so it won't be a problem).

So the command would be something like:
```
sudo mdadm --create --verbose --assume-clean --level=raid5 --raid-devices=7 /dev/md127 /dev/sdf1...
```

Double check the command, and that is the last thing to try. There should be no data loss especially since your Events are so close.

---

### Post by lilrabbit129 on 2018-09-04
Firstly, thanks for all the help Darko.

I have the command set-up ( sudo mdadm --create --verbose --assume-clean --level=raid5 --raid-devices=7 /dev/md127 /dev/sdf1 /dev/sdc1 /dev/sdb1 /dev/sdd1 /dev/sdg1 /dev/sde1 /dev/sdh1 ), but being a bit of a chicken, I'm doing some more research before pulling the trigger. 

I've read a bit about --assume-clean and using create to resurrect a failed raid. They mention something about chunk sizes and data offset, which change over time. Is that something I have to worry about? Can I somehow save that information off before performing this command?

I've saved the --examine output to a file, as well as triple checked that the drive ordering is right. 

Thanks,

---

### Post by darkod on 2018-09-04
You have the chuck size in the above superblock output:
```
Chunk Size : 64K
```

I think 64K is the default one so you don't need to specify it. But you can if you wish... And the data offset, I honestly have never seen it used. You most probably didn't set it up when creating the array so no need to worry about it now.

The assume clean helps keep the data, even if you get some parameter wrong. I've seen a guy doing those tests using different parameters on purpose. Of course, array created with different chuck will not mount (won't match), but you can re-create again over it and the data will be there... :)

I know it's scary but this command is your last option. That is why it is the last option... :)

---

### Post by lilrabbit129 on 2018-09-04
So this is the output I got after doing the command:

```
sudo mdadm --create --verbose --assume-clean --level=raid5 --raid-devices=7 --chunk=64 /dev/md127 /dev/sdf1 /dev/sdc1 /dev/sdb1 /dev/sdd1 /dev/sdg1 /dev/sde1 /dev/sdh1 
[sudo] password for rfeliciano: 
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdf1 appears to contain an ext2fs file system
       size=18446744068250754048K  mtime=Tue Jun  5 21:54:30 2018
mdadm: /dev/sdf1 appears to be part of a raid array:
       level=raid5 devices=7 ctime=Tue Dec 21 20:21:48 2010
mdadm: /dev/sdc1 appears to be part of a raid array:
       level=raid5 devices=7 ctime=Tue Dec 21 20:21:48 2010
mdadm: /dev/sdb1 appears to be part of a raid array:
       level=raid5 devices=7 ctime=Tue Dec 21 20:21:48 2010
mdadm: /dev/sdd1 appears to be part of a raid array:
       level=raid5 devices=7 ctime=Tue Dec 21 20:21:48 2010
mdadm: /dev/sdg1 appears to be part of a raid array:
       level=raid5 devices=7 ctime=Tue Dec 21 20:21:48 2010
mdadm: /dev/sde1 appears to be part of a raid array:
       level=raid5 devices=7 ctime=Tue Dec 21 20:21:48 2010
mdadm: /dev/sdh1 appears to contain an ext2fs file system
       size=18446744069244804100K  mtime=Mon Aug 21 00:48:43 2006
mdadm: /dev/sdh1 appears to be part of a raid array:
       level=raid5 devices=7 ctime=Tue Dec 21 20:21:48 2010
mdadm: size set to 1953380928K
mdadm: automatically enabling write-intent bitmap on large array

```

Here is what happened when I tried to mount:

```
sudo mount -o ro /dev/md127 /mnt/raid5/
mount: wrong fs type, bad option, bad superblock on /dev/md127,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

Here is the resulting dmesg

```
[404608.659110] md/raid:md127: device sdh1 operational as raid disk 6
[404608.659113] md/raid:md127: device sde1 operational as raid disk 5
[404608.659116] md/raid:md127: device sdg1 operational as raid disk 4
[404608.659118] md/raid:md127: device sdd1 operational as raid disk 3
[404608.659120] md/raid:md127: device sdb1 operational as raid disk 2
[404608.659122] md/raid:md127: device sdc1 operational as raid disk 1
[404608.659124] md/raid:md127: device sdf1 operational as raid disk 0
[404608.659775] md/raid:md127: allocated 7548kB
[404608.659809] md/raid:md127: raid level 5 active with 7 out of 7 devices, algorithm 2
[404608.659811] RAID conf printout:
[404608.659812]  --- level:5 rd:7 wd:7
[404608.659815]  disk 0, o:1, dev:sdf1
[404608.659817]  disk 1, o:1, dev:sdc1
[404608.659818]  disk 2, o:1, dev:sdb1
[404608.659820]  disk 3, o:1, dev:sdd1
[404608.659822]  disk 4, o:1, dev:sdg1
[404608.659824]  disk 5, o:1, dev:sde1
[404608.659826]  disk 6, o:1, dev:sdh1
[404608.659839] md127: Warning: Device sdb1 is misaligned
[404608.660057] created bitmap (15 pages) for device md127
[404608.661972] md127: bitmap initialized from disk: read 1 pages, set 29807 of 29807 bits
[404608.745259] md127: detected capacity change from 0 to 12001572421632
```

Here is the mdstat:

```
cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active raid5 sdh1[6] sde1[5] sdg1[4] sdd1[3] sdb1[2] sdc1[1] sdf1[0]
      11720285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [7/7] [UUUUUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk

unused devices: <none>
```

That's pretty much where I am right now.

How can I tell ( since it won't mount) if things were created properly? Is the bad superblock indicative of it not being created properly?

Thanks

---

### Post by darkod on 2018-09-04
I actually don't see any errors... Only one warning that sdb1 is misaligned, but that is only warning. Plus raid5 works with one member missing/unreadable.

Was the filesystem on md127 or you were using something else? LVM maybe?

According to the info in this thread the array looks correct. The order of disks is correct and it looks good...

Does blkid see filesystem and UUID on md127?
```
sudo blkid
```

---

### Post by lilrabbit129 on 2018-09-04
Here is the output of blkid

```
sudo blkid
/dev/sda1: UUID="3d4f2394-6ab7-4dde-95d3-c6bff2f09cc2" TYPE="ext4" PARTUUID="000eafa1-01"
/dev/sda5: UUID="dee9b83d-0caf-44d4-8c84-ca2520c5adbf" TYPE="swap" PARTUUID="000eafa1-05"
/dev/sdc1: UUID="f9425b43-8252-7b7d-026c-e534441aa020" UUID_SUB="997234d1-9fca-f737-0b99-61a107a75854" LABEL="dreadnaught:127" TYPE="linux_raid_member" PARTUUID="1b47b0cc-01"
/dev/sde1: UUID="f9425b43-8252-7b7d-026c-e534441aa020" UUID_SUB="d26b5c76-8826-e7d4-d41e-9907fafccab6" LABEL="dreadnaught:127" TYPE="linux_raid_member" PARTUUID="03e48dc5-01"
/dev/sdf1: UUID="f9425b43-8252-7b7d-026c-e534441aa020" UUID_SUB="a799b984-670e-5528-1c69-f5cff01ca1a8" LABEL="dreadnaught:127" TYPE="linux_raid_member" PARTUUID="d1606855-01"
/dev/sdd1: UUID="f9425b43-8252-7b7d-026c-e534441aa020" UUID_SUB="0aaad7bd-3129-a7be-4257-9d904981ae75" LABEL="dreadnaught:127" TYPE="linux_raid_member"
/dev/sdb1: UUID="f9425b43-8252-7b7d-026c-e534441aa020" UUID_SUB="4905bcf8-1da4-8798-ca44-f1660a7c70fd" LABEL="dreadnaught:127" TYPE="linux_raid_member"
/dev/sdg1: UUID="f9425b43-8252-7b7d-026c-e534441aa020" UUID_SUB="7da90a2f-b2dc-dc50-8be2-ce21f6d11d99" LABEL="dreadnaught:127" TYPE="linux_raid_member" PARTUUID="babfcc2c-01"
/dev/sdi1: UUID="e7f35731-6bad-4ecf-aea4-08e1bab698f9" TYPE="ext4" PARTLABEL="primary" PARTUUID="fe4de6bf-1c54-4fe9-89cc-d9d891ada97d"
/dev/sdh1: UUID="f9425b43-8252-7b7d-026c-e534441aa020" UUID_SUB="80a89578-7e5a-85fe-8d53-63f937a311ea" LABEL="dreadnaught:127" TYPE="linux_raid_member" PARTUUID="c7df6cc4-01"
```



Here's DF just so it makes more sense:

```
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           388M   41M  348M  11% /run
/dev/sda1       272G  233G   25G  91% /
tmpfs           1.9G  188K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sdi1       4.6T  4.3T   86G  99% /mnt/fivetb
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           388M   28K  388M   1% /run/user/111
tmpfs           388M     0  388M   0% /run/user/1000
```

There is no output when I call  sudo blkid /dev/md127...

EDIT: Yes the filesystem was on /dev/md127, IIRC it was ext4. 

Thanks.

---

### Post by lilrabbit129 on 2018-09-04
Another note: I did notice that during creation /dev/sdh1 was being seen as ext2fs possibly, so I tried creating an array with /dev/sdh1 as "missing" ( to create a degraded raid5). Unfortunately that didn't solve anything.

---

### Post by lilrabbit129 on 2018-09-04
Ahh so another thing:

I've noticed that my old superblock on ( for example ) /dev/sdh1 was:

```
/dev/sdh1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : f21f5306:c8a07e60:fad3a920:52a40d5b
  Creation Time : Tue Dec 21 20:21:48 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 11721071616 (11178.09 GiB 12002.38 GB)
   Raid Devices : 7
  Total Devices : 7
Preferred Minor : 127

    Update Time : Thu Aug  9 23:31:29 2018
          State : clean
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0
       Checksum : ce567281 - correct
         Events : 120788

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8      113        6      active sync   /dev/sdh1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8       65        5      active sync   /dev/sde1
   6     6       8      113        6      active sync   /dev/sdh1

```

Whereas it now looks like:

```
/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : f41a4359:85a9c29b:c8c3456f:dc497295
           Name : dreadnaught:127  (local to host dreadnaught)
  Creation Time : Tue Sep  4 15:59:33 2018
     Raid Level : raid5
   Raid Devices : 7

 Avail Dev Size : 3906764976 (1862.89 GiB 2000.26 GB)
     Array Size : 11720285568 (11177.34 GiB 12001.57 GB)
  Used Dev Size : 3906761856 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=3120 sectors
          State : clean
    Device UUID : 05f0be2f:465797eb:b64d362a:f4806ccc

Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Sep  4 15:59:33 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 4f3fc5cb - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 6
   Array State : AAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
```

Obviously some things are bound to change, but the version went from 0.90.00 to 1.2. Could this be an issue? Is mdadm not backwards compatible? I'm assuming the version change is also why the format looks so different now, with no listing of what it thinks each drive is?

EDIT: Some more reading makes me think that I created this array with a 1.2 format superblock, when it should be a 0.9 superblock. I'm thinking I can do the --create with --metadata=0.90. I've seen examples online of upgrading from 0.9 --> 1+ but nothing saying the opposite. Is this possible? I'm a bit hesitant to "just try it" in fear of doing more damage than I might already have. 

Thanks!

---

### Post by lilrabbit129 on 2018-09-05
Update:

I went ahead and did this command:

```
sudo mdadm --create /dev/md127 --verbose --level=raid5 --raid-devices=7 --layout=left-symmetric --chunk=64 --metadata=0.90  --assume-clean /dev/sdf1 /dev/sdc1 /dev/sdb1 /dev/sdd1 /dev/sdg1 /dev/sde1 /dev/sdh1 

```

That netted me a valid UUID from blkid!

```
/dev/md127: UUID="6ae39f37-cd1b-4838-bac2-d375b1e1c9f5" TYPE="ext3"
```

Unfortunately it should be ext4, trying to mount got me this error in dmsg:

```
[431188.738835] EXT4-fs (md127): mounting ext3 file system using the ext4 subsystem
[431188.852160] EXT4-fs (md127): ext4_check_descriptors: Block bitmap for group 0 overlaps superblock
[431188.852165] EXT4-fs (md127): group descriptors corrupted!
```

an e2fsck wasn't super helpful:

```
sudo e2fsck -C0 -v -p /dev/md127 
e2fsck: A block group is missing an inode table while checking ext3 journal for /dev/md127

/dev/md127: ********** WARNING: Filesystem still has errors **********
```

I feel like i'm getting closer, hopefully whatever information the 1.2 metadata overwrote on the FS can be salvaged or repaired. 

Any ideas?

---

### Post by darkod on 2018-09-05
There shouldn't have been anything overwritten by wrong metadata version. I didn't catch that, you were using very old metadata version. So it needed to be set in the create command which you later did.

Don't forget the error you are seeing might be from the array failing, not the first create attempt. I think that is more probable.

Well, you managed to assemble the array. I don't know much about these latest errors though... Try googling them around until someone can figure something. :)

---

### Post by darkod on 2018-09-05
Can this help you? [https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

---

### Post by lilrabbit129 on 2018-09-05
Hmm that does look promising. Though the symptoms aren't quite what  I'm seeing. 

I ran fsck.ext4 ( with the -N option) and it said that the FS was modified, though the -N is supposed to be dry-run only. Maybe its just really good at pretending.

Regardless, I tried mounting the FS and it mounted. Unfortunately I think I lost about 2TB of data ( 2TB free instead of the 90GB it was supposed to have free). 

At this point I'm thinking of cutting my losses and just eat the 2TB loss. I'll probably run fsck.ext4 "for real", and get the errors fixed. Then hope that the 2TBs I lost are in my backups. 

Thanks for all your help in this!

---

### Post by lilrabbit129 on 2018-09-05
Bonus update:

So after fsck.ext4 finished, it was able to find an additional 1.5TBs of data. I'm now sitting at roughly 400GBs of data lost. Considering it could have been many TBs, I'm calling it a win. 

Thanks again for all your help!

Hopefully there's enough steps in this thread for someone else to follow in case they run into something similar.

---

### Post by darkod on 2018-09-05
Great. Although I have to say I am still confused why that would happen because with assume clean no data should be lost (not from the create process anyway) even if you didn't put the correct metadata version in the first attempt. Again, the data corruption might have happened on the very failure of the array, not in the subsequent re-create attempt.

If you consider it solved, please mark the thread as solved. You can do that in Thread Tools above the first post.

Cheers.

---

