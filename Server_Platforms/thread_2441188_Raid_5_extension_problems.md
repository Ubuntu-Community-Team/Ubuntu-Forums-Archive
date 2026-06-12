---
title: "Raid 5 extension problems"
date: 2020-04-20
forum: Server Platforms
---

### Post by templeclause2 on 2020-04-20
I have 4x 3TB disks and 1x M2 disk where the OS is running on. 

The 4x 3TB disks are on /dev/sda, /dev/sdb, /dev/sdc, /dev/sdd. The os is on /dev/sde. 

I created a RAID 5 with 3 disks (/dev/sdb, /dev/sdc, /dev/sdd) according to this instructions: 
[https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04#creating-a-raid-5-array](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04#creating-a-raid-5-array)

Then I copied everything from my /dev/sda HDD to this raid setup /dev/md0. 
From there I deleted the /dev/sda1 partion and tried to extend the RAID 5 with the /dev/sda. 

I removed the /dev/md0 entry from the fstab file so it doesn't get mounted and then rebooted the system. 

This is my shell log for the extension:

```

tc@Ubuntu:$ sudo mdadm --add /dev/md0 /dev/sda
[sudo] password for tc: 
mdadm: added /dev/sda


tc@Ubuntu:$ sudo mdadm --grow /dev/md0 --size=max
mdadm: component size of /dev/md0 unchanged at 3906886144K


tc@Ubuntu:$ sudo mdadm --grow /dev/md0 --raid-devices=4


tc@Ubuntu:$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sda[4] sdb[0] sdc[1] sdd[3]
      7813772288 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  reshape =  0.0% (297408/3906886144) finish=1313.4min speed=49568K/sec
      bitmap: 0/30 pages [0KB], 65536KB chunk


unused devices: <none>


tc@Ubuntu:$ sudo e2fsck -f /dev/md0
[sudo] password for tc: 
e2fsck 1.44.1 (24-Mar-2018)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/md0: 4280/244183040 files (0.1% non-contiguous), 966524122/1953443072 blocks


tc@Ubuntu:$ sudo resize2fs /dev/md0
resize2fs 1.44.1 (24-Mar-2018)
Resizing the filesystem on /dev/md0 to 2930164608 (4k) blocks.
The filesystem on /dev/md0 is now 2930164608 (4k) blocks long.




```

Remarks: The grow command with the --size=max didn't change anything so i tried the --raid-devices=4 command. I waited until the process was done before continuing to extend the file system. 

I had a look at gparted and everything looked like it should. After that I added the /dev/md0 to fstab again and rebooted the system. 

After the reboot my /data folder (where /dev/md0 is mounted to) is empty :-(  And gparted doesn't show /dev/sda as part of the raid setup anymore...

I assume I should have saved the new mdadm config? Is there a way I can still save my data?

Thanks

---

### Post by darkod on 2020-04-20
Let me see if I understand this right... You had all your data on sda, and created a 3x member raid5 with sdb, sdc and sdd. Then you copied the data onto the array and added sda to it, after which you started the grow/reshape process. Right?

Lets assume the above is right.

What you should have done:
1. Use partitions in mdadm, not whole disks. That means use sda1, sdb1, sdc1 and sdd1. Not the disks. It can work with disks directly but best practice is to use partitions.
2. I assume you couldn't add sda from the start because you had data on it. If that was the reason, the correct way to do it would have been to create 4x member raid5 with sdb, sdc, sdd and one missing member. Yes, mdadm allows you to do that. After that you would copy the data onto the array and simply added sda. You now have your 4x member raid5 without doing any reshape of a new array soon after creating it. Because the array would already be 4x raid5 when creating it so no reshape needed.

That is what you should have done. Now, about what you should do now. First is to give us more info of the current array state. Please post the output of these commands (in CODE tags for easier reading):
```
sudo mdadm -D /dev/md0
sudo mdadm -E /dev/sd[abcd]
```

Lets see what that tells us.

---

### Post by templeclause2 on 2020-04-21
Thank you very much for your remarks and help!

Yes you understood right, that's exactly what I did, live and learn :-)

1. Why would it be better to use partition and not whole disks? 
2. Exactly, all my data was on sda so I couldn't add it to the RAID. Didn't know you can do that with mdadm, I will keep that in mind for sure! 

```

/dev/md0:
           Version : 1.2
        Raid Level : raid0
     Total Devices : 3
       Persistence : Superblock is persistent


             State : inactive
   Working Devices : 3


              Name : UbuntuMediaServer:0  (local to host UbuntuMediaServer)
              UUID : 7dde1451:b5de3c53:1494b632:13c33969
            Events : 13615


    Number   Major   Minor   RaidDevice


       -       8       32        -        /dev/sdc
       -       8       48        -        /dev/sdd
       -       8       16        -        /dev/sdb



```

```

/dev/sda:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7dde1451:b5de3c53:1494b632:13c33969
           Name : UbuntuMediaServer:0  (local to host UbuntuMediaServer)
  Creation Time : Fri Apr 17 21:12:38 2020
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813776048 (3725.90 GiB 4000.65 GB)
     Array Size : 11720658432 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813772288 (3725.90 GiB 4000.65 GB)
    Data Offset : 261120 sectors
   Super Offset : 8 sectors
   Unused Space : before=261040 sectors, after=3760 sectors
          State : clean
    Device UUID : e3e4560c:fa052a66:cf829566:61a4e31e


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Apr 20 16:36:36 2020
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : 43e60b2e - correct
         Events : 13615


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7dde1451:b5de3c53:1494b632:13c33969
           Name : UbuntuMediaServer:0  (local to host UbuntuMediaServer)
  Creation Time : Fri Apr 17 21:12:38 2020
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813776048 (3725.90 GiB 4000.65 GB)
     Array Size : 11720658432 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813772288 (3725.90 GiB 4000.65 GB)
    Data Offset : 261120 sectors
   Super Offset : 8 sectors
   Unused Space : before=261040 sectors, after=3760 sectors
          State : clean
    Device UUID : f7b65c65:dd844735:a651ab32:926bd10c


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Apr 20 16:36:36 2020
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : 260cf22e - correct
         Events : 13615


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7dde1451:b5de3c53:1494b632:13c33969
           Name : UbuntuMediaServer:0  (local to host UbuntuMediaServer)
  Creation Time : Fri Apr 17 21:12:38 2020
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813776048 (3725.90 GiB 4000.65 GB)
     Array Size : 11720658432 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813772288 (3725.90 GiB 4000.65 GB)
    Data Offset : 261120 sectors
   Super Offset : 8 sectors
   Unused Space : before=261040 sectors, after=3760 sectors
          State : clean
    Device UUID : 10a12b53:5a4ce881:c007afae:ee7b7bc5


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Apr 20 16:36:36 2020
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : 952a6a3d - correct
         Events : 13615


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)



```

---

### Post by darkod on 2020-04-21
As you can see, md0 currently seems to try assemble as raid0 which is wrong.

Looking at the superblock info, it confirms sda is not marked as raid member right now, but no worry about that. The good part of the superblock info is that it has identical event counter for all three disks (13615) and they all say they are members of 4x raid5.

So now you should stop the current md0 and re-assemble it as raid5. After that you can mount it read-only and quickly check if you see the folders and files. After that unmount it again and add sda.

```
sudo mdadm --stop /dev/md0
sudo mdadm --assemble --verbose /dev/md0 /dev/sdb /dev/sdc /dev/sdd
```

If the assemble fails post the output here and do nothing else!

If it assembles correctly mount RO and check data quickly.

```
sudo mount -o ro /dev/md0 /mnt
ls /mnt
```

You can check the folders and files quickly, after that unmount and add sda:
```
sudo umount /mnt
sudo mdadm /dev/md0 --add /dev/sda
```

That should be it.

---

### Post by templeclause2 on 2020-04-21
I stopped, and assembled it with your command. This is the output. Not sure if that means it successful? Should I try to mount it?

```

sudo mdadm --assemble --verbose /dev/md0 /dev/sdb /dev/sdc /dev/sdd
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 2.
mdadm: added /dev/sdc to /dev/md0 as 1
mdadm: added /dev/sdd to /dev/md0 as 2
mdadm: no uptodate device for slot 3 of /dev/md0
mdadm: added /dev/sdb to /dev/md0 as 0
mdadm: /dev/md0 assembled from 3 drives - need all 4 to start it (use --run to insist).

```

---

### Post by darkod on 2020-04-21
Can you run again -D and show us details how the array is right now?

```
sudo mdadm -D /dev/md0
```

It was expected to assemble with 3 drives but not expected that it doesn't want to start. 3 out of 4 should be enough in raid5. Maybe it has some outstanding from the reshape. -D should show more info.

---

### Post by templeclause2 on 2020-04-21
Thank you so much for your help. 

This is what it returns:
```

mdadm: cannot open /dev/md0: No such file or directory

```

---

### Post by darkod on 2020-04-21
OK, my bad. The array is not even started so it can't give you details.

Right now you have two options:
1. Try to assemble the array by adding --run which will force it to start.
2. Try to assemble it with sda included too.

If the reshape terminated correctly, I would go with option 1. The mdadm -E shows sda outside of the array, so I would force it to start with only the three members that have identical event counters.

```
sudo mdadm --assemble --verbose --force --run /dev/md0 /dev/sdb /dev/sdc /dev/sdd
```

---

### Post by templeclause2 on 2020-04-21
I tried it with the --force and --run command and it worked :-) 

```

mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 2.
mdadm: added /dev/sdc to /dev/md0 as 1
mdadm: added /dev/sdd to /dev/md0 as 2
mdadm: no uptodate device for slot 3 of /dev/md0
mdadm: added /dev/sdb to /dev/md0 as 0
mdadm: /dev/md0 has been started with 3 drives (out of 4).

```

and details give me this

```

/dev/md0:
           Version : 1.2
     Creation Time : Fri Apr 17 21:12:38 2020
        Raid Level : raid5
        Array Size : 11720658432 (11177.69 GiB 12001.95 GB)
     Used Dev Size : 3906886144 (3725.90 GiB 4000.65 GB)
      Raid Devices : 4
     Total Devices : 3
       Persistence : Superblock is persistent


     Intent Bitmap : Internal


       Update Time : Mon Apr 20 16:36:36 2020
             State : clean, degraded 
    Active Devices : 3
   Working Devices : 3
    Failed Devices : 0
     Spare Devices : 0


            Layout : left-symmetric
        Chunk Size : 512K


Consistency Policy : bitmap


              Name : UbuntuMediaServer:0  (local to host UbuntuMediaServer)
              UUID : 7dde1451:b5de3c53:1494b632:13c33969
            Events : 13615


    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       3       8       48        2      active sync   /dev/sdd
       -       0        0        3      removed

```

I also mounted the array in read only and I can see my files :-D So I'm super happy already, thank you so much! 

How should we proceed? I guess I should backup my data first :rolleyes: 

And than start over and create the RAID with partitions instead of disks? So would I create an ext4 parition on each disk?

EDIT:
I think this would be my best approach:
[LIST]
[*]Back up the data to an external hard drive (need to buy one first)
[*]Reformat sda to an ext4 standalone drive
[*]Copy everything from /dev/md0 to sda
[*]Delete the raid configuration
[*]Create an ext4 partition on sdb, sdc and sdd
[*]Create an raid 5 on the newly created 3 partitions with 4 drives as you suggested
[*]Copy everything from sda to /dev/md0
[*]Format sda and create a new ext4 partion on it
[*]Finally add this new partion on sda to the RAID array
[/LIST]

And if anything goes wrong I always have my backup on the external drive. Could you point me in the right direction on how to create a RAID 5 array with mdadm with 4 disks but only add 3 at first? 

Thanks!

---

### Post by darkod on 2020-04-21
One correction, partitions for mdadm should NOT be formatted. Use a program like parted in terminal which only creates a partition with mkpart command without formatting it. Or any other partition manager but make sure you don't format it.

With mdadm the filesystem is on top of the array, in this case /dev/md0. That is why all partitions you use for mdadm on all disks should NOT have a filesystem.

You can keep the array as it is temporarily until you back up to external device, but do not forget that right now it is degraded like it says in -D. You already have one member missing. If another disk fails out of what ever reason, the array will stop.

---

### Post by templeclause2 on 2020-04-21
Okay got it :-) 

