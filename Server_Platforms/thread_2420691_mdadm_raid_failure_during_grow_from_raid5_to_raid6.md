---
title: "mdadm raid failure during grow from raid5 to raid6"
date: 2019-06-09
forum: Server Platforms
---

### Post by gtippitt on 2019-06-09
I am sorry if I am posting this in the wrong forum.  Most of the other past questions about MDADM raids seemed to have been posted here, and the answers to complicated MDADM questions seemed to get better answers here.

My server is running Ubuntu Mate 18.04.  I had a RAID5 with 5 drives and was trying to add 3 new drives, 3 spares, and grow it from raid5 to raid6 for more security.  The command was running, drive lights flashing, and everything looked copacetic, so I left it to do its thing and went to bed.  A few hours later during the night, a large SUV ran off the road knocking down an electric pole 2 blocks from my house, so I lost power.   The machine has a UPS battery backup that normally gets it through short hick-ups in power, but the power was out for a couple of hours while and I slept, and the server went down disgracefully.  

After the power came back up, the server failed to start correctly as I'd feared.  From the maintenance startup, I commented out the mount of the raid in my /etc/fstab, so that I could start the server without the raid causing errors.   I checked the MDADM details for the device, I'm getting a mess that I don't know how or if I can recover from.  I did lots of reading today, and the best solution I saw mentioned to a similar problem was to stop the raid and try to reassemble it, which didn't work.

[INDENT][FONT=Fixedsys] sudo mdadm --detail /dev/md127
/dev/md127:
           Version : 1.2
     Creation Time : Wed Jun 27 11:13:02 2018
        Raid Level : raid6
     Used Dev Size : 18446744073709551615
      Raid Devices : 8
     Total Devices : 8
       Persistence : Superblock is persistent

       Update Time : Fri Jun  7 02:47:36 2019
             State : active, FAILED, Not Started 
    Active Devices : 5
   Working Devices : 8
    Failed Devices : 0
     Spare Devices : 3

            Layout : left-symmetric-6
        Chunk Size : 512K

Consistency Policy : unknown

     Delta Devices : 2, (6->8)
        New Layout : left-symmetric

              Name : nas:raid2  (local to host nas)
              UUID : f57a5772:02fcbe49:d321a076:d3edcc74
            Events : 36590

    Number   Major   Minor   RaidDevice State
       -       0        0        0      removed
       -       0        0        1      removed
       -       0        0        2      removed
       -       0        0        3      removed
       -       0        0        4      removed
       -       0        0        5      removed
       -       0        0        6      removed
       -       0        0        7      removed

       -       8      112        0      sync   /dev/sdh
       -       8      193        5      spare rebuilding   /dev/sdm1
       -       8      177        6      sync   /dev/sdl1
       -       8      145        7      sync   /dev/sdj1
       -       8      128        3      sync   /dev/sdi
       -       8       81        -      spare   /dev/sdf1
       -       8       49        -      spare   /dev/sdd1
       -       8       96        4      sync   /dev/sdg
[/FONT][/INDENT]

In addition to the 8 drives listed above, there are 3 more 4TB drives (/dev/sd[ceh]) that were part of the raid before the power failure.  I tried including them in the "mdadm --assemble /dev/md127 /dev/sd[.....]" command, but I got an error that no superblock was found on them.  I have run SMART self-tests on all the drives, and none failed.  

The original 5 drives were about 18 months old.  Three of the drives that I was trying to add were brand new drives, and the other 3 had been used by a friend for about 2 to 3 years.  I had created a Linux Raid partition on the drives I was adding by attaching them to my UBUNTU laptop using a USB to SATA adapter before powering down my server to install them in its case.

If anyone can give me some ideas that might help me I would be deeply appreciative.  The 20TB of data isn't a matter of life or death, but it is a large collection of my music, photos, and videos I would hate to lose.  I'm not positive, but I'm fairly sure than the 5 drives with a state of "SYNC" above, are the original 5 drives in the raid5 array before I started the changes, so I'm hoping a majority of my data might still be there if I knew how to access it.

Thank you,
Greg

---

### Post by TheFu on 2019-06-09
I fear this is one of those instances where RAID is not a backup and only a backup will solve the problems with RAID.  I would wipe the RAID disks, assemble a new RAID set with the final configuration I want, then restore the data from my backups. You could fix the disks that don't have partition tables too.  

I am concerned that RAID1 isn't being used for huge HDDs. The best practice, recommended by enterprise storage experts, is not to use anything other than RAID1 or RAID10 for HDDs over 2TB in size.

