---
title: "Slow Raid 5 Performance"
date: 2014-10-02
forum: Server Platforms
---

### Post by johnathan3 on 2014-10-02
I have recently bought 3 4TB drives to put into a Raid5 at first setup it was going great running like 90MB/sec i was happy with this and started to fill it with my media.

it is no about 50% full and my speeds have slowed to about 35 - 40 MB/s

I have a feeling this may be due to the way I Partitioned the drive when I started out, not really knowing anything about formating such large drives.
Here are some stats:

dd if=/NAS/Video/Vacation.mp4 of=/dev/null
3038030+1 records in
3038030+1 records out
1555471720 bytes (1.6 GB) copied, 33.0492 s, 47.1 MB/s

dd if=/dev/urandom of=/NAS/RwriteTest.del bs=64M count=20
20+0 records in
20+0 records out
1342177280 bytes (1.3 GB) copied, 244.348 s, 5.5 MB/s

dd if=/NAS/Video/Vacation.mp4of=/NAS/RandoFile.del
3038030+1 records in
3038030+1 records out
1555471720 bytes (1.6 GB) copied, 57.1956 s, 27.2 MB/s


/dev/md5:
        Version : 1.2
  Creation Time : Mon Sep 15 19:33:28 2014
     Raid Level : raid5
     Array Size : 7813768192 (7451.79 GiB 8001.30 GB)
  Used Dev Size : 3906884096 (3725.90 GiB 4000.65 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent
    Update Time : Thu Oct  2 15:21:39 2014
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
         Layout : left-symmetric
     Chunk Size : 512K
           Name : MediaVault:5  (local to host MediaVault)
           UUID : 594e4698:fd525be7:6ed6506a:a4878e38
         Events : 120
    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1
       3       8       65        2      active sync   /dev/sde1

All disks are the same as below
#lshw:

 physical id: 6
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST4000VN000-1H41
             vendor: Seagate
             physical id: 0.0.0
             bus info: [EMAIL="scsi@4:0.0.0"]scsi@4:0.0.0[/EMAIL]
             logical name: /dev/sde
             version: SC44
             serial: Z#######
             size: 3726GiB (4TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=ce2###2e-####-####-####-3a574e####9f sectorsize=4096
           *-volume
                description: EFI partition
                physical id: 1
                bus info: [EMAIL="scsi@4:0.0.0,1"]scsi@4:0.0.0,1[/EMAIL]
                logical name: /dev/sde1
                serial: 30####4-####-4aa9-####-efab8f####e8
                capacity: 3726GiB
                configuration: name=primary


#cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md5 : active raid5 sde1[3] sdc1[0] sdd1[1]
      7813768192 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
unused devices: <none>


I have also used a Raid 5 Tuneup script from another popular thread, it got me to the performance i have now, an increase of about 3MB sec.

I can attach the tune script if needed


Any Help with this would be great!.

---

### Post by Michael_McKenney on 2014-10-02
I have seen this many times before on RAID 5 as you get towards the outer sectors.  The parity writes and the sectors being futher apart on drives can degrade performance.  I usually do RAID 1 and 10 over RAID 5.  I have seen on high end RAID SCSI controller RAID 5 get 8 MB/s per drive average on writes.

---

### Post by johnathan3 on 2014-10-03
I only have 3 drives so, raid 10 is not possbile

---

### Post by Michael_McKenney on 2014-10-03
You would have to add a fourth drive.   The other suggestion is remove RAID 5 and run as JBOD or single drives.  Get a back drive for your data.

---

### Post by Vegan on 2014-10-03
Might be a better idea to use ZFS and cluster a larger number of disks

---

### Post by johnathan3 on 2014-10-06
I dont really want to invest more money into the server, it is not the most powerful thing in the workd and only has 4GB ram, i dont know if performance will be any better with ZFS. 
I did use ZFS previously (maybe 1.5 - 2 years ago) and alway ran into issues with it, so i gave up on it.

---

### Post by Michael_McKenney on 2014-10-06
Your options are another hard drive to do RAID 10 or do individual drives and backup nightly.

---

### Post by johnathan3 on 2014-10-06
Mainly I will be fine with my Setup, i just wanted to be sure that it was not how i Parttioned the disks or marked the chunk size or something like that.
I know my drives are 4K drives because they are new. so should i have a 4k chunk size or is the 512 size correct?
I want to actually learn what everything is in relation to each other and how they effect each other and why.

I cant really find good documentation explaining how to do this stuff and why. it is mostly just "do this and then do that for this specific setup" none of which is as my setup is.

---

### Post by Michael_McKenney on 2014-10-06
Physical sector size and RAID striping/chunk are two separate things.  In RAID you are setting up a stripe across the drive and breaking it into RAID chunks to improve performance across the drives.    

Three drives: So your stripes would look like this.  
1,2,P
P,2,3
1,P,3
1,2,P
P,2,3
1,P,3

P is parity 

You lose a drive, it can rebuild the stripe

1.) Two data chunks will recreate parity chunk
2.) Parity - Data Chunk = other Data Chunk


Chunk size is amount of data written to each disk.  64KB stripe on 4 disks is 16 KB chunk per disk.  In your three drive array, you have 2 data drives per stripe and one parity drive.  You are storing your files on two of three drives.  Smaller the chunk means more parity writes to manage.

Ex:
4800 KB file size 
16KB chunk is 300 chunks, 150 stripes and parity calculations to write the file.  
32KB chunk is 150 chunks, 75 stripes and parity calculations to write the file

In Windows, I use a 512 byte format so I get less slack per chunk.  Slack is the space that can't be used in a chunk.  512 byte means 32 blocks per 16KB chunk.  parity writes can slow performance of RAID 5 to a crawl.  Reads are great but write kill you.  On SCSI RAID, you can give Read % and Write % characteristic to a RAID controller.   On my SQL Servers, I give 62% write and 38% read.  I want data written faster to prevent lose of data and corruption of the data bases.  

Chunk size is based on your file size and do you do more reads or writes?  It is also based on number of drives in array.  You only worry about chunk size.  More stripes to write to more parity calculations so slow you down.  The disk head does operations in order.  On a highend SQL Server with 4 drives, you might want 256KB stripe with 64KB chunks per drive or 128KB stripe and 32KB chunks.  Same with a video server with huge movies.  On a document server with Office files, 32 KB Stripe with 8KB chunks.  I have 16 drive SCSI and SAS RAID 10 arrays.   Reads and writes are on both SCSI and SAS RAID 1 disks   simultaneously in RAID 10 pairs.  Most on-board SATA RAID controllers is one drive at a time.  

Stripe / # of drives = chunks.  Then, your OS format is sectors per chunk.  

So check out your data file sizes first to get an idea on your chunk size.

---

