---
title: "Seeking advice on RAID setup for my shiny new server"
date: 2008-07-20
forum: Server Platforms
---

### Post by MountainX on 2008-07-20
I just burned a CD for Hardy (8.4.1 AMD 64 server) and I plan to install it on my home file server. I'm ready to get started now, but I realized I need advice on how to set the RAID controllers (cache IO or not, writeback or writethru, read ahead or not, etc.).

My hardware is:
Dual Xeon with 6 GB RAM

LSI MegaRAID 320-2E SCSI controller with: 
4x Seagate ST373454LC 15k rpm drives.

logical drives:
1. two physical disks as RAID 1 for Ubuntu (boot, root)
2. one physical drive for swap, application scratch, logs, etc.
3. one physical drive for virtual machine (dedicated) or other uses

Areca ARC-1220 SATA PCI-express 8x controller with:
4x Samsung HD103UJ
2x WD740GD Raptors

The raptors are set up as passthrough only. They will be dedicated to virtual machines or other things.

The 4x Samsungs are the main storage. I plan to use RAID 5 with one 2 TB volume and a 1 TB volume.

I would appreciate any advice on how to set up the RAID for this home file server. This is awesome hardware for my situation and I'd like to get the most out of it. 

All computers are connected via GigE. All our family data will reside on this file server. This includes music, photos, documents, everything. Most folders in my home partition are mounted folders that reside on this file server. (At the moment, we have a Windows-based file server that will be replaced by this one.) So I need really snappy performance from the network and file server in order not to notice that all my documents are not on my local computer.

BTW, I have an older computer that is used to back up the data from the file server. Not doing offsite backup.

I also think it might be good to spin down the drives after inactivity because the file server runs 24 x 7, but when the family is asleep why not save some wear and tear on the disks? Advice on this?

And I'm a newbie (about 6 months learning Ubuntu, no prior Linux or admin background).
[B][U]
UPDATE:[/U][/B]

LSI MegaRAID 320-2E SCSI controller with 4x Seagate 15k rpm drives:
I think I will set this up as RAID5 and use it for home folders for everyone on my home network.
I think I'll use 64k stripe, write through cache and adaptive read settings on the controller. Should I use cached IO or direct IO?

Areca ARC-1220 SATA PCI-express 8x controller with:
4x Samsung HD103UJ
2x WD740GD Raptors

I think I'll use the raptors for Ubuntu (/boot, root, swap, and everything except /home) in RAID1.
Would write back caching be safe on this volume?

And I'll use the samsung 1 TB drives in RAID5 for music, photos, and all the other data we store.
Should I use a larger stripe size for this volume?

This change will benefit the clients that mount /home on this file server because the fastest drives will be used for home directories. And I'll use NFS4 to share these directories.

But this change will hurt any virtual machines I run on the file server. Since I don't run the virtual machines that often, I think I'll get more benefit by making the home directories as responsive as possible.

Do I need to change any settings for the filesystem when installing Ubuntu in regard to caching to match what I specify in the RAID controllers?

The controllers don't have battery backup installed. The server is on a good UPS and generator.

(BTW, Ubuntu recognizes all the RAID hardware out of the box.)

---

### Post by BobMUK on 2008-07-31
> I also think it might be good to spin down the drives after inactivity because the file server runs 24 x 7, but when the family is asleep why not save some wear and tear on the disks? Advice on this?

First up - no!!  Never spindown overnight, the most wear and tear a disk gets is at spinup.

OK, you're obviously concerned with power consumption/noise - let's look at what you've got:
4x 15K 73GB Seagates
2x (10K?) 73GB WDs 
4x 7.2K 1TB Samsungs

> I think I'll use the raptors for Ubuntu (/boot, root, swap, and everything except /home) in RAID1.
...which means you've got 2 disks using a significant amount of power and producing significant noise for the sake of 73GB of relatively slow storage (RAID 1 will give the same performance as a single drive).

Why not incorporate boot/root/swap into a RAID 5 array?  RAID 5 gives you the same fault tollerance as RAID 1 (ie. the loss of 1 drive).  However you're overlooking the performance benefit of RAID 5 - striping the data across 4 (3+P) members gives you an overall performance aprox. 3x the performance of a single drive.