I don't use RAID for media storage, only where HA is needed. Do have weekly backups of the media, however.  Definitely use RAID1 for running VM storage, where a failure would be very bad.  Used RAID5 for VM storage, when the disks were smaller than 500MB in size. 

When posting terminal output, please use "code tags" so it looks the same here.  That's in the "Advanced" editor, or you can manually wrap the text.

Also, because of the detailed nature of getting the commands correct, please show the EXACT, COMPLETE commands that you've attempted. Don't make us guess whether a mistake was made.

---

### Post by darkod on 2019-06-09
You first need to run --examine on all partitions/disks involved (whether before, currently or after the grow). That will show info of the mdadm superblock per device. And please stay consistent in using partitions, not whole disks as raid members, even if that means one big partition on the disk.

Run the examine with:
```
sudo mdadm -E /dev/sdXY
```

for each member. And post the output in code tags like already mentioned.

---

### Post by gtippitt on 2019-06-09
TheFu - Your comment regarding using mirrored RAID is what I wished I'd done, and good advice to others that may read this thread.  If I can't get this fixed, I may go back to working on my time machine, and when it's working, then I'll go back 18 months in time and set it all up differently.  On second thought, I'll go back and buy winning PowerBall lottery tickets, and put all of my data on cloud storage and let somebody else would take care of backing it up for me. ;-)

Darkod - I'm not sure why some of the drives don't have partition numbers.  I don't remember  which way the drives were before, but all of them have a single partition, and when I added the new drives, I used "/dev/sd?1" for the new ones on the "mdadm --add /dev/md127 /dev/sd?1 ...." command.  

