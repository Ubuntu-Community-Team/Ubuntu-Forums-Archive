---
title: "recovering data from synology diskset using ubuntu -"
date: 2016-07-20
forum: Server Platforms
---

### Post by erwinpanen-fastmail on 2016-07-20
Hi,
Not sure if I'm in the right place to post this, came here because I found pointers of other people that found help here!

I have 2 disks that were in a SHR config in a synology 2 disk station. One day I got an error with one of the harddrives. Data had become read only.
Searched and found explanation to recover or copy data using ubuntu.
Using ubuntu 16.05 LTS.

2 disks are /dev/sdc and /dev/sdd.
info /dev/sdc

```
erwin@ubuntu-1:~$ sudo mdadm -E /dev/sdc/dev/sdc:
``````

  MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
erwin@ubuntu-1:~$ sudo mdadm -E /dev/sdc1
/dev/sdc1:
         Magic : a92b4efc
       Version : 1.2
   Feature Map : 0x0
    Array UUID : 906c70a9:455374ab:87943a95:7f3ae6a7
          Name : DiskStation:3
 Creation Time : Wed Jun 12 20:52:10 2013
    Raid Level : raid1
  Raid Devices : 1

Avail Dev Size : 5851088833 (2790.02 GiB 2995.76 GB)
    Array Size : 2925544256 (2790.02 GiB 2995.76 GB)
 Used Dev Size : 5851088512 (2790.02 GiB 2995.76 GB)
   Data Offset : 2048 sectors
  Super Offset : 8 sectors
  Unused Space : before=1968 sectors, after=18446744073709549576 sectors
         State : clean
   Device UUID : 922f5b98:59438189:779afa43:bd3b69bd

   Update Time : Wed Jul 20 09:48:17 2016
      Checksum : dabc7b5f - correct
        Events : 4

  Device Role : Active device 0
  Array State : A ('A' == active, '.' == missing, 'R' == replacing)
```

info /dev/sdd
```
erwin@ubuntu-1:~$ sudo mdadm -E /dev/sdd1/dev/sdd1:
``````

         Magic : a92b4efc
       Version : 1.2
   Feature Map : 0x0
    Array UUID : 92a5fac8:186767b4:a07480b3:61d0a1ab
          Name : DiskStation:2
 Creation Time : Sun Jun 16 13:35:37 2013
    Raid Level : raid1
  Raid Devices : 1

Avail Dev Size : 5851088833 (2790.02 GiB 2995.76 GB)
    Array Size : 2925544256 (2790.02 GiB 2995.76 GB)
 Used Dev Size : 5851088512 (2790.02 GiB 2995.76 GB)
   Data Offset : 2048 sectors
  Super Offset : 8 sectors
  Unused Space : before=1968 sectors, after=18446744073709549576 sectors
         State : clean
   Device UUID : 98fb4cdd:ee4fd408:84968c4d:b9196feb

   Update Time : Tue Jul 19 17:34:29 2016
      Checksum : 229141e7 - correct
        Events : 11850982

  Device Role : Active device 32768
  Array State : . ('A' == active, '.' == missing, 'R' == replacing)
```

Trying to assemble throws superblock error:
```
erwin@ubuntu-1:~$ sudo mdadm --assemble /dev/md0 /dev/sdc1 /dev/sdd1mdadm: superblock on /dev/sdd1 doesn't match others - assembly aborted
```

Can anyone point me to how to make my data visible and retrievable?
Thanks for helping out!

---

### Post by darkod on 2016-07-20
If you notice the Array UUID and the Events info in the examine output, the UUID is not the same for both sdc1 and sdd1. According to mdadm superblock they do not belong to the same array (I say according to the superblock, not that they actually were not part of same array).

Also, the Events on sdc1 are very low, only 4, while sdd1 has quite a big value.

According to that and because raid1 can work with only one member, I would try to assemble it with only sdd1 and see what happens. It would be like:
```
sudo mdadm --stop /dev/md0 (stop any previous attmpt array, if any)
sudo mdadm --assemble --verbose /dev/md0 /dev/sdd1
```