How can I tell mdadm to create a RAID 5 array with 4 disks but only add 3 for now? So I don't have to reshape the array.

---

### Post by darkod on 2020-04-21
In the --create command where you list the member devices at the end, normal would be "/dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1".

In your case use "missing /dev/sdb1 /dev/sdc1 /dev/sdd1". (without quotes, I just put the quotes to specify the last part of the --create command)

That keeps "empty" slot for sda1. Later simply adding sda1 will start the sync automatically and that's it.

---

### Post by templeclause2 on 2020-04-21
Thank you :-) 

Do I still need to resize the ext4 partion that I will create on /dev/md0 after I added sda1 or will that happen automatically as well?

---

### Post by darkod on 2020-04-21
No need, the raid5 array (and with that the filesystem on it) will have the correct size from the start. That is the benefit creating it as 4x raid5 from the start. Yes, one disk will be missing but that is OK for raid5.

For example for raid6 which can work with two broken disks, you can create mdadm array with two members missing from the start. As long as the minimum is there, it will work. And the array size is correct from the start, hence no reshape needed.

---

### Post by templeclause2 on 2020-04-21
Ah okay now I get it. Basically I will create a degraded RAID 5 array which would fail if one disc fails. Until I add sda, then it will be fully functional.

---

### Post by darkod on 2020-04-21
Exactly. That's the only way if you want the array size to be correct right from the start even though you have less disks to dedicate to it.