```

root@nas:/home/gtippitt# mdadm -E /dev/sdc1
mdadm: cannot open /dev/sdc1: No such file or directory


root@nas:/home/gtippitt# mdadm -E /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x44
     Array UUID : f57a5772:02fcbe49:d321a076:d3edcc74
           Name : nas:raid2  (local to host nas)
  Creation Time : Wed Jun 27 11:13:02 2018
     Raid Level : raid6
   Raid Devices : 8

 Avail Dev Size : 7813774991 (3725.90 GiB 4000.65 GB)
     Array Size : 23441323008 (22355.39 GiB 24003.91 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 260096 sectors
     New Offset : 257024 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : bbf1a3d2:c16d0c94:718fe16b:c4b95e34

  Reshape pos'n : 116207616 (110.82 GiB 119.00 GB)
  Delta Devices : 2 (6->8)
     New Layout : left-symmetric

    Update Time : Fri Jun  7 02:47:36 2019
  Bad Block Log : 512 entries available at offset 264 sectors
       Checksum : 60136fc0 - correct
         Events : 36590

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : spare
   Array State : A..AAAAA ('A' == active, '.' == missing, 'R' == replacing)


root@nas:/home/gtippitt# mdadm -E /dev/sde1
mdadm: cannot open /dev/sde1: No such file or directory

root@nas:/home/gtippitt# mdadm -E /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x44
     Array UUID : f57a5772:02fcbe49:d321a076:d3edcc74
           Name : nas:raid2  (local to host nas)
  Creation Time : Wed Jun 27 11:13:02 2018
     Raid Level : raid6
   Raid Devices : 8

 Avail Dev Size : 7813774991 (3725.90 GiB 4000.65 GB)
     Array Size : 23441323008 (22355.39 GiB 24003.91 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 260096 sectors
     New Offset : 257024 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 161dad39:19ee2d3d:fd59c4b8:52f9bed0

  Reshape pos'n : 116207616 (110.82 GiB 119.00 GB)
  Delta Devices : 2 (6->8)
     New Layout : left-symmetric

    Update Time : Fri Jun  7 02:47:36 2019
  Bad Block Log : 512 entries available at offset 264 sectors
       Checksum : 5981258e - correct
         Events : 36590

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : spare
   Array State : A..AAAAA ('A' == active, '.' == missing, 'R' == replacing)


root@nas:/home/gtippitt# mdadm -E /dev/sdg
/dev/sdg:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4c
     Array UUID : f57a5772:02fcbe49:d321a076:d3edcc74
           Name : nas:raid2  (local to host nas)
  Creation Time : Wed Jun 27 11:13:02 2018
     Raid Level : raid6
   Raid Devices : 8

 Avail Dev Size : 7813777072 (3725.90 GiB 4000.65 GB)
     Array Size : 23441323008 (22355.39 GiB 24003.91 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 260096 sectors
     New Offset : 257024 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 32abc3ba:813f26a7:3f998c40:9855c591

  Reshape pos'n : 116207616 (110.82 GiB 119.00 GB)
  Delta Devices : 2 (6->8)
     New Layout : left-symmetric

    Update Time : Fri Jun  7 02:47:36 2019
  Bad Block Log : 512 entries available at offset 264 sectors - bad blocks present.
       Checksum : 8d5eb94e - correct
         Events : 36590

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : A..AAAAA ('A' == active, '.' == missing, 'R' == replacing)


root@nas:/home/gtippitt# mdadm -E /dev/sdh
/dev/sdh:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4c
     Array UUID : f57a5772:02fcbe49:d321a076:d3edcc74
           Name : nas:raid2  (local to host nas)
  Creation Time : Wed Jun 27 11:13:02 2018
     Raid Level : raid6
   Raid Devices : 8

 Avail Dev Size : 7813777072 (3725.90 GiB 4000.65 GB)
     Array Size : 23441323008 (22355.39 GiB 24003.91 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 260096 sectors
     New Offset : 257024 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 3ac1a869:0211b8c4:df2d1a43:fff4d7d2

  Reshape pos'n : 116207616 (110.82 GiB 119.00 GB)
  Delta Devices : 2 (6->8)
     New Layout : left-symmetric

    Update Time : Fri Jun  7 02:47:36 2019
  Bad Block Log : 512 entries available at offset 264 sectors - bad blocks present.
       Checksum : 9d75c3c1 - correct
         Events : 36590

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A..AAAAA ('A' == active, '.' == missing, 'R' == replacing)


root@nas:/home/gtippitt# mdadm -E /dev/sdi
/dev/sdi:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4c
     Array UUID : f57a5772:02fcbe49:d321a076:d3edcc74
           Name : nas:raid2  (local to host nas)
  Creation Time : Wed Jun 27 11:13:02 2018
     Raid Level : raid6
   Raid Devices : 8

 Avail Dev Size : 7813777072 (3725.90 GiB 4000.65 GB)
     Array Size : 23441323008 (22355.39 GiB 24003.91 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 260096 sectors
     New Offset : 257024 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ec2b853d:0e7a3ec8:22aa087f:44f165fd

  Reshape pos'n : 116207616 (110.82 GiB 119.00 GB)
  Delta Devices : 2 (6->8)
     New Layout : left-symmetric

    Update Time : Fri Jun  7 02:47:36 2019
  Bad Block Log : 512 entries available at offset 264 sectors - bad blocks present.
       Checksum : db550ffd - correct
         Events : 36590

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : A..AAAAA ('A' == active, '.' == missing, 'R' == replacing)


root@nas:/home/gtippitt# mdadm -E /dev/sdj1
/dev/sdj1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4c
     Array UUID : f57a5772:02fcbe49:d321a076:d3edcc74
           Name : nas:raid2  (local to host nas)
  Creation Time : Wed Jun 27 11:13:02 2018
     Raid Level : raid6
   Raid Devices : 8

 Avail Dev Size : 7813774991 (3725.90 GiB 4000.65 GB)
     Array Size : 23441323008 (22355.39 GiB 24003.91 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 260096 sectors
     New Offset : 257024 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a70a3768:e27da0f6:0094b888:8865d5bb

  Reshape pos'n : 116207616 (110.82 GiB 119.00 GB)
  Delta Devices : 2 (6->8)
     New Layout : left-symmetric

    Update Time : Fri Jun  7 02:47:36 2019
  Bad Block Log : 512 entries available at offset 264 sectors - bad blocks present.
       Checksum : fc88492a - correct
         Events : 36590

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 7
   Array State : A..AAAAA ('A' == active, '.' == missing, 'R' == replacing)


root@nas:/home/gtippitt# mdadm -E /dev/sdk1
mdadm: No md superblock detected on /dev/sdk1.


root@nas:/home/gtippitt# mdadm -E /dev/sdl1
/dev/sdl1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4c
     Array UUID : f57a5772:02fcbe49:d321a076:d3edcc74
           Name : nas:raid2  (local to host nas)
  Creation Time : Wed Jun 27 11:13:02 2018
     Raid Level : raid6
   Raid Devices : 8

 Avail Dev Size : 7813774991 (3725.90 GiB 4000.65 GB)
     Array Size : 23441323008 (22355.39 GiB 24003.91 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 260096 sectors
     New Offset : 257024 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : bf1c68ac:9294a91e:96076352:b7a324ca

  Reshape pos'n : 116207616 (110.82 GiB 119.00 GB)
  Delta Devices : 2 (6->8)
     New Layout : left-symmetric

    Update Time : Fri Jun  7 02:47:36 2019
  Bad Block Log : 512 entries available at offset 264 sectors - bad blocks present.
       Checksum : 40bc23b8 - correct
         Events : 36590

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 6
   Array State : A..AAAAA ('A' == active, '.' == missing, 'R' == replacing)


root@nas:/home/gtippitt# mdadm -E /dev/sdm1
/dev/sdm1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4e
     Array UUID : f57a5772:02fcbe49:d321a076:d3edcc74
           Name : nas:raid2  (local to host nas)
  Creation Time : Wed Jun 27 11:13:02 2018
     Raid Level : raid6
   Raid Devices : 8

 Avail Dev Size : 7813774991 (3725.90 GiB 4000.65 GB)
     Array Size : 23441323008 (22355.39 GiB 24003.91 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 260096 sectors
     New Offset : 257024 sectors
   Super Offset : 8 sectors
Recovery Offset : 38735872 sectors
          State : clean
    Device UUID : 69c2a00c:cc55b015:cc01ae65:54262ef9

  Reshape pos'n : 116207616 (110.82 GiB 119.00 GB)
  Delta Devices : 2 (6->8)
     New Layout : left-symmetric

    Update Time : Fri Jun  7 02:47:36 2019
  Bad Block Log : 512 entries available at offset 264 sectors - bad blocks present.
       Checksum : dc9f1771 - correct
         Events : 36590

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : A..AAAAA ('A' == active, '.' == missing, 'R' == replacing)
```