So I'd suggest the following:
1 RAID 5 array comprising the 4 Seagates giving you around 220GB of pretty fast storage - use this for boot/root/swap and maybe home (depending on how big you're expecting home to get)
1 RAID 5 comprising the Samsungs, giving 3TB of not-quite-as-fast storage - use this for everything else.

> Do I need to change any settings for the filesystem when installing Ubuntu in regard to caching to match what I specify in the RAID controllers?

If the controllers are doing hardware RAID and therefore present just one big "drive" to Ubuntu then nothing further needs to be done - all the caching is done "under the covers" of the RAID card.  Just be sure to create file systems with parameters apropriate to what's going to be stored on them (google blocks per inode for more info).

Hope that helps!

---

### Post by MountainX on 2008-07-31
Thanks for your reply! :)

OK, I will not spin down overnight. I hear what you said about wear/tear at spinup, and I have read that before. I just wanted to make sure the advice had not changed in the last few years. So I won't spin down.

I'm not too concerned about noise. The computers are in another room. Power consumption doesn't seem to be a big issue yet either. I was mainly concerned about wear and tear on the computer equipment.

My (new) strategy (for utilizing the disks) is based on the fact that RAID, even RAID 0, is slower than a single drive in almost all conditions except things like continuous transfers. Putting competing read/write functions on separate spindles will be faster than having them all on one RAID array, even something striped across 4 disks.

I'm going to try to separate each of the following "functions" onto separate spindles:
[LIST]
[*]operating system (root file system)
[*]swap
[*]temporary files and log files
[*]data (/home)
[/LIST]

I will end up using more passthrough drives on my RAID controllers and not using much RAID at all. Again, for my usage (typical desktop usage), this will be faster than RAID. But it is a shame not to fully utilize these good RAID controllers.

I will come up with a good backup strategy. Ideally I want something automated that runs when there are changed files but there has been no activity for X minutes. (I do not know how to do this yet.) I want versioning of backed up files, and I want the backup in an uncompressed (normal, native) format.

By utilizing separate spindles and a good backup strategy I think I will have better performance and data protection than with RAID. Obviously RAID doesn't offer versioning. RAID really only offers uptime, and in a home office environment, I don't desire the small amount of extra uptime as much as I desire everyday performance and versioned backups.

Hope that makes sense. I still need lots of advice regarding the backup solution.

---

### Post by BobMUK on 2008-07-31
> Thanks for your reply!

No problem!

> based on the fact that RAID, even RAID 0, is slower than a single drive in almost all conditions except things like continuous transfers

Hmm. Where are you getting your information from?
Consider the case of RAID 0.  Data is striped across N drives.  For long transfers you get a performance of A*N (where A is the performance of a single drive).  For small transfers, your worst-case performance is **exactly** the same as a single drive.
RAID 5 performance, for reads, is exactly the same as RAID 0. For writes it's slightly more complicated but still faster than a single spindle.

> RAID really only offers uptime
It also gives you redundancy.  You use a single disk as a JBOD (passthru) and when it dies you lose everything since your last backup was taken.  Lose a disk from a RAID 5 and you lose nothing.

> Obviously RAID doesn't offer versioning
Of course RAID is not a substitute for good backups, and never has been.  Regular backups are essential regardless of your hardware!

It sounds like you've talked yourself out of using RAID which is of course your choice - but if you doubt what I've said above send me a PM and I'll tell you where I work and what I do :)


> I still need lots of advice regarding the backup solution. 
I usually tar-up my root and dump it to an external drive weekly (which is locked away safely).  All my data gets archived onto DVD (my box is a PVR).  Don't think I can be much help to you on the backups sorry!

---

### Post by MountainX on 2008-07-31
Here is where I'm getting some of my info:

What RAID can and cannot do (straight talk on RAID's limitations/pitfalls)
[http://www.hardforum.com/showthread.php?t=952998](http://www.hardforum.com/showthread.php?t=952998)

There is also a benchmark (I do not have the link handy) showing that a 4-disk WD Raptor RAID 0 setup is slower than a 7k rpm single drive in almost all normal desktop usage situations. In one test the RAID did beat the single disk by about 10%, but in other situations it was actually slower. And this is using a setup where the raptors used in the RAID are individually faster than the single drive tested against -- yet the RAID was slower. When less than 4 stripes were used, the RAID faired even worse.

If you disagree with that, let me know and I will PM you to get more info. Thanks for sharing your knowledge with me.

---

### Post by MountainX on 2008-07-31
BTW, I believe that JBOD will have a higher statistical failure rate than a single drive (as will RAID 0). I'm not planning on using JBOD.

Here is the link to the benchmark I referred to above:
[http://www.hardforum.com/showthread.php?t=1001325&highlight=proved+ineffective](http://www.hardforum.com/showthread.php?t=1001325&highlight=proved+ineffective)

(I hope I quoted it correctly.)


In regard to redundancy, I recently realized that the redundancy is  limited and that in my own situation I wasn't getting that much benefit from the type of redundancy RAID offers. See these points:
* RAID does not protect data from hardware failure of any component besides physical disks.
* A RAID array has one file system. This creates a single point of failure. 
* A RAID array's file system is vulnerable to a wide variety of hazards other then physical disk failure, so RAID cannot defend against these sources of data loss. 
* RAID will not prevent corruption. RAID will not save data from accidental modification or deletion by the user.

---

### Post by Titan8990 on 2008-07-31
> * RAID does not protect data from hardware failure of any component besides physical disks.

When was the last time your MOBO died and it erased all the data on your hard drive?

> * A RAID array has one file system. This creates a single point of failure.

RAID 1 has no single point of failure. Both drives need to die in order for your data to be lost. How is this different than a single drive? This statement acts like a single drive is more fault tolerant than RAID but this is not the case.

> * A RAID array's file system is vulnerable to a wide variety of hazards other then physical disk failure, so RAID cannot defend against these sources of data loss.

Such as?

> * RAID will not prevent corruption. RAID will not save data from accidental modification or deletion by the user.

Is it supposed to? This is what filesystem permissions are for...

---

### Post by MountainX on 2008-07-31
A motherboard failure, power supply failure or power loss (for example) could corrupt some data on the hard drive, and probably to a greater extent when RAID is used. Right?

Anyway, when looking at the overview of all these facts (opinions), I still believe I will get better desktop usage performance with multiple separate spindles rather than with RAID, and that I will meet my data protection needs with automated backup that includes versioning of individual files.

I know how to implement the HDD setup, partitioning, etc., but I do not know how to implement the backups in Linux. (In Windows I achieved exactly my backup ideal with SyncBack SE.)

---

### Post by Titan8990 on 2008-07-31
> A motherboard failure, power supply failure or power loss (for example) could corrupt some data on the hard drive, and probably to a greater extent when RAID is used. Right?

Only when using FakeRAID can MOBO failure cause you to lose your data: [http://en.wikipedia.org/wiki/Fakeraid#Firmware.2Fdriver_based_RAID_.28.22fake_RAID.22.29](http://en.wikipedia.org/wiki/Fakeraid#Firmware.2Fdriver_based_RAID_.28.22fake_RAID.22.29). 

Otherwise mobo failure will not lead to data loss. PSU failure can just completly fry everything in your system via electrical surge. Nothing can stop that. Best you can do about that is buy a high quality unit such a PC Power and Cooling or a Seasonic (few other grade "A" PSUs out there).

> 
Anyway, when looking at the overview of all these facts (opinions), I still believe I will get better desktop usage performance with multiple separate spindles rather than with RAID, and that I will meet my data protection needs with automated backup that includes versioning of individual files.

This depends on the type of RAID you select. RAID 5 for example will outperform a single drive while adding data protection but like the other person said earlier, it is not meant to replace regular back ups.

> I know how to implement the HDD setup, partitioning, etc., but I do not know how to implement the backups in Linux. (In Windows I achieved exactly my backup ideal with SyncBack SE.)

Try:

$man rsync

You can write a script and set up as a cron job using rsync. Here is an example of the backup script:

```
#!/bin/sh

# %Y     year
# %m     month (01..12)
# %d     day of month (e.g, 01)
# %s     seconds since 1970-01-01 00:00:00 UTC

# Variable for the Program
BACKUPDIR=/
THEDATE=`date '+%Y%m%d-%s'`
LOGDIR=/var/log/backup
EXCLUDEFILE=/scripts/exclude
LOGFILE=/var/log/backup/rsync-$THEDATE.log
GZFILE=/var/log/backup/rsync-$THEDATE.gz
DESTINATION=/media/sda1/backup0
LAST=/media/sda1/backup5
MNTPOINT=/media/sda1/
BACKUPD=/dev/sda1

#Check to make sure that our backup drive is mounted - To be included later


#If the log directory does not exist then create it

if [ ! -d $LOGDIR ]; then
    mkdir -p $LOGDIR
fi

#If the destination directory does not exist then create it

if [ ! -d $DESTINATION ]; then
        mkdir -p $DESTINATION
fi

#Rotate the backups

rm -rf $LAST
mv /media/sda1/backup4 $LAST
mv /media/sda1/backup3 /media/sda1/backup4
mv /media/sda1/backup2 /media/sda1/backup3
mv /media/sda1/backup1 /media/sda1/backup2
cp -al $DESTINATION /media/sda1/backup1

#Now run rsync to backup the filesystem

rsync -avr --delete --delete-excluded --exclude-from=$EXCLUDEFILE --log-file=$LOGFILE $BACKUPDIR $DESTINATION

# gunzip the logfile
gzip -c $LOGFILE > $GZFILE

# delete the original, uncompressed logfile
rm $LOGFILE
```

The script above makes a full system backup. It keeps 5 of them and a cron job runs in every night. Some will argue that a full backup isn't needed everyday but it just how I like to do it.

---

### Post by MountainX on 2008-07-31
Thanks for the tips on the backup script. I would like an easy way to include/exclude files, particularly new files. With SyncBack SE, I could specify whether new files added to a folder would be automatically included (backed up) or excluded.

> **Titan8990 said:**
> 
This depends on the type of RAID you select. RAID 5 for example will outperform a single drive while adding data protection but like the other person said earlier, it is not meant to replace regular back ups.


The benchmark link I provided above shows that RAID (any level) will not usually outperform a single drive for typical desktop usage patterns.

---

### Post by Titan8990 on 2008-07-31
Are you refering to these benchmarks: [http://www.hardforum.com/showthread.php?t=1001325&highlight=proved+ineffective?](http://www.hardforum.com/showthread.php?t=1001325&highlight=proved+ineffective?)

Where the OP does not use the same drives as single as he does for the RAID set?

That backup script excludes files listed in a file specified by the $EXCLUDEFILE variable. My exclude file looks like this:

```
/proc/
/sys/
/tmp/
/media/
```

You could write another script that will write your exclude file for you. Possible something like:

```
find / -mtime > /scripts/exclude
```

---

### Post by Titan8990 on 2008-07-31
Just tested the above and it appears that it will work:

```
jordan@einstein:~/test$ find ~/test -mtime -1 > ~/test/exclude
jordan@einstein:~/test$ cat exclude 
/home/jordan/test
/home/jordan/test/exclude
/home/jordan/test/newfile
/home/jordan/test/newfile3
/home/jordan/test/newfile2

```

---

### Post by MountainX on 2008-07-31
Thanks for the additional backup script tips.

> **Titan8990 said:**
> Are you refering to these benchmarks: [http://www.hardforum.com/showthread.php?t=1001325&highlight=proved+ineffective?](http://www.hardforum.com/showthread.php?t=1001325&highlight=proved+ineffective?)


Yes, that is one that I have seen cited frequently. There are others, but I don't have links to them.

> **Titan8990 said:**
> 
Where the OP does not use the same drives as single as he does for the RAID set?


I think this sums it up: "Even running _four_ WD740GDs in RAID-0 is not enough to match the single user performance of a single WD1500ADFD."

The WD740GD is the 74GB 10k rpm raptor. The WD1500ADFD is the 150 GB raptor, also 10k rpm. 

The link includes a good discussion of the limitations of the benchmark. Do you know of other limitations not discussed there? 

However, in my situation I am not proposing replacing RAID 1 with a single drive. I am proposing replacing one RAID array with multiple independent drives so that I gain additional performance by sending potentially competing disk operations to different drives. As I said, things like logs would be directed to a spindle independent of the main OS. /home would be independent as well. So I think the performance advantages to me (by foregoing RAID) would be greater than what this benchmark suggests.

BTW, I am not against RAID. My /home partition, in fact, will be on a 4-drive RAID 5 array utilizing 15k rpm SCSI drives. But this array will be independent of the spindles for the OS, logs, swap, etc. (The OS "drive" may in fact be a 2-drive RAID-1 array.) 

So my strategy is not to avoid RAID entirely, **it is to make the use of independent spindles a higher priority than striping** (while using both).

---

### Post by Titan8990 on 2008-07-31
First of all benchmarks are worthless unless there is a constant. There is no constant here as he is using different drives. It is almost like a science experiment.

Also, I have a very good feeling that this OP is using FakeRAID and not a dedicated controller which means that his CPU is doing all the work. Single drive systems **are not** faster than a RAID 0 or RAID 5. I however would never recommend RAID 0 for any situation because it has **no** fault tolerance. 

The RPM of a HDD is only a slight indication of it's speed. There is no reason one 10k RPM HDD can't be faster than another 10K RPM drive because in the real world there are some faster than others. Many other factors play in to this including:

firmware
cache size
number of platters/layout

I think that you should look towards more professional benchmarks. For example here is one that explains how/why the ADFD raptors are that much better than the older GD raptors: [http://www.anandtech.com/storage/showdoc.aspx?i=2922](http://www.anandtech.com/storage/showdoc.aspx?i=2922)

---

### Post by MountainX on 2008-07-31
> **Titan8990 said:**
> 
I think that you should look towards more professional benchmarks. 

That benchmark was done by StorageReview.com. They have a good reputation.

Here's a description of their standard testbed:
[http://www.storagereview.com/Testbed4.sr](http://www.storagereview.com/Testbed4.sr)

They aren't idiots and I doubt they fell into the fake-raid trap.

> **Titan8990 said:**
> all benchmarks are worthless unless there is a constant. There is no constant here as he is using different drives. It is almost like a science experiment.


That's an unfair attack on the benchmark in my opinion. Yes, the 150 GB drive has a 16 MB cache vs. 8 MB for the (4) 74 GB raptors. There are other tweaks. But the benchmark proves that even 4 fast drives in a RAID 1 will not beat a single drive in at least some situations. So it serves a purpose.

**I still believe I'll get better performance from a set of independent spindles than I will from using the same drives together in a RAID array.** Is this opinion wrong? I have seen nothing to convince me it is wrong yet.

---

### Post by Titan8990 on 2008-07-31
Those "some situations" are when the drive A is considerably faster than drive B to begin with. That benchmark means absolutely nothing to me. If you wish to live by it, that is your choice.

---

### Post by MountainX on 2008-07-31
I found the links to some of the original research on the question of RAID-0 vs single drives:

[http://forums.storagereview.net/wiki/index.php/SingleDriveVsRaid0](http://forums.storagereview.net/wiki/index.php/SingleDriveVsRaid0)
"regardless of interface, controller, or drive used the conclusions above remain valid."

[http://www.storagereview.com/articles/200406/20040625TCQ_5.html](http://www.storagereview.com/articles/200406/20040625TCQ_5.html)
shows some of the great detail they get into while examining RAID controllers

---

### Post by MountainX on 2008-07-31
> **Titan8990 said:**
> Those "some situations" are when the drive A is considerably faster than drive B to begin with. That benchmark means absolutely nothing to me.

If you read the links I posted, I think you will see the benchmarking is sound. 

And those "some situations" are **_not_** just when the drive A is considerably faster than drive B to begin with according to [http://forums.storagereview.net/wiki/index.php/SingleDriveVsRaid0](http://forums.storagereview.net/wiki/index.php/SingleDriveVsRaid0)

I'm backing up my statements with references. I have not seen any solid counterpoints. I admit that my knowledge is limited and I'm here to learn, but the quote above seems to be based on nothing substantial at all, so I can't learn anything from it.

---

### Post by MountainX on 2008-07-31
"**RAID helps multi-user applications far more than it does single-user scenarios.** The enthusiasm of the power user community combined with the marketing apparatus of firms catering to such crowds has led to an extraordinarily erroneous belief that striping data across two or more drives yields significant performance benefits for the majority of non-server uses. This could not be farther from the truth! Non-server use, even in heavy multitasking situations, generates lower-depth, highly-localized access patterns where read-ahead and write-back strategies dominate. Theory has told those willing to listen that striping does not yield significant performance benefits. Some time ago, a controlled, empirical test backed what theory suggested. Doubts still lingered- irrationally, many believed that results would somehow be different if the array was based off of an SATA or SCSI interface. As shown above, the results are the same. Save your time, money and data- leave RAID for the servers!"

[http://www.storagereview.com/articles/200406/20040625TCQ_5.html?page=0%2C5](http://www.storagereview.com/articles/200406/20040625TCQ_5.html?page=0%2C5)

---

### Post by windependence on 2008-08-01
> **MountainX said:**
> If you read the links I posted, I think you will see the benchmarking is sound. 

And those "some situations" are **_not_** just when the drive A is considerably faster than drive B to begin with according to [http://forums.storagereview.net/wiki/index.php/SingleDriveVsRaid0](http://forums.storagereview.net/wiki/index.php/SingleDriveVsRaid0)

I'm backing up my statements with references. I have not seen any solid counterpoints. I admit that my knowledge is limited and I'm here to learn, but the quote above seems to be based on nothing substantial at all, so I can't learn anything from it.

I am usually the one here telling the n00bs not to use RAID because they don't need it, but in this case I think what has been said about the benchmarks being flawed is right on. This big bruha about spindle speed is crap. It's seek time that you want unless you are reading continuous data (read "big files") all the time. 

There is no way you can convince me that a RAID 5 array (hardware RAID) or a RAID 0 array with many spindles would be slower than a single drive. Because the data is striped across the drives, it can be pulled from several drives at once, which is much faster than reading from a single drive.

In the end though, with the speed of most modern drives, I don't think you are going to actually notice it. What's the difference between instantaneous and almost instantaneous? Of course, YMMV. In a sever situation, however, and after all we ARE in the SERVER forum, RAID will be faster, especially with many concurrent users like a web server. I don't recommend software RAID at all. I have my reasons. :)

-Tim

---

### Post by MountainX on 2008-08-01
> **windependence said:**
> 
There is no way you can convince me that a RAID 5 array (hardware RAID) or a RAID 0 array with many spindles would be slower than a single drive.

-Tim

I'm not in disagreement with most of what you said, but it sounds like you didn't read any of the good research at StorageReview.com. I posted links previously.

---

### Post by BobMUK on 2008-08-01
Wow, I didn't think this thread would turn into such a heated discussion!  :)


> First of all benchmarks are worthless unless there is a constant. There is no constant here as he is using different drives. It is almost like a science experiment.

Couldn't have said it better myself.
Perhaps there are other flaws in their testing too.

> I still believe I'll get better performance from a set of independent spindles than I will from using the same drives together in a RAID array. Is this opinion wrong? I have seen nothing to convince me it is wrong yet.

OK - here goes:

Let's look specifically at the simplest case - RAID 0 - with 4 members as an example.

A long sequential write gets striped across all 4 members - each disk writes aprox. 1/4 of the overall data, taking aprox. 1/4 of the time it would take on a single spindle.  These writes happen in parallel, giving an overall time-to-complete of aprox. 1/4 of what a single spindle would.

Short reads/writes that are so short that the data is all on a single disk will take *exactly* as long as just reading/writing to a single spindle.

ANY discrepancy between these figures and what the testbed reflects is down to a flaw in the test.  Period.

> The benchmark link I provided above shows that RAID (any level) will not usually outperform a single drive for typical desktop usage patterns.

But surely the point was that your box is a home media server?  If you're generally transfering files in the 10's of MB then you've got a server workload.

One other thing I had to mention:
> BTW, I believe that JBOD will have a higher statistical failure rate than a single drive (as will RAID 0). I'm not planning on using JBOD.

JBOD means "just a bunch of disks" and means a drive attached to a raid controller but just being used as a single spindle without RAID.  Which was what you were talking about doing....

---

### Post by MountainX on 2008-08-01
> **BobMUK said:**
> Wow, I didn't think this thread would turn into such a heated discussion!  :)


That's a good thing, right? :)

> **BobMUK said:**
> 
JBOD means "just a bunch of disks" and means a drive attached to a raid controller but just being used as a single spindle without RAID.  Which was what you were talking about doing....

I assumed JBOD always meant aggregation. The disks are grouped into a "bunch" and presented (to the system) as a single volume. That means that the risk of failure is a multiple of the individual disk failure chance.

A single spindle without RAID is called a "passthrough" disk in the controller manuals I've been reading. 

I have the ability to do either JBOD (with multiple disks) or passthrough (with single disks) in both my controllers.

---

### Post by windependence on 2008-08-01
> **BobMUK said:**
> Wow, I didn't think this thread would turn into such a heated discussion!  :)




Couldn't have said it better myself.
Perhaps there are other flaws in their testing too.



OK - here goes:

Let's look specifically at the simplest case - RAID 0 - with 4 members as an example.

A long sequential write gets striped across all 4 members - each disk writes aprox. 1/4 of the overall data, taking aprox. 1/4 of the time it would take on a single spindle.  These writes happen in parallel, giving an overall time-to-complete of aprox. 1/4 of what a single spindle would.

Short reads/writes that are so short that the data is all on a single disk will take *exactly* as long as just reading/writing to a single spindle.

ANY discrepancy between these figures and what the testbed reflects is down to a flaw in the test.  Period.



But surely the point was that your box is a home media server?  If you're generally transfering files in the 10's of MB then you've got a server workload.

One other thing I had to mention:


JBOD means "just a bunch of disks" and means a drive attached to a raid controller but just being used as a single spindle without RAID.  Which was what you were talking about doing....

Hey Bob, it's good to have an ally here. I always get hammered by the software RAID guys when I tell someone to buy a good hardware controller. :)

-Tim

---

### Post by MountainX on 2008-08-01
I think the biggest point I was trying to make (and that people here may be missing) is that multiple independent disks have several important speed advantages over an array made of those same disks in certain circumstances.

That's a slightly different point from the benchmark cited, but it is also complementary to (and maybe builds on) some of the insights gained from that and other benchmarks.

Here is what I understand:

In a situation where you need to read and write both (1) some data and (2) logs/temp files/swap, having those two types of data on independent storage (even if just single disks each) will usually outperform having those file operations both go to the same RAID array (even if it is a striped array consisting of more than 2 disks).

This is even more true where virtual machines are involved. Each VM should have its own disk, even if only a single disk, rather than putting several VMs on a RAID array (again, even if using a larger number of disks). I run VMs a lot, so this is an important consideration for me.

My home server does have files that are in the 10's of MBs and more, but it also has my /home partition -- and that is the part where performance matters the most to me. I use my /home data more than anything else, and I want good performance in "typical desktop usage" scenarios.

And I still think the people criticizing StorageReview.com's benchmarking haven't read it. Those guys do some impressive work. For example, they benchmarked 4 WD raptors. A little while later WD sent them 4 more. They benchmarked that 2nd batch again just to be sure there wasn't a difference. They don't leave much to chance. They do not do shoddy work. The benchmarks are more sound than most benchmarks, in my opinion.

The great benefit (to me) of this thread is that it has motivated me to read all this stuff in greater detail. I have learned a lot, and if someone points out where I'm wrong, I'll learn even more ;)

---

### Post by windependence on 2008-08-01
I run ONLY VMs on my production stuff and they run on a separate RAID5 array. Why? Because the data throughput is better. Like Bob, if I told you what I do, I might lend more credibility to my post but suffice it to say we know from real world experience.

I would venture to say, on your home server you will never see a difference. Linux memory management is much different from Windoze. Linux shoves whatever it can into memory and swaps it out when needed so there are less reads and writes on the media. Windows, still uses a swap file. Yes, Linux CAN too, but you don't need it with enough RAM, and you can even turn swapping off if you ave enough physical memory.

Did the benchmarks happen to mention what OS they used? I bet I can guess.

-Tim

---

### Post by MountainX on 2008-08-01
> **windependence said:**
> I run ONLY VMs on my production stuff and they run on a separate RAID5 array. Why? Because the data throughput is better. Like Bob, if I told you what I do, I might lend more credibility to my post but suffice it to say we know from real world experience.

I would venture to say, on your home server you will never see a difference. Linux memory management is much different from Windoze. Linux shoves whatever it can into memory and swaps it out when needed so there are less reads and writes on the media. Windows, still uses a swap file. Yes, Linux CAN too, but you don't need it with enough RAM, and you can even turn swapping off if you ave enough physical memory.

Did the benchmarks happen to mention what OS they used? I bet I can guess.

-Tim

The blog where I read about running VMs on separate independent spindles is written by a guy who has a ton of real work experience (he is Scott Hanselman). But, yes, he is a Windoze guy. 

My VMs are usually running Windoze as the guest OS with vmWare on Ubuntu as host.

It sounds like you guys are smart, but a LOT of smart guys over at Hard Forum are in disagreement with you -- at least it seems to me that there is disagreement on some of the points. In particular, they (and others) feel that multiple independent spindles have certain advantages and over here you guys tend to choose RAID more often... (I know there are nuances, so I'm making a generalization.)

---

### Post by windependence on 2008-08-01
Hehe, this is REALLY funny. If you search my posts you will see tons of posts where I am trying to tell people here NOT to use RAID because they don't need it. Most times I don't, but in your case you are transferring large files and like Bob mentioned, that is where you will see the speed difference. Even the blogs agree with that. If this is a home media server, you're gonna tell me you aren't transferring several gigs of stuff? Movies? Music?

-Tim

---

### Post by BobMUK on 2008-08-01
> Wow, I didn't think this thread would turn into such a heated discussion!  

> That's a good thing, right? 

LOL, of course... it's a quiet Friday afternoon!  :)

> JBOD means "just a bunch of disks" and means a drive attached to a raid controller but just being used as a single spindle without RAID. Which was what you were talking about doing.... 
> I assumed JBOD always meant aggregation. The disks are grouped into a "bunch" and presented (to the system) as a single volume. That means that the risk of failure is a multiple of the individual disk failure chance.

Alas that's incorrect.  Waht you've described, effectively, is RAID 0!!  JBOD means it's just a single drive.  Honest.  (Please don't cite wikipedia etc as a source that says otherwise!)

---

### Post by MountainX on 2008-08-01
> **windependence said:**
> If this is a home media server, you're gonna tell me you aren't transferring several gigs of stuff? Movies? Music?

-Tim

It's a home file server. I have a separate SageTV server. But the file server will deal with large files sometimes. However, I'm targeting performance of the operations I will do the most, which is just working with the smaller files in /home.

---

### Post by BobMUK on 2008-08-01
> However, I'm targeting performance of the operations I will do the most, which is just working with the smaller files in /home.

Fair enough, point taken - for your specific needs you may be better off with a single disk for /home.

Though personally I've never found my RAID 5 arrays too slow for any of my needs!

If the box is still unbuilt/being rebuilt why not try some of the options including RAID and non-RAID, use hdparm and get some figures of your own?  You may be pleasantly surprised!

---

### Post by MountainX on 2008-08-01
> **BobMUK said:**
> Fair enough, point taken - for your specific needs you may be better off with a single disk for /home.

Though personally I've never found my RAID 5 arrays too slow for any of my needs!

If the box is still unbuilt/being rebuilt why not try some of the options including RAID and non-RAID, use hdparm and get some figures of your own?  You may be pleasantly surprised!

Yes, that is a good suggestion. My current file server is running Win2003 and I have been taking my time and experimenting as I build up this Ubuntu server to replace it. I would like to learn about tools like hdparm.

---

