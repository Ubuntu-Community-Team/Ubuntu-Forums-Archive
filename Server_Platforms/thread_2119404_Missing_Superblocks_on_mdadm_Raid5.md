---
title: "Missing Superblocks on mdadm Raid5"
date: 2013-02-23
forum: Server Platforms
---

### Post by Kljuka on 2013-02-23
My Mdadm Raid5 array of 4 drives failed during synchronization after replacement of one failed drive. It threw me to RamFS where after a while I couldn't mount the array any more (don't know what I did... :( ).



I inserted Ubuntu live CD and this is where I am now :

[LIST]
[*]fdisk finds all the partitions on all 4 drives correctly (/dev/sda - /dev/sdd)
[/LIST]

[LIST]
[*]I can assemble array using
```
mdadm --create /dev/md3 --assume-clean --level=5 --raid-devices=4 missing /dev/sdb3 /dev/sda3 /dev/sdc3

cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md3 : active raid5 sda3[3] sda1[2] sda2[1]
2923643904 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [_UUU]
```
[/LIST]

[LIST]
[*]I **can't mount** the array (/dev/md3) using:
```
mount -t ext3 /dev/md3 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/md3,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
```
[/LIST]

[LIST]
[*]checking filesystem with **e2fsck fails**
```
e2fsck /dev/md3
e2fsck 1.42.5 (29-Jul-2012)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/md3

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193
```
[/LIST]

[LIST]
[*]using **dumpe2fs** /dev/md3 won't find any Superblocks:
```
dumpe2fs /dev/md3 dumpe2fs 1.42.5 (29-Jul-2012)
dumpe2fs: Bad magic number in super-block while trying to open /dev/md3
Couldn't find valid filesystem superblock.
```
[/LIST]

It seems to me that all the Superblocks of ext3 filesystem on the raid array are missing. 

[LIST=1]
[*] Is there a way to recreate the superblock on the array? Or am I doomed?
[*]Am I missing something? Did I forget to use some commands?
[*]If not: is there a way to recover all the files/directories?
[*]And in the worst possible case: how do I recover particular files (eg.: some bash scripts in my /home/ directory)? Which tools do you suggest?
[/LIST]

I will appreciate a lot your help because I'm completely in the dark here :confused:.


p.s.: dumping the content of /dev/md3 and using "grep" shows that there's still data on it
p.p.s.: I have a backup of important data. Only after disk failure do you figure out that some "unimportant" data was actually quite important.

---

### Post by rubylaser on 2013-02-23
When you re-create the array with the assume clean option, the metadata version has to be the same, and the disk order exactly the same. Are you positive that both of those conditions are met?

---

### Post by Kljuka on 2013-02-23
I have no idea about the metadata version. How do I check that? When I created the array I was using Ubuntu 8.04 (I guess) so quite a long time ago (year 2008).

And I'm 90% sure about the disk order (I'm working on a "dd copy" of all partitions not to damage the data).

---

### Post by rubylaser on 2013-02-23
If your array is that old, then your metadata version should be 0.90.  You can redo the create --assume-clean again, but this time pass the --metadata=0.90 in. Also, your chunk size should have been 64K, so pass this in as well --chunk=64

---

### Post by darkod on 2013-02-24
Also note in your --create command you posted above, the order of the devices is "missing /dev/sdb3 /dev/sda3 /dev/sdc3".

As rubylaser said, the exact same order is very important. When you created the array as new, wouldn't the logical disk order be like "sda3 sdb3 sdc3 sdd3"?

And after you did the --create, look at the /proc/mdstat. It actually says md3 is assembled with "sda3 sda1 sda2". All are partitions on the same disk, not different disks.

Any thoughts on that rubylaser?

---

### Post by rubylaser on 2013-02-24
> **darkod said:**
> Also note in your --create command you posted above, the order of the devices is "missing /dev/sdb3 /dev/sda3 /dev/sdc3".

As rubylaser said, the exact same order is very important. When you created the array as new, wouldn't the logical disk order be like "sda3 sdb3 sdc3 sdd3"?

And after you did the --create, look at the /proc/mdstat. It actually says md3 is assembled with "sda3 sda1 sda2". All are partitions on the same disk, not different disks.

Any thoughts on that rubylaser?

I hope that's just a copy / paste error, because I can't explain that unless that was a failed auto assemble. I would stop /dev/md3 and try again with the create command.

```
mdadm --stop /dev/md3
```

---

### Post by Kljuka on 2013-02-24
Wow rubylaser. Thanks. This definitely helped. After checking my old "mdadm --detail /dev/md3" it was indeed "metadata version 0.9" and "chunk size 64K".