The commands for /dev/sdc1 and /dev/sde1 both failed, so I tried them as /dev/sdc and /dev/sde without the partition number and got output below.  While it shows they are part of the raid, the details for the raid don't list these 2 drives.
```
root@nas:/home/gtippitt# mdadm -E /dev/sdc
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4c
     Array UUID : f57a5772:02fcbe49:d321a076:d3edcc74
           Name : nas:raid2  (local to host nas)
  Creation Time : Wed Jun 27 11:13:02 2018
     Raid Level : raid6
   Raid Devices : 8

 Avail Dev Size : 7813776384 (3725.90 GiB 4000.65 GB)
     Array Size : 23441323008 (22355.39 GiB 24003.91 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 260096 sectors
     New Offset : 257024 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ff1eb221:32d38674:98854d57:570ad5a1

  Reshape pos'n : 116207616 (110.82 GiB 119.00 GB)
  Delta Devices : 2 (6->8)
     New Layout : left-symmetric

    Update Time : Thu Jun  6 17:20:10 2019
  Bad Block Log : 512 entries available at offset 40 sectors - bad blocks present.
       Checksum : e87fc95d - correct
         Events : 36577

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AA.AAAAA ('A' == active, '.' == missing, 'R' == replacing)


root@nas:/home/gtippitt# mdadm -E /dev/sde
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4c
     Array UUID : f57a5772:02fcbe49:d321a076:d3edcc74
           Name : nas:raid2  (local to host nas)
  Creation Time : Wed Jun 27 11:13:02 2018
     Raid Level : raid6
   Raid Devices : 8

 Avail Dev Size : 7813777072 (3725.90 GiB 4000.65 GB)
     Array Size : 23441323008 (22355.39 GiB 24003.91 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 260096 sectors
     New Offset : 257024 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 99bf484b:8fe18e81:ffd46bea:16e8af3a

  Reshape pos'n : 113055744 (107.82 GiB 115.77 GB)
  Delta Devices : 2 (6->8)
     New Layout : left-symmetric

    Update Time : Thu Jun  6 17:14:38 2019
  Bad Block Log : 512 entries available at offset 264 sectors - bad blocks present.
       Checksum : 4ab66ef5 - correct
         Events : 34592

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
```


For the /dev/sdk drive, I got errors for both the drive and the partition..  When I looked at the drive with gnome-disks, it shows the drive has an EXT4 partition rather than a Linux raid partition.  I don't know how that happened.  It is possible that when I was using "cfdisk" for deleting the partition tables and creating new ones on the drives I was going to add, I may have hit the wrong thing.  Alternatively, it is possible the drive is bad and when I tried to make those changes, they didn't didn't get saved.  I got some of the drives used, and didn't pay attention to what was on them before.  Whatever the reason, I'm going to ignore that drive and remove it from the machine later and not try to include it in the array.  It is not currently one of the drives that MDADM is showing in the --detail output for the raid.  

