---
title: "I overwrote my RAID5, is it possible to get my data back?"
date: 2015-03-07
forum: Server Platforms
---

### Post by jonathon-2000-uk on 2015-03-07
I'm trying to fsck a 5 x 3tb raid 5 array, lets just say there has been a few creates and wayward fsck's done all ready :(
 But currently I'm trying to run fsck on a configuration and it is using a very large amount of swap. I'm having to stop it after the first 6 hours and 1 million inodes as it has filled 400gigs of swap memory, however I can stop it and when I restart it, it will continue from where it left off, and seems to consume swap more slowly each time I do.

 I've started using an overlay but I had all ready done the damage before doing so ;(

 So I'm wondering if this is just a memory leak and more ram would help? (I currently have 8G) or if  actually just needs that much swap?
 I don't have any backups of the data, and there was a fair bit of it on there before I took the bad advice of using create to re-add a failed drive without backing up the old configuration, so I guess I'm also wondering if the time its taking means it is finding and recovering my data or if something else is happening?

 
I'm using mdadm with an ext4 partition.
 Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
fsck from util-linux 2.20.1

Any help would be much appreciated,

 Thanks Jonathon.

---

### Post by tgalati4 on 2015-03-07
Welcome to the forums.

It's possible that you are hitting some limits to what *fsck* can do on a large data volume.  You can try using the -V switch to get verbose output and see what is happening.  Keep your finger on the scroll-lock key so you can pause the output and write down some useful messages.

What RAID hardware are you using?  Some RAID hardware have a BIOS troubleshooting mode that you can perform repairs depending on what failed.

If this was a ZFS pool that you were checking, you would need around 12 GB of RAM to scrub the pool.  I would imagine that *fsck* needs a similar space to expand the inode tree during the check.  That fact that you are using swap means you have run out of RAM.  Can you put in 16 GB of RAM?

400 GB of swap seems excessive, considering only 8 GB of RAM,  When swap exceeds 2X RAM, you need to rethink your workload.

Trying to rescue a RAID without a backup is risky.

---

### Post by jonathon-2000-uk on 2015-03-07
Oh right yeah sorry, should have included a few more details.
Its just software raid, mdadm, and its a ext4 partition.
I can just about afford to buy another 8G ram, but of course am hesitant, as given the swap usage I wasn't sure if it was a bug or just due to the partition size, so don't know if it would solve or even help the issue.
And I increased the swap to 500G to see how fsck would respond as it was exiting with "can't allocate memory."
But theres are a lot of errors, seemingly for each inode, is there something other than that I should look out for?
I'm also using a page file rather than a partition, I don't know if that makes any difference?
Any insight into what this fsck behaviour means would be much aprecaited.

Thankyou Jonathon

---

### Post by tgalati4 on 2015-03-08
Normally in this situation, I would follow the recommendations from several tutorials:

[https://raid.wiki.kernel.org/index.php/RAID_Recovery](https://raid.wiki.kernel.org/index.php/RAID_Recovery)

[https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)

Why are you performing an *fsck* on this RAID?

---

### Post by jonathon-2000-uk on 2015-03-08
_Long Story Short;_
 I **REALLY** should have read that wiki first, but I did a create with the wrong configuration and am now trying to recover my data, as I have no backups of the original array configuration and the array was my data backup.
 So am trying to figure out what this fsck behaviour may be an indication of?

Thanks Jonathon

 

 _The Long Story;_
 I had a failed drive that kept getting marked as spare when I tried to re-add it to the array. (Was just a failing cable in the end!) Then I took the bad advice of using mdadm create to try and re-add it without knowing and there being no mention of how important keeping the same settings are and with no backup of what they where.
 And alas I didn't come across that wiki until long after,
 “Recreating should be considered a *last* resort, only to be used when everything else fails. People getting this wrong is one of the primary reasons people lose data. It is very commonly used way too early in the fault finding process.”
 was unfortunately too late for me.
 But as I said, I have no backup for the data, which is why I'm having to keep trying to recover it.
 So I guess I'm wondering if this fsck behaviour is a sign that I've screwed things up long beyond repair?
 Originally I was just using the default settings with a sequential drive order, I know that sda was the first drive, as its the one that failed and I'm almost certain the next 2 are sequential as I originally made a 3 drive array, and would have put them sequentially, but the 4[SUP]th[/SUP] an 5[SUP]th[/SUP] may not have been, so I tried [abced] but both these times fsck would fail at the same point with failed to allocate memory errors.
 I made the array in January 2013 so I've tried creating the array with a 1meg data offset. With the drives in sequential order fsck completed, and there was a clean partition, but there was only 500meg of data when I had close to 7TB. So currently I'm trying [abced] with a 1meg data offset which is where I currently am.
 And I only set up the overlay at this point!
 None of the backup super blocks are accessible any more. And I've tried recreating the array with the current default data offset and the super block isn't accessible there at all any more?
 So I kept re-running fsck as it was moving a little further every time and I was hoping that it was just because of the amount of data I had. But once it reached 50mil inodes (seemed to be complaining solely about invalid extent nodes) it started exiting with illegal extent nodes and complaining about bad blocks. I tried the array with each disc missing in the array, so its not a failing disc.
 I created an overlay at this point so I could test mke2fs -S.
 But this means fsck is starting from the beginning again and using all that swap again.
 And I'm wondering if I've just completely screwed it all up by this point.
 As I said, I have no backups, as the raid was for backup (and yes I know taking advice on some forum before complete research was stupid, and currently its turning about to be a very costly reminder) so I guess I'm just trying to find out if there's any chance what so ever of recovering my data.  
 What does this fsck behaviour likely mean? And if I have to move pass the bargaining stage of loosing all my stuff and move into the depression stage? >.<
 Cause naturally if its just a matter of time, and to just keep re-running it till completion, I will continue if it actually has a chance of recovering my data.

Thankyou Jonathon

---

### Post by tgalati4 on 2015-03-08
It doesn't sound like *fsck* will recover your data.  It was not designed as a robust RAID recovery tool, but simply checks for file consistency by going through each inode and following its block chain.  Why it's consuming all of that RAM is a mystery, but probably because it has encountered errors and is traveling around the array looking for blocks and that takes a lot of time and RAM.

At this point, I would perform a non-destructive *badblocks* on each drive individually to see if one drive is physically failing.  Mark that drive and then research what other options are available.

So, to the best of your knowledge, you reassembled the RAID5 with drives 4 and 5 reversed, and that perhaps messed up the striping on the drive.  I'm pretty sure *mdadm* keeps the correct drive order by using UUID's for each drive.  What was the very first error that you encountered?

The troubleshooting steps from the links above (and that is only 2 of several) require some data, so let's see what we can see.  How about the RAID block status for each drive:

```
mdadm --examine /dev/sdb1 >> raid.status 
```  Repeat for each drive.  Then post.

---

### Post by jonathon-2000-uk on 2015-03-09
As I understand it, the drives superblock is overwritten when you do mdadm create, hence the predicament I'm in now, I used create rather than assemble :(
 And I didn't keep a backup of the old drive information because I'm an idiot and didn't realise it was important.

I re-created using the default settings and abcde, so it defaulted to 128 MiB Data Offset. And I believe fsck exitied with 'failed to allocate memory' error, as it did with abced order. I then read about the change in the default data offset and have set it to 1 MiB since, but still get 'failed to allocate memory' errors. Except with abcde, 1 MiB offset, where it failed to find all but a few megs of my data. It doesn't even find the superblock now if I re-create with the 128 MiB Data Offset?

 Do you mean badblocks with the -n option? I've run it with just -v on 3 of the drives, checking the last 2 now, I've been hesitant to run it with n as this takes 2 days on a 3tb drive and is rather intensive.
 
 And bear in mind I have moved the cables around now, so the root drive is now at sda and I swapped the cables around for what was sde and sdd, so they are now sde and sdf respectively.
 
I'm well aware I've got myself into a royal mess  :(
Thankyou Jonathon

 ```
/dev/sdb1:

           Magic : a92b4efc
         Version : 1.2
     Feature Map : 0x0
      Array UUID : e4e2814d:0c7f706e:29c3c664:170bb120
            Name : Theodore:0  (local to host Theodore)
   Creation Time : Sat Mar  7 18:37:29 2015
      Raid Level : raid5
    Raid Devices : 5
 

  Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
      Array Size : 11721056256 (11178.07 GiB 12002.36 GB)
     Data Offset : 2048 sectors
    Super Offset : 8 sectors
           State : clean
     Device UUID : 44e45eea:cb7a9c92:1f78f0bb:08805b3e
 

     Update Time : Sat Mar  7 18:37:29 2015
        Checksum : 9b4f95ca - correct
          Events : 0
 

          Layout : left-symmetric
      Chunk Size : 512K
 

    Device Role : Active device 0
    Array State : AAAAA ('A' == active, '.' == missing)
 /dev/sdc1:
           Magic : a92b4efc
         Version : 1.2
     Feature Map : 0x0
      Array UUID : e4e2814d:0c7f706e:29c3c664:170bb120
            Name : Theodore:0  (local to host Theodore)
   Creation Time : Sat Mar  7 18:37:29 2015
      Raid Level : raid5
    Raid Devices : 5
 

  Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
      Array Size : 11721056256 (11178.07 GiB 12002.36 GB)
     Data Offset : 2048 sectors
    Super Offset : 8 sectors
           State : clean
     Device UUID : d9c721c2:0f42a9ec:3d5f07f7:da643ba0
 

     Update Time : Sat Mar  7 18:37:29 2015
        Checksum : 6a160c95 - correct
          Events : 0
 

          Layout : left-symmetric
      Chunk Size : 512K
 

    Device Role : Active device 1
    Array State : AAAAA ('A' == active, '.' == missing)
 /dev/sdd1:
           Magic : a92b4efc
         Version : 1.2
     Feature Map : 0x0
      Array UUID : e4e2814d:0c7f706e:29c3c664:170bb120
            Name : Theodore:0  (local to host Theodore)
   Creation Time : Sat Mar  7 18:37:29 2015
      Raid Level : raid5
    Raid Devices : 5
 

  Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
      Array Size : 11721056256 (11178.07 GiB 12002.36 GB)
     Data Offset : 2048 sectors
    Super Offset : 8 sectors
           State : clean
     Device UUID : d8cc3756:3591b451:27105c7d:183aeb17
 

     Update Time : Sat Mar  7 18:37:29 2015
        Checksum : 613be6e1 - correct
          Events : 0
 

          Layout : left-symmetric
      Chunk Size : 512K
 

    Device Role : Active device 2
    Array State : AAAAA ('A' == active, '.' == missing)
 /dev/sde1:
           Magic : a92b4efc
         Version : 1.2
     Feature Map : 0x0
      Array UUID : e4e2814d:0c7f706e:29c3c664:170bb120
            Name : Theodore:0  (local to host Theodore)
   Creation Time : Sat Mar  7 18:37:29 2015
      Raid Level : raid5
    Raid Devices : 5
 

  Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
      Array Size : 11721056256 (11178.07 GiB 12002.36 GB)
     Data Offset : 2048 sectors
    Super Offset : 8 sectors
           State : clean
     Device UUID : db67cb49:cd4cc26b:1c7feb9b:6a4b3506
 

     Update Time : Sat Mar  7 18:37:29 2015
        Checksum : 7bb6bdc4 - correct
          Events : 0
 

          Layout : left-symmetric
      Chunk Size : 512K
 

    Device Role : Active device 3
    Array State : AAAAA ('A' == active, '.' == missing)
 /dev/sdf1:
           Magic : a92b4efc
         Version : 1.2
     Feature Map : 0x0
      Array UUID : e4e2814d:0c7f706e:29c3c664:170bb120
            Name : Theodore:0  (local to host Theodore)
   Creation Time : Sat Mar  7 18:37:29 2015
      Raid Level : raid5
    Raid Devices : 5
 

  Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
      Array Size : 11721056256 (11178.07 GiB 12002.36 GB)
     Data Offset : 2048 sectors
    Super Offset : 8 sectors
           State : clean
     Device UUID : 1f34e7f9:953da644:9ff6a904:57c24e30
 

     Update Time : Sat Mar  7 18:37:29 2015
        Checksum : 978e6941 - correct
          Events : 0
 

          Layout : left-symmetric
      Chunk Size : 512K
 

    Device Role : Active device 4
    Array State : AAAAA ('A' == active, '.' == missing)
```

---

### Post by tgalati4 on 2015-03-09
I missed the "create" in the previous post.  So you have effectively created a new RAID5 array over your existing RAID5 array.  That will generally destroy data in a profound way.

No, you normally don't need to use *badblocks -n*, just a simple *badblocks* run will demonstrate that the disk is spinning properly and that the read head can read the entire surface.  I would only use the -n switch for isolating the problem of a specific drive that you suspect is having problems and you don't care about the data on the drive because you have a backup.  It does take longer.

Back to your problem at hand.  Your current RAID status looks OK, which is good, that means that you can at least use the RAID array again in the future.  I guessed that it would be 12 TB with 15 TB of disks and that seems to be the case.

I would change the title of this thread to "I overwrote my RAID5, how do I get my data back?"  the current title about *fsck* using excessive swap is really not the problem we are dealing with here.

It's possible that you will need to purchase a data forensics tool (for Windows) to recover data from this broken array.

[http://www.diydatarecovery.nl/kb_raid5_article.htm](http://www.diydatarecovery.nl/kb_raid5_article.htm)

And 

[http://www.diydatarecovery.nl/FAQ_RAID_recovery.htm](http://www.diydatarecovery.nl/FAQ_RAID_recovery.htm)

Notice that I am now just going through the steps suggested here.  Recreating an array over a damaged array causes more damage and makes recovery difficult.  The fact that no one else has contributed to this thread is instructive.

It's possible that *testdisk* could reassemble the previous RAID5 and that would be the best possible outcome, but I have no experience using *testdisk* in this Use Case.  Perhaps others have and can weigh in.

Regardless, spend some time reading:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Prepare yourself to build another machine with at least 12 TB of disks to receive the data.  How full was the array?  

If you don't want to build a second machine, then you would need about 375 32GB USB sticks.

---

### Post by jonathon-2000-uk on 2015-03-09
Yeah I was just hoping the fsck behaviour was a clear indicator of something, with a simple answer, and that I hadn't messed things up as bad as I thought I had. And didn't want to start off the bat with the entire mess I've made.
 Obviously if I can't really afford an extra 8gb ram stick then I can't afford a second pc.
 But yes, I was hoping it might just be a fsck problem, so I'll rename the thread to make my problem clearer, I did think it all a long shot but without any other backup there&#8217;s not a lot else I can do? :(

Thanks Jonathon

---

### Post by tgalati4 on 2015-03-09
Well, 3TB drives are around $150 each and you would need 4 of them to get 12TB to perform a straight reimage (JBOD) of the orginal dataset.  That's $600.  Otherwise your only recourse is to perform some read-only probes on your current array to see what you can see.

Try running *testdisk* on the current array and see what it says.  Read up on it first.  There are a few folks who have used it successfully on RAID5.

---

### Post by MAFoElffen on 2015-03-11
I use a lot of RAID and do a lot of RAID Testing. This is going to sound like hindsight at this point, but maybe this example will help others before this happens again--

I keep saying this, but will say it again... RAID is not a substitute for a good backup. It is a container with some very good fault tolerant, but even then, you should have backing up those arrays as an active piece of your recovery plan. The importance of this comes to the forefront when something goes south.

At the next condition, it doesn't matter if it is RAID or not... If you have something that does go wrong and don't have a backup... That time would be the smart time to consider imaging your disks, so you have a sanpshot of a point in time to possible get back to. As you start making changes to the filesystem and/or container... the potential chances each way expand greatly for success or not.

If you overwrite what you have... Let me say it this way, Deleting a file just clears an entry in the partition table. If a container such as a partition, LVM group or RAID container have troubles (early on, before major changes) everything is there, if the configuration or definition can be restored for that. But when you overwrite what is there-- That is what we effectively use to make data inaccessible, when we clear or initialize disks (a security wipe).

It's not that It doesn't happen. It's not that I cannot empathize with you and feel your pain. I can. It reoccurs here many times a week (much too often). It has happened to me and I made mistakes. I am not perfect and was humbled. Since then, I hope I have learned by my own mistakes, from what toehrs have taught me, and can share to others how not to have to go through that... and if so, how to go about trying to recover.

But a backup at some point will take you a long way and save much frustration. Now if you don't care about that... like I think you mentioned, the data was just a backup of other data... If so, then why stress on recovering a backup of a backup? Just recreate an empty array and take another backup of your data, right?

---

### Post by jonathon-2000-uk on 2015-03-11
Yeah sorry when I say it was the backup, I mean its where I was putting my data for safe keeping, but I have no copies of what I was storing on there. Nor could I afford to, mirroring or say raid 10 of course more than doubles the cost.
 And I recognise that some basic steps, like using an overlay, should have been implemented far, far earlier in the recovery process.
 This has all been a very hard lesson, and I've now learnt a lot that would have saved me had I known it before, especially for me that line from the wiki bears repeating;
 &#8220;Recreating should be considered a *last* resort, only to be used when everything else fails. People getting this wrong is one of the primary reasons people lose data. It is very commonly used way too early in the fault finding process.&#8221;
 And just some simple steps like keeping a backup of the raid configuration.
 So at the moment, I'm just working to try and mitigate the cost of that lesson.
 And hopefully others will stumble upon that wiki, or these pages, before taking action. As I wish I had done.
 

 But I've run badblocks on all the drives now, and it reported no problems. I'm running testdisk now to see what it can find, but its mostly finding a lot of &#8220;ms data&#8221; but I haven't run a deep scan yet.
 Do you know if I should be searching for Intel or GPT partitions? I know that msdos partitions, which I think comes under the intel/pc category, doesn't support physical dives over a certain size, but since raid is a loop device I'm not sure what category it falls under? I've been searching GPT so far.
And is there a way to find out what version of mdadm would have likely been installed through the ppa in January of 2013? I'd have been using Ubuntu 12.10 and what ever version of mdadm that would have been installed through the package manager, judging by this;
[https://launchpad.net/ubuntu/+source/mdadm](https://launchpad.net/ubuntu/+source/mdadm)
it would have been 3.2.3, but I'm not sure how detailed it is, and am guessing its likely a lot more complicated than that to find out?

Thanks Jonathon

---

### Post by tgalati4 on 2015-03-11
Unfortunately, to get *testdisk* to work correctly, you need to break the RAID once again.  Since you performed a create, you have a new RAID5 with correct striping.  Perhaps a deep scan will get you closer, but you need to give *testdisk* something to fix.  Because you don't have an image of the degraded array, you are now working on the only copy of the data and that increases the risk of destroying more data as you go through this repair process.

One way to break the current, clean array is to find all of the superblocks and overwrite them with a hex editor.  Then let *testdisk* do it's thing.  If *testdisk* can't find a valid file system structure to resurrect, then use *photorec* to find individual files.  Of course it may only find 32KB files or whatever the minimum block size is.  At least you get the thumbnails of all the photos that you have lost.  It's like finding coffee mugs in a house that has completely burned down.

It's possible the previous *fsck* attempts have totally munged your data.  If you selected "automatically fix errors" then that is quite possible.

---

### Post by jonathon-2000-uk on 2015-03-12
So I should be using testdisk to try and recover the original raid superblocks on the drives?
 

 And yes, I have been using fsck -y, hence it being the focus of my original question. And asking if its a sign of irreparable damage, a bug, or a sign its just finding a lot of data?
 

 Thanks Jonathon

---

### Post by tgalati4 on 2015-03-13
If you had a 400 GB swap, then I doubt *fsck* was repairing the file system in a coherent fashion.  If you had a lot of orphaned inodes (pieces of files that can't be found while going through the block chain), *fsck* will simply delete them.  And that causes damage because it is deleting possibly valid file chains.  Because of the way the RAID5 was handled, it's possible that the entire array had missing files--which happens when you have two drive failures since the parity blocks can't rebuild from the loss of two drives.

So the extensive *fsck* activity was possibly due to the deleting of every orphaned inode which is every file larger than the block size.

Try using *photorec* and see what file pieces are recoverable.

*Testdisk* will try to use backup superblocks to rebuild the file system, which is why you want to delete the current superblocks from the newly-created RAID5.  Like I said, you need to break the RAID in a coherent fashion in order for *testdisk* to have a chance to rebuild the older RAID.

What did *photorec* find?

---

### Post by jonathon-2000-uk on 2015-03-13
I've been running photorec for the last half hour on the md device and its filled about 11gb in the recovery folder. The files seem broken and fragmented though. Looking through some of the text files, they seem to be broken up into pieces, a few video file have been recovered but they will play for a moment or 2 then jump forward, or are missing the video, but some small jpegs seem intact, larger ones have the black bars across half of them. Its recovered some mp3s but again their split up into pieces? And no file names.
 Could that be caused by the drive order still being wrong?

As a bit of an aside, heres an example of what I mean,

f1510253158.txt reads;
```
fication area,
 volume controls and the battery charge indicator, and utilities ranging
 from weather forecast to system monitoring.
 .
 This package contains the MATE Panel applet library.

Package: libmate-panel-applet-dbg
Description-md5: 1471255c76c6d0bb134423572c01783f
Description-en: library for MATE Panel applets (debugging symbols)
 The MATE Panel is an essential part of the MATE Desktop, providing
 toolbar-like 

```

and the next file, f1510253160.txt, reads;
```
-en: library for MATE Panel applets (development files)
 The MATE Panel is an essential part of the MATE Desktop, providing
 toolbar-like 

```

---

### Post by tgalati4 on 2015-03-13
That is precisely what I mean.  Small files that fit on one stripe (block) on one drive can be recovered.  Larger files like music and videos will have gaps.  You can reassemble those files if you have patience.  It's like a giant jigsaw puzzle.  

I don't think the drive order munged your files, since each drive has a UUID and the RAID assembly uses UUID's to order the drives correctly.  The combination of create (making a new RAID over an existing RAID) and using *fsck* with "yes" is a sure-fire way to destroy your data in a fashion that you seeing.

---

### Post by jonathon-2000-uk on 2015-03-13
Ah, I was labouring under the assumption that the drive order was determined by the order you used in the create command, and that this is where I was messing up. Well, that and the data offset.
 There wasn't really anything on my array, that was under a few kb, that had any value. And reassemble seems rather insurmountable.


 Its feeling like I'm coming to the point of termination? That there's really nothing I can do to fix what I did?

Damn, a lot of what I read online indicated that the drive order is extremely important and is affected by the order you use in the mdadm commands. But photorec seems to find the exact same (broken) files whether I scan the array, or the individual drives. And the drive order currently only seems to affect whether or not it can find the arrays superblock, there does seem to be a slight difference in the files it recovers based on drive order but I haven't figured out any pattern to it.
 I'm not even sure how you could go about finding and reassembling files from the pieces spread across the drives?
 So I'm at a complete loss, and it seems there's no further I can go?
 

 Thanks Jonathon :(

---

### Post by tgalati4 on 2015-03-14
If you read about how the data is stored in a RAID5 and then individually on each drive, each file is stored on individual sectors in a continuous chain.  When the chain is broken, typically the last 2 bytes of the sector give the address of the next sector in the chain.  So if you use a hex editor you can jump around the disk and follow the chain.  This is what *photorec* does.  It also analyzes the first few lines of the file to classify it as an mp3, a video file, a text file, etc.

Drive order is important to RAID5, but software RAID created by *mdadm* will use UUID to assemble the correct order.  If you move the cables around, reboot and reassemble, then the RAID5 array should come up normally.  What you can't do is perform a create over an existing pool.  That will destroy data in a profound way.

The only better tools are expensive, Windows-only, forensic tools, or send your disks out to a service ($3K to $10K) and they will do what I described--if they can.

If you search around, several others have had problems with trying to recover data from a failed RAID5:

[http://serverfault.com/questions/538904/mdadm-raid5-recover-double-disk-failure-with-a-twist-drive-order](http://serverfault.com/questions/538904/mdadm-raid5-recover-double-disk-failure-with-a-twist-drive-order)

Yes, disk order is important if you do anything that forces an array assembly with drives out of order.  If you just assemble and it fails, then that is a clue that something is not correct.

[http://serverfault.com/questions/162805/mdadm-raid-5-data-recovery](http://serverfault.com/questions/162805/mdadm-raid-5-data-recovery)

*mdadm* assemble fails until you get the correct order.  

Drives out of order doesn't damage the data until you force something like create a new RAID over an old RAID.

What were the lessons learned from this incident?

---

### Post by jonathon-2000-uk on 2015-03-15
> **tgalati4 said:**
> What were the lessons learned from this incident?
 Ah... No true Scotsman calls it oatmeal? >.<
 

 I'm currently trying iRecover to see if it can do anything, but naturally, I'm not very hopeful by this point, looks like I'll have to leave it running for some time too. I can't afford to buy it, but at least it can say if any things even likely recoverable by this point.
 The impression I get is that you don’t generally run fsck on a raid array, at all? And on a miss-configured array it will cause damage.
 It was a costly lesson for me, and one I'd like to say I hadn't been taught before, but;
 “Don't run any commands that you aren't absolutely sure about”
 is too often a re-run?! :(
 

 Thanks Jonathon

---

### Post by tgalati4 on 2015-03-15
Backups are important because RAID is not a backup strategy.  RAID5 has some failure modes (like losing 2 disks) and data recovery from RAID5 is difficult because the data is spread across many drives.  RAID6 and RAID10 came about to address some of these issues, but  basic understanding of setting up and maintaining RAID is essential because disaster is only a command away.

---