I assembled as you said:
```
mdadm --create /dev/md3 --assume-clean --metadata=0.90 --level=5  --chunk=64 --raid-devices=4 missing /dev/sdb2 /dev/sdb1 /dev/sdb3
mdadm: /dev/sdb2 appears to contain an ext2fs file system
size=-1102493376K mtime=Tue Nov 21 08:31:46 2028
mdadm: /dev/sdb2 appears to be part of a raid array:
level=raid5 devices=4 ctime=Sun Feb 24 03:57:57 2013
mdadm: /dev/sdb1 appears to be part of a raid array:
level=raid5 devices=4 ctime=Sun Feb 24 03:57:57 2013
mdadm: /dev/sdb3 appears to be part of a raid array:
level=raid5 devices=4 ctime=Sun Feb 24 04:54:27 2013
Continue creating array? y
mdadm: array /dev/md3 started.
```Why does it say /dev/sdb2 cointains ext2 while the others not?


Now I can finally see some information back from dumpe2fs. So this is what it outputs:
```
dumpe2fs /dev/md3
dumpe2fs 1.42 (29-Nov-2011)
Filesystem volume name: storage
Last mounted on: <not available>
Filesystem UUID: a748cb0a-427a-43c8-956d-773c11d5eead
Filesystem magic number: 0xEF53
Filesystem revision #: 1 (dynamic)
Filesystem features: has_journal ext_attr resize_inode dir_index filetype sparse_super large_file
Filesystem flags: signed_directory_hash
Default mount options: (none)
Filesystem state: clean
Errors behavior: Continue
Filesystem OS type: Linux
Inode count: 182755328
Block count: 731009616
Reserved block count: 36550480
Free blocks: 39511366
Free inodes: 181309822
First block: 0
Block size: 4096
Fragment size: 4096
Reserved GDT blocks: 849
Blocks per group: 32768
Fragments per group: 32768
Inodes per group: 8192
Inode blocks per group: 256
Filesystem created: Sun Aug 3 23:06:31 2008
Last mount time: Fri Feb 1 18:54:42 2013
Last write time: Sat Jan 19 19:06:50 2013
Mount count: 16
Maximum mount count: 25
Last checked: Sat Jan 19 19:06:50 2013
Check interval: 15552000 (6 months)
Next check after: Thu Jul 18 20:06:50 2013
Reserved blocks uid: 0 (user root)
Reserved blocks gid: 0 (group root)
First inode: 11
Inode size: 128
Journal inode: 8
Default directory hash: tea
Directory Hash Seed: ad1bab00-ae50-4870-952f-05bbf2413152
Journal backup: inode blocks
dumpe2fs: A block group is missing an inode table while reading journal inode
```I guess the superblock is back. But trying to mount it still fails:
```
mount -t ext3 -o ro /dev/md3 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/md3,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
```So I guess there are errors that have to be corrected. I ran:
```
e2fsck /dev/md3
e2fsck 1.42 (29-Nov-2011)
e2fsck: Group descriptors look bad... trying backup blocks...
Superblock has an invalid journal (inode 8).
Clear<y>?
```What should I do? Say yes to clear?



> And after you did the --create, look at the /proc/mdstat. It actually  says md3 is assembled with "sda3 sda1 sda2". All are partitions on the  same disk, not different disks."This was a copy/paste error on my part. The original disks were /dev/sd[a-d]3 but I dd copied the partitions to new disk /dev/sda[1-3] (and /dev/sdd3 missing). The order of disks changed through time because of reboots and disk replacements.

---

### Post by darkod on 2013-02-24
> **Kljuka said:**
> 
This was a copy/paste error on my part. The original disks were /dev/sd[a-d]3 but I dd copied the partitions to new disk /dev/sda[1-3] (and /dev/sdd3 missing). The order of disks changed through time because of reboots and disk replacements.

Did you do this only as data access procedure? I hope you are not planning to run a raid array with all partitions on the same disk.

Even for a short time, that might be too intense for the disk, imagine it has to race all over the disk since you made it have raid5 array with three partitions on the same disk. I don't understand. Even if one disk failed, you still had three left, right? Why dd-ing to a single disk?

---

### Post by Kljuka on 2013-02-24
I wouldn't run raid5 from 1 disk. This is only a "Save the data procedure". I don't want to test Data Recovery on original data disks (not to mess things up even further).

---

### Post by rubylaser on 2013-02-24
It does look like it recognizes the filesystem, but it's messed up.  If you run the fsck like this it's very likely you'll end up with almost the whole filesystem in your lost+found folder.  If this is just a test, and you still have the original disks, it's worth a shot at this point.

---

### Post by Kljuka on 2013-02-24
Yes, it's been taking fsck already a couple of hours doing the job.