---

### Post by templeclause2 on 2020-04-21
I looked into parted but it's very unclear to me what kind of partitions I should create on the RAID disks, can you help me out?

---

### Post by darkod on 2020-04-21
Lets say we will start with sdb. To enter parted prompt you need to do:
```
sudo parted /dev/sdb
```

I usually prefer working with MiB so the first thing I set is unit to MiB.
```
unit MiB
```

At any time you can check the current partition table and info with print:
```
print
```

For example, here is an output from my server disk that you can compare:
```
Model: ATA HGST HUS726T4TAL (scsi)
Disk /dev/sda: 3815448MiB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start     End         Size        File system  Name  Flags
 1      1.00MiB   2.00MiB     1.00MiB                  GRUB  bios_grub
 2      2.00MiB   302MiB      300MiB      fat32        ESP   boot, esp
 4      302MiB    32770MiB    32468MiB                 ROOT  raid
 3      32770MiB  3815430MiB  3782660MiB               LVM   raid
```

Short explanation for the above list.
Partition 1 is small 1MiB partition for grub2 and legacy boot.
Partition 2 is 300MiB for EFI boot (ESP partition).
Partition 4 is 32GiB for raid1 for OS.
Partition 3 is the rest for raid1 for data.
As you can see none of the partitions have filesystem except ESP which works with fat32. Like we said before, mdadm partition are without filesystem, the md device is the one you format.