See how that goes and post the output of the assemble command. If that doesn't work there are further steps to try.

---

### Post by erwinpanen-fastmail on 2016-07-20
Darko, thanks for posting.
Here's the output of assemble cmd:

```
erwin@ubuntu-1:~$ sudo mdadm --assemble --verbose /dev/sdd1
mdadm: device /dev/sdd1 exists but is not an md array
```

```
erwin@ubuntu-1:~$ sudo mdadm --assemble --verbose /dev/sdc1
mdadm: device /dev/sdc1 exists but is not an md array.
```

Other things I've tried:
- foremost (saw a lot of garble passing in terminal, I'm not familiar with foremost, apparently this will recover and sort depending on file type - to me this has the disadvantage of losing my file structure. Foremost ended with some read / write error.)
- testdisk

---

### Post by darkod on 2016-07-20
I'm not familiar with foremost. Testdisk I have used for basic functions and only on partitions. I'm not even sure you can use it on software arrays.

Don't forget that when using mdadm raid it is the raid array that is holding the filesystem, not the partition. Although with raid1 (mirror) that might not be 100% true, I have never actually looked into the deep details of that.

So, without the array assembled I wouldn't try any rescue programs, which sounds like you did. The actions you have taken might have produced more problems than what you started with...

How about trying the standard auto-detect assemble:
```
sudo mdadm --assemble --scan --verbose
```

See if that gets you anywhere...

---

### Post by erwinpanen-fastmail on 2016-07-20
I understand - I'm giving all information as to what I have tried so that you are not mislead.
In [this]("https://ubuntuforums.org/showthread.php?t=1947275") post, I've read and tried to follow, and assemble my raid, but it did not work.

FYI, my nas is named diskstation, and this is what we see in identified as member of DiskStation.
So it appears both drives are identified as member of DiskStation.

Here are the results:
```
erwin@ubuntu-1:~$ sudo mdadm --assemble --scan --verbose[sudo] password for erwin: 
mdadm: looking for devices for further assembly
```

```
mdadm: /dev/sdd1 is identified as a member of /dev/md/DiskStation:2, slot 32768.mdadm: No suitable drives found for /dev/md/DiskStation:2
mdadm: looking for devices for further assembly
mdadm: /dev/sdc1 is identified as a member of /dev/md/DiskStation:3, slot 0.
mdadm: failed to add /dev/sdc1 to /dev/md/DiskStation:3: Invalid argument
mdadm: failed to RUN_ARRAY /dev/md/DiskStation:3: Invalid argument
mdadm: looking for devices for further assembly
mdadm: No arrays found in config file or automatically
erwin@ubuntu-1:~$ 



```

---

### Post by darkod on 2016-07-20
I think we now have only one last thing to try. But you'll have to be patient 3-4 hours until I get home and can write up everything nicely.

---

### Post by erwinpanen-fastmail on 2016-07-20
No problem, thanks for helping out!

---

### Post by darkod on 2016-07-20
The only idea I have is to try and re-create the array but using the --assume-clean option to tell mdadm that you are trying to re-create existing array. It is very important to use that parameter because by default --create is creating a new blank array.

I think the best option is to try use sdd1 only, because in the superblock it has more events and it looks like a better candidate than sdc1 to have more data intact. With --create it is good that you can specify missing members, in other words to create a raid1 with only one partition present.

In any case sdc1 will remain as it is because we will not be touching it.

The command to re-create the array with one missing member and only sdd1 would be:
```
sudo mdadm --create /dev/md0 --assume-clean --verbose --level=raid1 --raid-devices=2 missing /dev/sdd1
```

That should create a new 2 member raid1 array with one missing member and sdd1 and keeping the existing data by using the --assume-clean parameter.

If you want to, try it out and let us know how it went... This is only to assemble the array back, after that you will need to work on the filesystem and whether it will be intact or not.

---

### Post by erwinpanen-fastmail on 2016-07-20
Darkod,

This seems to work!

```
**erwin@ubuntu-1**:**~**$ sudo mdadm --create /dev/md0 --assume-clean --verbose --level=raid1 --raid-devices=2 missing /dev/sdd1[sudo] password for erwin: 
mdadm: /dev/sdd1 appears to be part of a raid array:
       level=raid1 devices=1 ctime=Sun Jun 16 13:35:37 2013
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: size set to 2925413184K
mdadm: automatically enabling write-intent bitmap on large array
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
```

1. Diskutil shows the 3 TB raid as unknown...
2. Any ideas from here?
3. I guess I can do the same for the other disk?

Thanks a lot for helping out!

---

### Post by darkod on 2016-07-20
If you want to, you can create another array (for example /dev/md1) at the same time with sdc1 and missing member. And see if any filesystem can be detected on it.

Now that you have md0 assembled, you should check it's FS and see what comes up. For example something like:
```
sudo fsck /dev/md0
```

DO NOT try to mount it, filesystem checks should be done unmounted. Also, I don't know which filesystem was used earlier, the fsck is only for ext2/3/4 I think... But you can also google for various commands how to check unknown filesystem.

---

### Post by erwinpanen-fastmail on 2016-07-20
```
erwin@ubuntu-1:~$ sudo fsck /dev/md0
[sudo] password for erwin: 
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/md0


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

- I'm quite sure the filesys is Ext4
- Shall I run the proposed cmd's?

```
**erwin@ubuntu-1**:**~**$ sudo e2fsck -b 8193 /dev/md0e2fsck 1.42.13 (17-May-2015)
e2fsck: Bad magic number in super-block while trying to open /dev/md0


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


**erwin@ubuntu-1**:**~**$ sudo e2fsck -b 32768 /dev/md0
e2fsck 1.42.13 (17-May-2015)
e2fsck: Bad magic number in super-block while trying to open /dev/md0


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

For completness sake:

```
**erwin@ubuntu-1**:**~**$ sudo mdadm --create /dev/md1 --assume-clean --verbose --level=raid1 --raid-devices=2 missing /dev/sdc1mdadm: /dev/sdc1 appears to be part of a raid array:
       level=raid1 devices=1 ctime=Wed Jun 12 20:52:10 2013
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: size set to 2925413184K
mdadm: automatically enabling write-intent bitmap on large array
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md1 started.
**erwin@ubuntu-1**:**~**$ sudo fsck /dev/md1
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/md1


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


**erwin@ubuntu-1**:**~**$ sudo e2fsck -b 8193 /dev/md1
e2fsck 1.42.13 (17-May-2015)
e2fsck: Bad magic number in super-block while trying to open /dev/md1


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


**erwin@ubuntu-1**:**~**$ sudo e2fsck -b 32768 /dev/md1
e2fsck 1.42.13 (17-May-2015)
e2fsck: Bad magic number in super-block while trying to open /dev/md1


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


**erwin@ubuntu-1**:**~**$ 
```

Any more ideas?
I guess I'll need to do some reading up on data recovery...

---

### Post by darkod on 2016-07-20
This says they use LVM too: [https://www.synology.com/en-global/knowledgebase/DSM/tutorial/Storage/How_can_I_recover_data_from_my_DiskStation_using_a_PC](https://www.synology.com/en-global/knowledgebase/DSM/tutorial/Storage/How_can_I_recover_data_from_my_DiskStation_using_a_PC)

Try to activate any possible LVM with:
```
sudo vgchange -ay
```

See if that reports any LVs as activated.

Don't force the fsck when you are not sure its ext filesystem, you might ruin what you achieved so far!!! Plus we are still not sure the array is any good at all, just because it assembled it doesn't mean anything.

---

### Post by erwinpanen-fastmail on 2016-07-20
Ok, I'll go really slow and await your reply / advice.
The vgchange -ay throws no response - any way to do this verbose?

---

### Post by erwinpanen-fastmail on 2016-07-20
```
**erwin@ubuntu-1**:**~**$ sudo vgchange -ay -v    Using volume group(s) on command line.
    No volume groups found.
```

---

### Post by darkod on 2016-07-20
There is no LVM on your raid. At least not recognizable...

Maybe they changed their setup mean while (if your device is newer???). Don't know, you'll have to do some googling around.

---

