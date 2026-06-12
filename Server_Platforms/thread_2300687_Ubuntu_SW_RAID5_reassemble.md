---
title: "Ubuntu SW RAID5 reassemble"
date: 2015-10-27
forum: Server Platforms
---

### Post by r-web on 2015-10-27
I have a Xubuntu LTS 14, which I use as Homeserver. And I'm a Linux amateur.
In this server, there are 1 (0.75TB) OS HDD, 1 (2TB) HDD (empty) and 6 (3TB) HDD which I united to a big SW-RAID5.

I works properly until a few days, I got the message that the Array I degraded. 
The Server missed one HDD, what is not a problem, because the RAID had a spare disc. 
But I want to find out which disc is demaged (and there a 6 identical discs), so I shut down the server, plugged out all of the 3TB HDDs and restarted. I passed the message, that it can't mount the RAID and then I plug in one by one HDD, to find out which HDD doesn't work (and I find out which one).
Then I shut up the server again, plugged in all HDDs except the damaged HDD and restarted. But at launching the OS it wont mount the RAID again and I aboard it again.

Then I thought, that I found an answer for this Problem:[URL="http://askubuntu.com/questions/621824/re-assemble-out-of-date-raid5"] re-assemble out-of-date raid5
[/URL]But now I'm very uncertain.