Do you think this might be a sign that I assembled the array with the drives in a wrong order? Is there a way to figure out the order of disks by assembling the array and afterwards doing some superblock check?

p.s.: I really wanted to understand how mdadm actually assembles the array (logic and mathematics used in mdadm) but I could only find a lot of forums full of raid disasters and partial (sometimes inaccurate) solutions. Seems to me there's no official structured and more in depth documentation available.

---

### Post by tealio on 2013-03-03
[SIZE=3][COLOR="#FF0000"]*** EDIT *** : using --zero-superblock should not be used in this case.  --assume-clean is better for this application.  It worked for me, but apparently was a bad idea.[/COLOR][/SIZE]


if fsck is taking that long, you've probably already trashed the filesystem.  I know, because i assembled one in the wrong order just yesterday.  It was late, and instead of sleeping and dealing with it in the morning, i decided to go ahead and destroy my filesystem.  I had a backup.  

It's probably too late for you, but here's what worked for me:

First, check the existing superblock too see what order the devices really go in:
```
root@AMD-Media:~# mdadm -E /dev/sd[abd] |egrep 'sd|Chunk|Role|Version'
/dev/sda:
        Version : 1.2
     Chunk Size : 128K
   Device Role : Active device 2
/dev/sdb:
        Version : 1.2
     Chunk Size : 128K
   Device Role : Active device 0
/dev/sdd:
        Version : 1.2
     Chunk Size : 128K
   Device Role : Active device 1

```

I'm using whole disks instead of partitions, and they are attached in a weird order, but your info should look similar.
Note the Device Role.  They should be reassembled in the order 0 1 2.  If there's a number missing (Let's say yours are numbered 0 1 3) they still just go in ascending order.  In my case it's /dev/sdb /dev/sdd /dev/sda

Next, do something scary:
```
root@AMD-Media:~# mdadm --stop /dev/md0
root@AMD-Media:~# mdadm --remove /dev/md0
root@AMD-Media:~# mdadm --zero-superblock /dev/sd[abd]
```

This clears the superblock on each device so that mdadm doesn't give you any problems about assembling devices (partitions, whatever) that have different event numbers, modify dates, etc.

Next, use the info from the mdadm -E to recreate the array.  In my case:
```
root@AMD-Media:~# mdadm --create /dev/md0 --bitmap=/etc/mdadm/md0.bitmap --chunk=128 --metadata=1.2 --level=5 --raid-devices=3 --force /dev/sdb /dev/sdd /dev/sda
```