In your case you can create one big data partition because you do not plan to use these disks for OS/boot. If you prefer you can also create the 1MiB and 300MiB partition and simply leave them there, just in case. That decision is up to you. But on data disks they wouldn't serve much purpose.

So, in your case you currently have no partitions on sdb and doing print should just show you the basic disk info, total size in MiB and no partitions on it.

The start of the first partition should always be 1MiB and if you decide to make only one big partition, the end is towards the end of the disk. In my case I prefer leaving 15-20MiB unused at the end because in the future you may need to replace a failed disk and the new one might be few MiB shorter (depends on manufacturer and model). If you now use literary until the last MiB, and get little shorter disk in future, you won't be able to add it to the array because the partition will be little smaller. And in mdadm you can only add identical or bigger partitions, but not smaller.

As you see my disk has 3815448MiB but I set my last partition to end at 3815430MiB (18MiB unused at the end). Again, whether you want to do the same is your choice.

Once you make your decisions, creating partitions is easy.

If the print command does not show you already have gpt table, create one (the print command will throw an error message if you have no partition table):
```
mklabel gpt
```

To create one big partition, and lets say your numbers match my numbers (the END will probabaly not, adjust the value as per your case!!!):
```
mkpart primary 1 3815430
```

Put a raid flag on it:
```
set 1 raid on
```

Pur a descriptive name on it if you want:
```
name 1 RAID5
```

The last two commands above assume the partition number is 1, that you have created only one. You can check that with print at any time after mkpart, as I said. You simply use the correct partition number in the commands for set or name and that's it.

You should be ready now to exit the parted prompt:
```
quit
```

There will be a message that you might need to adjust fstab (because you were modifying partition tables) but ignore it. The new partition is ready to be used right away.

You do the identical steps on all disks and you are ready to go.

---

### Post by templeclause2 on 2020-04-21
Thank you very much for taking the time to write that detailed answer :-) Can't wait to try it out as soon as I backed up my data :-)

---

### Post by templeclause2 on 2020-04-25
Everything worked as expected :-) Thank you again! 

I was a bit confused at first when the recovery process didn't start after I recreated the array but than I realised that since it's degraded and missing one disk, it doesn't have to do anything.
As soon as I added the last partition the recovery process started and everything works as expected now :-)

---

### Post by darkod on 2020-04-25
No problem. Glad it all worked out good.

---