The RAID was shown as inactive:```
root@ChrisXu:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sdb1[4](S) sdf1[6](S) sde1[5](S) sdd1[0](S) sdc1[1](S)
      14650651962 blocks super 1.2
       
unused devices: <none>
```I try to start I, but then a few HDDs are gone:```
root@ChrisXu:~# mdadm --run /dev/md1
mdadm: failed to run array /dev/md1: Input/output error

root@ChrisXu:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sdb1[4] sdd1[0] sdc1[1]
      8790391177 blocks super 1.2
```Then I try to stop the RAID and want to assemble it:```
root@ChrisXu:~#  mdadm --stop /dev/md1
mdadm: stopped /dev/md1
root@ChrisXu:~# mdadm --assemble --scan --verbose
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sr0: No medium found
mdadm: no recogniseable superblock on /dev/sdg1
mdadm: Cannot assemble mbr metadata on /dev/sdg
mdadm: no RAID superblock on /dev/sdf
mdadm: no RAID superblock on /dev/sde
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda5
mdadm: no RAID superblock on /dev/sda4
mdadm: no RAID superblock on /dev/sda3
mdadm: no RAID superblock on /dev/sda2
mdadm: no RAID superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdf1 is identified as a member of /dev/md/1, slot 5.
mdadm: /dev/sde1 is identified as a member of /dev/md/1, slot 4.
mdadm: /dev/sdd1 is identified as a member of /dev/md/1, slot 0.
mdadm: /dev/sdc1 is identified as a member of /dev/md/1, slot 1.
mdadm: /dev/sdb1 is identified as a member of /dev/md/1, slot 3.
mdadm: added /dev/sdc1 to /dev/md/1 as 1
mdadm: no uptodate device for slot 2 of /dev/md/1
mdadm: added /dev/sdb1 to /dev/md/1 as 3
mdadm: added /dev/sde1 to /dev/md/1 as 4 (possibly out of date)
mdadm: added /dev/sdf1 to /dev/md/1 as 5 (possibly out of date)
mdadm: added /dev/sdd1 to /dev/md/1 as 0
mdadm: /dev/md/1 assembled from 3 drives - not enough to start the array.
mdadm: looking for devices for further assembly
mdadm: No arrays found in config file or automatically
```Now the RAID wasn't shown anymore:```
root@ChrisXu:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>
```But it was still there:```
root@ChrisXu:~# mdadm --examine /dev/sd*1
mdadm: No md superblock detected on /dev/sda1.
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c4236ee8:8d61ac08:65ddda03:efe37f21
           Name : ChrisXu:1  (local to host ChrisXu)
  Creation Time : Wed May 28 13:12:28 2014
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860260785 (2794.39 GiB 3000.45 GB)
     Array Size : 14650649600 (13971.95 GiB 15002.27 GB)
  Used Dev Size : 5860259840 (2794.39 GiB 3000.45 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e773c6da:5bde2d4b:a89d6660:bf39e13b

    Update Time : Tue Oct 27 17:49:14 2015
       Checksum : 5c04c7f2 - correct
         Events : 179188

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AA.A.. ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c4236ee8:8d61ac08:65ddda03:efe37f21
           Name : ChrisXu:1  (local to host ChrisXu)
  Creation Time : Wed May 28 13:12:28 2014
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860260785 (2794.39 GiB 3000.45 GB)
     Array Size : 14650649600 (13971.95 GiB 15002.27 GB)
  Used Dev Size : 5860259840 (2794.39 GiB 3000.45 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 736fa993:e492a83a:29224627:7b53fb34

    Update Time : Tue Oct 27 17:49:14 2015
       Checksum : c45c1640 - correct
         Events : 179188

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AA.A.. ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c4236ee8:8d61ac08:65ddda03:efe37f21
           Name : ChrisXu:1  (local to host ChrisXu)
  Creation Time : Wed May 28 13:12:28 2014
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860260785 (2794.39 GiB 3000.45 GB)
     Array Size : 14650649600 (13971.95 GiB 15002.27 GB)
  Used Dev Size : 5860259840 (2794.39 GiB 3000.45 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 550e928a:52a9a63c:41d08209:23bf6ade

    Update Time : Tue Oct 27 17:49:14 2015
       Checksum : 48eee550 - correct
         Events : 179188

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AA.A.. ('A' == active, '.' == missing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c4236ee8:8d61ac08:65ddda03:efe37f21
           Name : ChrisXu:1  (local to host ChrisXu)
  Creation Time : Wed May 28 13:12:28 2014
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860260785 (2794.39 GiB 3000.45 GB)
     Array Size : 14650649600 (13971.95 GiB 15002.27 GB)
  Used Dev Size : 5860259840 (2794.39 GiB 3000.45 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 72d5a03c:c43057f3:1ba92e5a:429736d6

    Update Time : Tue Oct 27 17:27:55 2015
       Checksum : fa2adfe0 - correct
         Events : 179184

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : AA.AAA ('A' == active, '.' == missing)
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c4236ee8:8d61ac08:65ddda03:efe37f21
           Name : ChrisXu:1  (local to host ChrisXu)
  Creation Time : Wed May 28 13:12:28 2014
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860260785 (2794.39 GiB 3000.45 GB)
     Array Size : 14650649600 (13971.95 GiB 15002.27 GB)
  Used Dev Size : 5860259840 (2794.39 GiB 3000.45 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : c3b1168a:74011eb5:1ebc3417:038c1521

    Update Time : Tue Oct 27 17:27:55 2015
       Checksum : 114c94a6 - correct
         Events : 179184

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : AA.AAA ('A' == active, '.' == missing)
mdadm: No md superblock detected on /dev/sdg1.
```Then I tryed (stupidly !?) parts of the other answer:```
root@ChrisXu:~# mdadm --zero-superblock  /dev/sd[bcdef]1
```And I don't know what happend:```
root@ChrisXu:~# mdadm --examine /dev/sd*1
mdadm: No md superblock detected on /dev/sda1.
/dev/sdb1:
   MBR Magic : aa55
Partition[0] :   1917848077 sectors at      6579571 (type 70)
Partition[1] :   1818575915 sectors at   1953251627 (type 43)
Partition[2] :           10 sectors at    225735265 (type 72)
Partition[3] :        51890 sectors at   2642411520 (type 00)
/dev/sdc1:
   MBR Magic : aa55
Partition[0] :   1917848077 sectors at      6579571 (type 70)
Partition[1] :   1818575915 sectors at   1953251627 (type 43)
Partition[2] :           10 sectors at    225735265 (type 72)
Partition[3] :        51890 sectors at   2642411520 (type 00)
mdadm: No md superblock detected on /dev/sdd1.
mdadm: No md superblock detected on /dev/sde1.
mdadm: No md superblock detected on /dev/sdf1.
mdadm: No md superblock detected on /dev/sdg1.
```

In the next step of the solutoin (from above) I should re-create the raid. But I don't want to lose any data:```
root@ChrisXu:~# mdadm  --create /dev/md1 --level=5 --raid-devices=6 --assume-clean /dev/sdb1  /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 missing
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid0 devices=0 ctime=Thu Jan  1 01:00:00 1970
mdadm: partition table exists on /dev/sdb1 but will be lost or
       meaningless after creating array
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid0 devices=0 ctime=Thu Jan  1 01:00:00 1970
mdadm: partition table exists on /dev/sdc1 but will be lost or
       meaningless after creating array
mdadm: /dev/sde1 appears to contain an ext2fs file system
    size=-1364702208K  mtime=Wed Jun 18 21:33:55 2014
Continue creating array? (y/n) n
mdadm: create aborted.
```Should I continue?


[SIZE=1]I also posted the same problem in an other forum: [x-post]("http://www.computerbase.de/forum/showthread.php?t=1526335&p=18041723#post18041723")[/SIZE]

---

### Post by darkod on 2015-10-27
It's too late in my time zone so I won't even start to explain how many mistakes you made....

In the --create --assume-clean command you need to get the disk order right, otherwise it won't work. Luckily you posted the --examine output before you destroyed the superblocks, so we can figure out the order of the disks. According to the Device Role parameter in the --examine, it seems the correct order of the five disks (without the faulty) is: sdd1-sdc1-missing-sdb1-sde1-sdf1.

So that --create command needs to be adjusted to something like:
```
mdadm --create /dev/md1 --assume-clean --level=5 --raid-devices=6 /dev/sdd1 /dev/sdc1 missing /dev/sdb1 /dev/sde1 /dev/sdf1
```

Hopefully that will get the array going... And replace the faulty disk as soon as possible because in raid5 you have no redundancy when one member already failed and is missing. If you don't know how to add the new disk ask first after you buy it.

---

### Post by r-web on 2015-10-28
Thank you very very much!

I couldn't sleep, so I try what you wrote and it worked :)
Over night I checked the filesystem and the HDDsa and everything is fine.

Maybe you can help prevent, that a problem like this happens again.
How can I find out which (physical) HDD is broken?
At '*mdadm --detail /dev/md1*' I only see, that a disc is missing. The same with '*lsscsi*' (the port numbers are wrong) or '*hdparm -i /dev/sdc | grep SerialNo=*'.
Because there are 6 identical disc in the server and the serialNo I can't see. The disc are to close to each other.

Right now I order a new disc. I would change the disc the flowing way:
```
parted /dev/sdg mklabel gpt # the old disc isn't connected anymore, so I format the new this the same way I formated the other discs
parted -a optimal -- /dev/sdg mkpart primary 2048s -8192s
parted /dev/sdg set 1 raid on

mdadm /dev/md127 --add /dev/sdg1 # add the new psrtition
cat /proc/mdstat # it shows me how long it needs to sync
```Is that ok?

Thanks for the quick help, late at night. Muchos saludos!

---

### Post by darkod on 2015-10-28
mdadm --detail should show you which member is missing and hdparm will help you get the SN. Once you have the SN, it's easy even if you can't read the numbers easily because the disks are close.

You will power down the machine, and try to read the SN of the disks. If it's not possible, you can start dsiconnecting disks one by one until you find the correct disk. But you will be doing this all at once while the machine is powered off. You will not boot the machine with one disk at a time. After you find the correct disk, you will take it out and leave the other connected, and only then boot the machine. That way it will boot with all the remaining disks present, not with one by one.

Also, the naming of the disk devices (sda, sdb,sdc,...) goes in order usually from first SATA port towards the last. For example, if you have a board with 8 ports and they are labelled SATA0-SATA7, /dev/sdc will be the third disk in the order. So if you have SATA0, SATA1 and SATA2 used the /dev/sdc should be in SATA2. You should check that port first if that's the SN you are looking for.

About the commands to replace the disk, they look ok to me. Just for the mkpart command make sure you use the same start/end sectors as in the other disks. The partition has to be equal (or bigger) to the others.

---