```

root@nas:/home/gtippitt# mdadm -E /dev/sdk
/dev/sdk:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)

root@nas:/home/gtippitt# mdadm -E /dev/sdk1
mdadm: No md superblock detected on /dev/sdk1.

```

I am sorry that I didn't remember the exact commands I have tried already to get it up back up again.  I did a lot of reading, and many of the suggestions to others with various problems including using a "--force" parameter for MDADM commands.  I HAVE NOT used the force parameter when trying to stop and [re]assemble the raid.  I knew that I didn't know what I was doing, so I did not want to try anything that might be destructive without first asking for advice from others more knowledgeable than myself.

I am sorry that when I posted my initial message, I couldn't find the "CODE" formatting option for the details on the raid, so I indented it and changed the font to fixed to make it a bit more readable.  Here is the detail again formatted in a code block:
```
root@nas:/home/gtippitt# mdadm --detail /dev/md127
/dev/md127:
           Version : 1.2
     Creation Time : Wed Jun 27 11:13:02 2018
        Raid Level : raid6
     Used Dev Size : 18446744073709551615
      Raid Devices : 8
     Total Devices : 8
       Persistence : Superblock is persistent

       Update Time : Fri Jun  7 02:47:36 2019
             State : active, FAILED, Not Started 
    Active Devices : 5
   Working Devices : 8
    Failed Devices : 0
     Spare Devices : 3

            Layout : left-symmetric-6
        Chunk Size : 512K

Consistency Policy : unknown

     Delta Devices : 2, (6->8)
        New Layout : left-symmetric

              Name : nas:raid2  (local to host nas)
              UUID : f57a5772:02fcbe49:d321a076:d3edcc74
            Events : 36590

    Number   Major   Minor   RaidDevice State
       -       0        0        0      removed
       -       0        0        1      removed
       -       0        0        2      removed
       -       0        0        3      removed
       -       0        0        4      removed
       -       0        0        5      removed
       -       0        0        6      removed
       -       0        0        7      removed

       -       8      112        0      sync   /dev/sdh
       -       8      193        5      spare rebuilding   /dev/sdm1
       -       8      177        6      sync   /dev/sdl1
       -       8      145        7      sync   /dev/sdj1
       -       8      128        3      sync   /dev/sdi
       -       8       81        -      spare   /dev/sdf1
       -       8       49        -      spare   /dev/sdd1
       -       8       96        4      sync   /dev/sdg

```

---

### Post by darkod on 2019-06-09
The only option I see is for you to try to recreate the array, using the --assume-clean parameter. You should always use that if you want to keep the data, otherwise --create can create a new blank array. I found a similar thread here:
[https://ubuntuforums.org/showthread.php?t=2012904](https://ubuntuforums.org/showthread.php?t=2012904)

The person there decided not to use --assume-clean but later did not confirm if the data was lost or kept.

You should also use the correct member order in the command, and you have that info in the mdadm --detail and mdadm -E. According to mdadm -E most of the members have identical event counters, which usually helps during multiple disk fail. Because this was a reshape fail, I'm not sure how it will react.

What was the exact command when it failed? Did you try to add spares and reshape at the same time? Always try to take it one step at a time. Knowing how many spares you had exactly might help you deciding whether to add spare parameter in the --create you try.

I will give you one example of the --create but don't just jump and run it. Take a loo, think and do some more investigation. I don't know your setup and what were you doing exactly when the power went off, so my command might be wrong. The only thing I am unsure about is the number of spares, because that would need to be integrated in the command too. Of course, if you run it as root forget the 'sudo' in front.

```
sudo mdadm --create --assume-clean --verbose /dev/md127 --chunk=512 --level=6 --raid-devices=8 /dev/sdh /dev/sdd1 /dev/sdf1 /dev/sdi /dev/sdg /dev/sdm1 /dev/sdl1 /dev/sdj1
```

If you had 2 or 3 spares on purpose, that command might need to look something like:
```
sudo mdadm --create --assume-clean --verbose /dev/md127 --chunk=512 --level=6 --raid-devices=6 --spare-devices=2 /dev/sdh /dev/sdd1 /dev/sdf1 /dev/sdi /dev/sdg /dev/sdm1 /dev/sdl1 /dev/sdj1
```

Don't forget that the number of members listed at the end of the --create (in your case 8) has to match the total of raid-devices + spare-devices. In your case I do not know if it was 6+2 or what.

PS. Your --detail output hints that maybe the relation between raid-devices and spare-devices is 5+3, however one of the spares shows state 'spare rebuilding' so I could not say if you should try with 5+3 or 6+2. That might depend mostly on the original command you ran for the reshape.

---

