---
title: "Cannot restore 4 drive RAID5"
date: 2021-03-19
forum: Server Platforms
---

### Post by myh3ad4urts on 2021-03-19
Hello!

I'm hoping someone here will be willing to help me.  I've been running an Ubuntu server for about five years without any major issues.  Last week I lost the server power supply.  Replaced supply and discovered that the motherboard had also failed.  Replaced motherboard and processor (took advantage and upgraded both).

The OS is located on a separate drive (sda1) which recovered nicely.  Within the system are four more drives that I had set up in a RAID5 config (sdb1, sdc1, sdd1, sde1).  When booting, it times out when trying to connect to md0 (the RAID5 array).  When I execute 'mdadm --query --detail /dev/md0', mdadm reports that sde1 and sdd1 are in a raid0 which is inactive.  I have also executed 'mdadm --examine' on each drive.  Results are as follows:
sdb1:  no super block detected
sdc1:  raid1 with two devices
sdd1:  raid5 with four devices
sde1:  raid5 with four devices

The last piece of information I have to throw out here is that this system started with a raid1 array consisting of two drives (plus the OS drive which was never part of the array).  A year in (about four years ago), I added two more drives to the array and converted it to a raid5.  I believe that I was running ubuntu 16 at that time and have since updated to ubuntu 20.04.2.  No problems with the raid at any point until now.

At this point, I'm assuming that md0 is being reported as raid0 is because of the failure to connect the other two drives.  I'm wondering if the super blocks are hiding somewhere else on the drives and mdadm is not finding them???  

I'm already pushing past my level of knowledge and would really appreciate it if someone would be willing to help me figure out how I can get my raid back up and running.

Thank you,
Christian

---

### Post by darkod on 2021-03-19
Please post the full output of the examine command. Paste it here in CODE tags.
```
sudo mdadm -E /dev/sd[bcde]1
```

Be careful if taking any other steps because you might make the array unusable if wrong commands are executed.

---

### Post by myh3ad4urts on 2021-03-19
Thank you for the quick reply!
Output was as follows:
```
mdadm: No md superblock detected on /dev/sdb1./dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 6e86c410:ba5c5723:9595a890:5ef3c56f
           Name : hamburgerbuntu:0  (local to host hamburgerbuntu)
  Creation Time : Thu Sep  8 20:52:25 2016
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 2930134016 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 13af63d2:156eb449:3c85ea35:c0ae75d8


Internal Bitmap : 8 sectors from superblock
    Update Time : Fri Oct  6 14:01:10 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : dac3eb4d - correct
         Events : 6618




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 6e86c410:ba5c5723:9595a890:5ef3c56f
           Name : hamburgerbuntu:0  (local to host hamburgerbuntu)
  Creation Time : Thu Sep  8 20:52:25 2016
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860268416 (2794.39 GiB 3000.46 GB)
     Array Size : 8790402048 (8383.18 GiB 9001.37 GB)
  Used Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
    Data Offset : 261760 sectors
   Super Offset : 8 sectors
   Unused Space : before=261672 sectors, after=384 sectors
          State : clean
    Device UUID : 13af63d2:156eb449:3c85ea35:c0ae75d8


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Mar  2 21:10:44 2021
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : f9434748 - correct
         Events : 16191


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 6e86c410:ba5c5723:9595a890:5ef3c56f
           Name : hamburgerbuntu:0  (local to host hamburgerbuntu)
  Creation Time : Thu Sep  8 20:52:25 2016
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860268416 (2794.39 GiB 3000.46 GB)
     Array Size : 8790402048 (8383.18 GiB 9001.37 GB)
  Used Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
    Data Offset : 261760 sectors
   Super Offset : 8 sectors
   Unused Space : before=261672 sectors, after=384 sectors
          State : clean
    Device UUID : 694aac8c:f6e1b77e:e92ca9a1:a105c974


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Mar  2 21:10:44 2021
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : f0a1550e - correct
         Events : 16191


         Layout : left-symmetric
     Chunk Size : 64K


   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
```

---

### Post by darkod on 2021-03-19
It doesn't look very good. The update time of sdc1 says Oct 2017. Not sure if the superblock is just confused, or nothing was really written to the disk for 3 years. I guess it is difficult that you had a disk failed for so long and you didn't notice it.

First try to assemble it, but I think this will fail because one member lost the superblock and another has raid1 format in its superblock. Worth of try though...

Stop the wrong md0 if it is assembled, and then try to force assemble the 4-member raid5:
```
sudo mdadm --stop /dev/md0
sudo mdadm --assemble --force --verbose /dev/md0 /dev/sd[bcde]1
```

Post the output of what the verbose command says.

---

### Post by myh3ad4urts on 2021-03-19
Array stopped fine.

```
mdadm: looking for devices for /dev/md0mdadm: no recogniseable superblock on /dev/sdb1
mdadm: /dev/sdb1 has no superblock - assembly aborted
```

---

### Post by myh3ad4urts on 2021-03-19
Not likely that it wasn't used for years - I had the system emailing me the result of 'cat /proc/mdstat' every morning.  I also checked the status at least once a week (when I performed updates).

---

### Post by myh3ad4urts on 2021-03-19
The raid1 on sdc1 is what has me wondering if its possible that the old raid1 superblock is taking "precedent" over the correct raid5 superblock???  Is that even a possibility?

---

### Post by darkod on 2021-03-19
Like I thoughts... If you are sure your data was good (or relatively good) until the power went out, you could try creating new array but keeping the data intact. There might be some small part of corruption but you should get most of your data back.

I don't know another way, sorry.

If you want to try that, first is to zero the superblock on all members, and then create new array with --assume-clean parameter. This is very important!!. If you use --create without --assume-clean it will create new blank array probably losing all data. The only way to keep existing data is using that parameter.

```
sudo mdadm --zero-superblock /dev/sdc1
sudo mdadm --zero-superblock /dev/sdd1
sudo mdadm --zero-superblock /dev/sde1
sudo mdadm --create --verbose --assume-clean /dev/md0 /dev/sd[bcde]1
```

If that completes without errors, mount it read-only and check the data. I would do that before starting to use it for writing on it.

---

### Post by myh3ad4urts on 2021-03-19
Zeroed all three superblocks [cde]1.
Tried to create array:
```
christian@hamburgerbuntu:~$ sudo mdadm --create --verbose --assume-clean /dev/md0 /dev/sd[bcde]1
mdadm: no raid-devices specified.
christian@hamburgerbuntu:~$
```

That doesn't look good...

---

### Post by darkod on 2021-03-19
OK, it needs modifications it seems.
```
sudo mdadm --create /dev/md0 --verbose --assume-clean --level=raid5 --raid-devices=4 /dev/sd[bcde]1
```

---

### Post by myh3ad4urts on 2021-03-19
Oh no...
I just went back through what I had done...
I was reading about the no raid-devices on the forum and found reference to it.  I copied it.
Then saw your post and highlighted your text instead.  I thought the terminal had copied yours...  It didn't.  The version I pasted was missing the --assume-clean.
I missed it...
Oh no...
I'm going to go cry now.
Trying to mount the array so that I can verify that I just killed everything.  Can't even get it to do that.
Not been a great day.

---

### Post by myh3ad4urts on 2021-03-19
Got it to mount - for some reason it created it with a md127 reference instead of md0... ?!?
Checked the mount point - it's empty.
Oh no.

---