I had to use force because my bitmap file already existed.  Also, don't be tempted to use bracket expansion on the drive order.  bracket expansion doesn't respect the order you put things in, and as far as i can tell it alphabetizes them, so ```
/dev/sd[bda]
``` isn't equal to ```
/dev/sdb /dev/sdd /dev/sda
```

I'd love to show you the output from that, but it's rebuilding right now, and i didn't cut and paste it when i did it... 

It does, however come up and mention that there is evidence of an existing filesystem/partition table... If you're 100% SURE that you've got the metadata version, chunk size and order correct then you can allow the array to be created.  It will do a resync, but your data should be immediately available to mount and use.

Again, this is what worked for ME and MY SITUATION!  no guarantees!

---

### Post by darkod on 2013-03-03
Isn't a --create with --assume-clean a better option to try first? Without zeroing the superblocks. That should force it even if the events counters are not the same. Of course, you still have to use the same original order and use 'missing' for any missing members.

---

### Post by tealio on 2013-03-03
That is absolutely true.  My case was a weird one though, because i was trying to upgrade disks.
I'm going on memory here, but i think i ended up with the 2 original disks and the new disk all having a newer creation date.  Then i had one of the old disks fail.  So i ended up trying to rebuild an array from 2 good disks with different creation dates, and a third disk that I'm not so sure about... I'm currently trying to rebuild the original array so i can start over.  this has been going on since Wednesday.

If this rebuild fails at 99.9% like the others, then im going to run the array degraded, and put my new disk in a single disk RAID 1.  Then I'll have to copy over the data, then mirror that disk, then convert to RAID5 and add the third disk... PITA

anyway, to answer your question, --assume-clean would probably still have been a better option.

I don't wanna get too far off here, but if --assume-clean is a better option with similar results to --zero-superblock, then what is the case in which --zero-superblock would be used?  
Is it only for when you're really removing a drive from an array, but it's staying in your system? to keep mdadm from scanning it and trying to add it to an array?

---

### Post by darkod on 2013-03-03
Yes, as far as I understand it, you would use --zero-superblock to completely delete any traces of mdadm to use the disk as separate or add it later but as "new" disk, otherwise if it detects a superblock it might try to re-add it as disk that was earlier in the array and mess things for you.

For assembling existing array you would start with mdadm --assemble --scan, but that would work only if there are no major issues. If the events don't match I think it will fail. The next is --create --assume-clean or --create --run, with correct level and number of devices and their order.

If all of that fails, you need to look at drastic measures/attempts.

---

### Post by tealio on 2013-03-03
ok... so i just skipped straight to the big leagues... oops...

---

### Post by chamsters on 2013-05-09
Hey guys,

I'm having the identical issue and was hoping you guys could help me troubleshoot some?

> root@server:~# dumpe2fs /dev/md3dumpe2fs 1.41.3 (12-Oct-2008)
Filesystem volume name:   /var/lib/vz
Last mounted on:          <not available>
Filesystem UUID:          e4881189-a1aa-4dbd-9776-8df39c2f6039
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash
Default mount options:    (none)
Filesystem state:         clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              179109888
Block count:              716422752
Reserved block count:     35821137
Free blocks:              236978281
Free inodes:              78393903
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      853
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Tue Aug 24 18:34:53 2010
Last mount time:          Wed Feb 29 07:37:51 2012
Last write time:          Wed May  8 16:02:53 2013
Mount count:              4
Maximum mount count:      24
Last checked:             Thu Feb 16 10:44:25 2012
Check interval:           15552000 (6 months)
Next check after:         Tue Aug 14 11:44:25 2012
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
First orphan inode:       45294652
Default directory hash:   half_md4
Directory Hash Seed:      da833f00-139d-4f21-90e2-38830d884e00
Journal backup:           inode blocks
dumpe2fs: A block group is missing an inode table while reading journal inode





> root@server:~# cat /proc/mdstatPersonalities : [raid1] [raid0] [raid6] [raid5] [raid4]
md3 : active raid5 sdd3[2] sdc3[1] sda3[0]
      1910460672 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]


md1 : active raid1 sda1[0] sdb1[1]
      20480896 blocks [4/2] [UU__]


unused devices: <none>






> root@server:~# mount -a /dev/md3mount: wrong fs type, bad option, bad superblock on /dev/md3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so




---

### Post by darkod on 2013-05-09
What identical issue? The OP had the arrays not working, yours are active.

If /dev/md3 complains about mounting, did you try fsck first?
```
sudo fsck /dev/md3
```

Don't try to mount it before running fsck, it needs to be unmounted.

---

### Post by chamsters on 2013-05-09
> **darkod said:**
> What identical issue? The OP had the arrays not working, yours are active.

If /dev/md3 complains about mounting, did you try fsck first?
```
sudo fsck /dev/md3
```

Don't try to mount it before running fsck, it needs to be unmounted.


> root@londonpower:~# fsck /dev/md3fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Group descriptors look bad... trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/md3


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>




that's what I get....

---

### Post by darkod on 2013-05-09
What do you have on md3? Can you post:
```
sudo parted -l
```

---

### Post by chamsters on 2013-05-09
> **darkod said:**
> What do you have on md3? Can you post:
```
sudo parted -l
```

hm doesn't seem to work. 

> -bash: parted: command not found

---

### Post by darkod on 2013-05-09
It's included in every ubuntu. Did you write it correctly? The option should be -l which is small L.

Also, the /proc/mdstat says you have one raid5 array of 3 members, and all are active.
It also says you have ona raid1 array of 4 members out of which 2 are active, but that's still enough for raid1 to work.

---

### Post by chamsters on 2013-05-10
> **darkod said:**
> It's included in every ubuntu. Did you write it correctly? The option should be -l which is small L.

Also, the /proc/mdstat says you have one raid5 array of 3 members, and all are active.
It also says you have ona raid1 array of 4 members out of which 2 are active, but that's still enough for raid1 to work.


Definitely wrote it right. It's a custom ovh build of proxmox so could just be a 'minimal' version or something?

re: mdstat, yep - 1 x md1 with a 2 drive raid1 (used to be 4, other 2 spare); 1 x md3 with 4 drive (now 3 after reassembly when trying to at least view my data).

---

### Post by darkod on 2013-05-10
First, custom builds can introduce differences so some things might not apply. You might wanna look for help on their website too, since you decided to use their custom build.

Second, what do you mean md3 with 4 drive but now 3? Assembling a 4 disk array with 3 disks should still say it's a 4 disk array with one member missing. Your says it's a 3 disk array, all members present, period. Are you sure you assembled it or you created a new one? The data might be overwritten if a new array was created over the old one.

Otherwise, the assemble procedure doesn't change the number of disks/members. There is a procedure to change number of disks with --grow but that's different. Assemble doesn't do that, and if you did a simple assemble it should still say you have 4 members one missing.
Can you post the exact command you used?

---

