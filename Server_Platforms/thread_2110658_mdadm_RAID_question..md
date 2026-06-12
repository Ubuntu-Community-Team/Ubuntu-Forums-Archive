---
title: "mdadm RAID question."
date: 2013-01-30
forum: Server Platforms
---

### Post by Roasted on 2013-01-30
I have Ubuntu Server 12.04 running along with a pair of 3TB HDDs. I had both of them mirroring using mdadm that I set up through the command line. To "test" my array, I powered the server off and unplugged one of the drives. I then booted it up and it asked me if I wanted to start up in degraded mode. I said yes.

Afterwards I powered the server off and plugged the drive back in. To my surprise, it booted up again and again as degraded mode. Both drives are present. I can see them via blkid as well as in the BIOS. Did I goof? Do I have to re-add the drive to the array to get it fully working again? I thought in the past I had done this and both drives came back fully working when I powered back up...

Also, another question - is it bad practice to have a file system on your drives before you add them to the array? I think I may have had ext4 on both of them before creating an array and adding them accordingly. I saw one source that said this was bad practice and you can expect issues, however, others had suggested that the sync process to build the array would "blow away" that theory because it's rebuilding the disks from ground up. Thoughts?

EDIT - I just ran sudo mdadm --manage /dev/md127 --add /dev/sdc1, and now my array is syncing back up. Is this expected behavior that a RAID has to resync once it's powered on in degraded mode?

---

### Post by SAngeli on 2013-01-31
Hi,

I have been using mdadm for a very short period of time but I documented myself quite a lot and hope to provide you wish useful answers.

> Do I have to re-add the drive to the array to get it fully working again?
Yes, once the failed HD is put back into the server your have to wipe out all the content with fdisk, recreate the Linux raid autodetect partition just like you did at beginning. 
Then, you have to add it to the existing raid array with this command:
```
sudo mdadm --add /dev/md0 /dev/sdb1
```
NOTE:
/dev/md0 should be matched to your existing array name
/dev/sdb1 should be matched to your current hd device

At this point you can verify if the array is in recovery mode by typing the following command:
```
cat /proc/mdstat
``` 

Just wait for mdadm to finish and then check again.

The reason why you should wipe out all content of the HD and recreate the partition, in my understanding, is because it is assumed that your hd really failed. So, when you introcude a new replacement it has to be completely empty and prepared to be part of the array matching the current running hd.

> is it bad practice to have a file system on your drives before you add them to the array?
To my knowledge you must first create the array assigning Linux raid autodetect partition(s). After the raid is created the HD(s) are all in sync, you can create a filesystem.
You could also create the filesystem immediately after you issued "mdadm --create /dev/md0 ....." but what if something goes wrong?
So, it is up to you. I would first want to make sure all is properly working and than worn on filesystem and so on.

Also I would advise you to speed up your min and max rebuild speed so that it would take less time to rebuild the array.
You can find excellend documentation at this link:
[http://www.cyberciti.biz/tips/linux-...ild-speed.html](http://www.cyberciti.biz/tips/linux-...ild-speed.html)

But in a nutshell here is what you have to do:
```
nano –w /etc/sysctl.conf
# RAID rebuild speed parameter tweak
dev.raid.speed_limit_min = 50000
dev.raid.speed_limix_max = 200000

nano /etc/rc.local
# RAID cache tuning
echo 8192 > /sys/block/md0/md/stripe_cache_size
blockdev --setra 4096 /dev/md0
```

Lastly, I wish to share with you some documentation I found very helpful for me:
Ubuntu mdadm lesson 1
[http://www.youtube.com/watch?v=mee9l1aNZdc](http://www.youtube.com/watch?v=mee9l1aNZdc)

Ubuntu mdadm lesson 2 (this is what you want to watch)
[http://www.youtube.com/watch?v=HryJvlOtEVU](http://www.youtube.com/watch?v=HryJvlOtEVU)

Take care,
Spiro

---

### Post by Roasted on 2013-01-31
Thank you for your detailed response. I really appreciate it. The more I read last night the more indications I picked up on that suggested resyncing the drives is necessary since once they're dropped from the array, they're dropped for good unless you re-add it. Makes sense. Anyway, there's a few things I want to touch base on. For example, you made the comment: 

> 
Yes, once the failed HD is put back into the server your have to wipe out all the content with fdisk, recreate the Linux raid autodetect partition just like you did at beginning. 


So when I tested my array by taking out a working drive, then re-inserting it, are you suggesting I need to format it entirely and re-create the Linux autodetect raid partition? Or are you suggesting that would be common practice with a fresh drive that has nothing on it?

Also, via terminal, how would one accomplish such a task? I'm getting confused by all of these guides online with mdadm. What guides out there that highlight what I want to do have almost nothing in common except for building the initial array and adding the drives to the array. For example, one source suggested that having an ext file system on the drives before adding them as RAID is a bad idea. But why? Does the RAID setup not run through the HDDs and set them up as it needs during the build process? Also, with terminal, how would one set the drive as RAID autodetect? If you skip this step, what are the consequences? I don't recall doing this, as I just remember focusing on putting a GPT table on the drives (which I did via GParted on Lubuntu LiveUSB). I don't recall setting anything as RAID, but if I run blkid I see both drives listed as linux_raid_member. 

Also, what are the consequences of having a file system on a hard drive before it's added to the RAID array? I'm nearly 100% positive I had EXT4 on both drives before I added them to the array. I think I did this because an unallocated disk is simply /dev/sdb, but I saw in the documentation I needed to add /dev/sdb1 to the array, so I think that's when I added the file systems accordingly. So if I remember right, I went:

[LIST=1]
[*]Formatted drives with GPT partition table.
[*]Added EXT4 partition spanning across the entirety of each drive.
[*]Built a /dev/md0 raid 1 array with 2 members, however it came out to /dev/md127 (does it matter?)
[*]Took 6-7 hours to sync (significantly less than I expected for 2x3TB mirror, to be honest).
[*]Rsync'd 1.3TB of data over.
[*]Still running.
[/LIST]

What say you on the topic? Did I goof? It's just hard to assume that I'm right or wrong on the topic based on what I'm reading when I have an array actively running with seemingly good results. Know what I mean?

---

### Post by SaturnusDJ on 2013-01-31
> **Roasted said:**
> 
Also, another question - is it bad practice to have a file system on your drives before you add them to the array? I think I may have had ext4 on both of them before creating an array and adding them accordingly. I saw one source that said this was bad practice and you can expect issues, however, others had suggested that the sync process to build the array would "blow away" that theory because it's rebuilding the disks from ground up. Thoughts?

Mdstat block size is the same, with or without the creation of a filesystem at the disks. After the creation of an array, (g)parted still shows the filesystem at disk level until a filesystem is created on top of the array. Mdadm doesn't care about what you feed it.
In other words: It's not dangerous and mdadm will handle it correctly.

If you're using partitions instead of devices in an array, just make sure they have the correct size.

> 
EDIT - I just ran sudo mdadm --manage /dev/md127 --add /dev/sdc1, and now my array is syncing back up. Is this expected behavior that a RAID has to resync once it's powered on in degraded mode?
It's expected behavior if the content is somehow modified. You should be able to prevent this by mounting read-only at most.

---

### Post by Roasted on 2013-01-31
> **SaturnusDJ said:**
> 
If you're using partitions instead of devices in an array, just make sure they have the correct size.


Everything that I've read has had the directions of using /dev/sdb1, /dev/sdc1, etc to add to an array. This, I can only assume, is utilizing the partitions to build the array. In fact I intentionally put EXT4 on the drives in order to have the ability to add via /dev/sdb1 /dev/sdc1 in accordance to the directions. Is that to say that I could technically do /dev/sdb and /dev/sdc to add to the array instead to use the entire disk?

In other words:

```
mdadm --manage /dev/md127 --add /dev/sdb1 /dev/sdc1
```

vs

```
mdadm --manage /dev/md127 --add /dev/sdb /dev/sdc
```

Eh?

Thanks for the quick response!

---

### Post by SaturnusDJ on 2013-01-31
You only want to do that if the array is also created that way. It's no surprise to me if mixing devices and partitions in an array is possible too, but that's only confusing.

If you use partitions, you can create 'unformatted' ones, but mdadm doesn't care. (Actually that's just a partition without a filesystem.)

---

### Post by Roasted on 2013-01-31
> **SaturnusDJ said:**
> You only want to do that if the array is also created that way. It's no surprise to me if mixing devices and partitions in an array is possible too, but that's only confusing.


You're saying that if I create an array via partitions (/dev/sdb1, /dev/sdc1) that I should NOT add additional drives via entire disk to that very array (/dev/sdd, /dev/sde)... is that what I'm understanding?

If you're building an array from ground up, does it matter? Are there pros or cons to doing it one way vs the other? I would think that via partition is the way to go since, well, I see it on every single list of directions in existence, but stranger things have happened on the internet.

---

### Post by rubylaser on 2013-01-31
If you add a write intent bitmap, you can use the re-add command, and it will not require a full re-sync (this does have a slight write performance penalty).

```
mdadm --grow --bitmap=internal /dev/md127
```
```
mdadm /dev/md127 --re-add /dev/sdc1
```

In regards to using partitions vs. whole disks.  There isn't a performance or reliability difference from one to the other, but:

1) If you use partitions, you can label the partition to allow you to easily identify your array members.

2) If you use disks from different manufacturers, you may end up with disks that are not exactly the same size. If you use partitions, you can allocate less than the whole disk, and then later, if you end up with a slightly smaller replacement drive for whatever reason, this won't impact you, as you were smart and reserved some space when you were creating the array. This is the main reason I use partitions vs. whole disks.

---

### Post by Roasted on 2013-01-31
> **rubylaser said:**
> 
1) If you use partitions, you can label the partition to allow you to easily identify your array members.


Good call.

> 
2) If you use disks from different manufacturers, you may end up with disks that are not exactly the same size. If you use partitions, you can allocate less than the whole disk, and then later, if you end up with a slightly smaller replacement drive for whatever reason, this won't impact you, as you were smart and reserved some space when you were creating the array. This is the main reason I use partitions vs. whole disks.

I thought mdadm would automatically use a smaller disk as the gauge of the array size?

In other words:

HDD 1 = 3002 GB
HDD 2 = 3000 GB
Array = 3000 GB

Would that work if the drive that you're replacing is the smaller drive? So if I have two 3002 GB HDD's and one fails, and the replacement is 3000 GB, would that downsize the array by 2 GB to 3000 or would that fumble things up?

---

### Post by rubylaser on 2013-01-31
> **Roasted said:**
> 
I thought mdadm would automatically use a smaller disk as the gauge of the array size?

In other words:

HDD 1 = 3002 GB
HDD 2 = 3000 GB
Array = 3000 GB

Would that work if the drive that you're replacing is the smaller drive? So if I have two 3002 GB HDD's and one fails, and the replacement is 3000 GB, would that downsize the array by 2 GB to 3000 or would that fumble things up?

You are create in the case of creating an array. But, down the line if you need to replace a disk you could be hosed.  Let's say you have (3) 3TB disks now (3000GB) and later one dies, and you replace it with a different vendors 3TB disk.  If it's even 1 byte smaller, you will not be able to add this replacement disk to the array (it would be smaller than your smallest array member).  I normally just make my partitions a couple hundred megs smaller than their full size.  That should cover any future differences, while sacrificing almost no space.

---

### Post by Roasted on 2013-01-31
> **rubylaser said:**
> You are create in the case of creating an array. But, down the line if you need to replace a disk you could be hosed.  Let's say you have (3) 3TB disks now (3000GB) and later one dies, and you replace it with a different vendors 3TB disk.  If it's even 1 byte smaller, you will not be able to add this replacement disk to the array (it would be smaller than your smallest array member).  I normally just make my partitions a couple hundred megs smaller than their full size.  That should cover any future differences, while sacrificing almost no space.

But wouldn't this be possible?

HDD 1 = 3002 GB
HDD 2 = 3002 GB

HDD 2 fails.
HDD 2a purchased.
HDD 2a = 3000 GB (2 GB smaller than the original drives)

Couldn't I downsize the array (aka, the volume containing the HDD 1 member) to 2900 GB, then add HDD 2a to the array and end up with a 2900 GB volume?

---

### Post by SaturnusDJ on 2013-01-31
Should be possible yes. First shrink the filesystem, then array. Of course this is more risky than the partitioned setup.

---

### Post by rubylaser on 2013-01-31
> **Roasted said:**
> But wouldn't this be possible?

HDD 1 = 3002 GB
HDD 2 = 3002 GB

HDD 2 fails.
HDD 2a purchased.
HDD 2a = 3000 GB (2 GB smaller than the original drives)

Couldn't I downsize the array (aka, the volume containing the HDD 1 member) to 2900 GB, then add HDD 2a to the array and end up with a 2900 GB volume?

Yes, this is possible, but not worth the risk.  Since your need to resize the partition first, there is a very real danger of data loss. I wouldn't even consider this a viable option, I'd just buy a larger (4TB) disk to replace it, and remove this issue altogether.

---

### Post by Roasted on 2013-01-31
> **SaturnusDJ said:**
> Should be possible yes. First shrink the filesystem, then array. Of course this is more risky than the partitioned setup.

I appreciate the response. I found the command resize2fs which sounds like it might work.

resize2fs /dev/md127 [size]

I would hope this method wouldn't be laced with issues. After all, I'd just be resizing the ext4 partition on the array in the same demeanor I'd be resizing an ext4 partition on a regular drive. Then again, RAID introduces more cooks into the kitchen, so I suppose anything is possible.

EDIT:

> **rubylaser said:**
> Yes, this is possible, but not worth the risk.  Since your need to resize the partition first, there is a very real danger of data loss. I wouldn't even consider this a viable option, I'd just buy a larger (4TB) disk to replace it, and remove this issue altogether.

I understand. I suppose if anything, best practice would be to tear down the array and downsize the partitions accordingly. This setup is in its infancy stage so it's far more do-able than a production server would be that people rely on, etc. 

I don't mean to sound like a broken record but I'd like to iron out a few key points. In regard to the 3000 vs 3002 comparison done above with keeping drives downsized in an effort to ensure replacements won't be 1 byte short or anything like that, we're talking about the DRIVE partitions - right? Meaning you would want:

HDD 1 = 2900 GB, 100GB unallocated
HDD 2 = 2900 GB, 100GB unallocated
mdadm --manage /dev/md127 --add /dev/sdb1 /dev/sdc1

Correct? We're not talking about the actual file system sitting on /dev/md127, right?

I really appreciate the insight fellas!

EDIT 2 - Speaking of which, if I would add the drives via the entire disk, I'd undoubtedly run into that issue by default in the event I drop a 3000 GB replacement in place of a 3002 GB original...

---

### Post by SaturnusDJ on 2013-01-31
That's right because if you limit the filesystem, the raid array still uses the maximum of the partitions. (However that's controllable also I believe.)


You want to have a back-up first if you're going to do things like this to important data. I found out the hard way.

Practice in a virtual machine.

---

### Post by Roasted on 2013-01-31
One last question. How do you fellas change the partition type of GPT disks via terminal? Working with GPT takes sfdisk and fdisk out of the picture, leaving me with GParted via LiveUSB session or, what people tell me, is parted via terminal. I have yet to get parted to work properly though. So from what I can tell, it's either GParted or bust. Clearly there's a terminal way, no?

---

### Post by darkod on 2013-01-31
To create a gpt table on disk /dev/sda for example:
sudo parted /dev/sda

Once in the parted prompt:
mklabel gpt

Don't forget on gpt disks you need a small 1MiB partition with bios_flag on if you plan to install grub2 on that disk. This is because the gpt MBR is smaller than msdos, and grub2 doesn't fit. parted creates partitions with no filesystem by default, which is exactly what grub2 needs so i usually do it in parted:
unit MiB
mkpart GRUB 1 2
set 1 bios_grub on

To exit parted you simply do:
quit

Short users manual:
[http://www.gnu.org/software/parted/manual/parted.html](http://www.gnu.org/software/parted/manual/parted.html)

EDIT PS: Don't forget, creating new table deletes all partitions and data. parted is also good for manipulating flags on the partitions, like raid (for mdadm SW raid), or lvm. It can work with many different unit sizes and gives you precise control.

---

### Post by Roasted on 2013-01-31
Thanks for the insight. I appreciate it like no other. I do have to wonder though... even for a server, perhaps it makes more sense to boot into GParted Live in order to manipulate partition structure? I'm all about using terminal when possible but there's something about GParted's interface that just makes a truckload more sense while giving me a greater sense of security that what I'm doing is indeed correct. Hmm...

Also, I have to wonder. With mdadm being as smart as it is, why is it so important (based on documentation I read) to make sure the partition type of the drives going into the array is set to "Linux RAID"? Would mdadm not see that, oh, sdb and sdc are not labeled as Linux RAID drives, I must change them first - THEN continue adding them to the array just as the user just instructed me to.

Eh?

---

### Post by darkod on 2013-01-31
I also thought that the raid flag is important, but recently found out that it works without it too.

I would still set it, if not for anything else, to know that the partition is part of mdadm.

But it seems you can add partitions without the flag to md devices and it will accept them.

And for parted vs Gparted, you can use whatever is suitable for you. I'm not against GUI tools, but actually parted is not as confusing as you might think.

Besides, how often are you touching partitions? :)

---

### Post by Roasted on 2013-01-31
> **darkod said:**
> 
But it seems you can add partitions without the flag to md devices and it will accept them.


What I'm questioning is whether or not mdadm puts the raid flag on drives you add to the array. Have you by chance tried adding drives without the raid flag to an mdadm array to see if it adds them afterwards?

> 
Besides, how often are you touching partitions? :)

Which is *exactly* why trying to drill CLI partitioning tools into my head for this particular instance is beginning to feel somewhat of a null point. After all, since it happens that unfrequently that I need to alter partition structures, I'll likely opt for pulling out the LiveUSB flash drive with GParted on it before I dig up old notes on CLI tools to make that adjustment.

---

### Post by darkod on 2013-01-31
I haven't tried myself if there will be a raid flag after adding partitions to mdadm, but i asked another user here in his thread about mdadm, and he said no.

If I understood correctly, the md devices were assembled, and are working, but the raid flag wasn't added.

---

### Post by Roasted on 2013-01-31
> **darkod said:**
> I haven't tried myself if there will be a raid flag after adding partitions to mdadm, but i asked another user here in his thread about mdadm, and he said no.

If I understood correctly, the md devices were assembled, and are working, but the raid flag wasn't added.

I can't help but to shake the million dollar chance-of-your-lifetime question... What is the difference between setting up a mdadm RAID array with your drives labeled as RAID vs not labeling them as RAID? If mdadm works without the RAID flag, where's the benefit to using it? Hmm...

EDIT - Okay. So I blew away the RAID that was existent based entirely out of precaution. I noticed that my WD Reds came across as 3001 GB, which made me nervous in the event that, yeah maybe someday I have a drive failure and get mis-matched drives and then we're looking at a 3000 GB replacement. Since I have backups and all I have to do is rsync the data back over when the resync is done, I figured I'd do this. I first unmounted, stopped, and tore down the array from within the server itself. I also ran the --zero-superblock command against each drive. Then I booted to a LiveUSB session of Ubuntu and fired up GParted. I put a new partition table on each drive (GPT) even though one already existed. Then I created a new unformatted partition on each drive. I set GParted to allow 1024 MiB (1 GB) free at the end of each drive, resulting in 2999 GB of space. This is probably significant overkill, but we're talking 3 TB drives - I can spare 1 GB rather easily. Then I set each flag as RAID. To double check, I rebooted back to Ubuntu LiveUSB and checked in GParted - everything looked good. Dang GParted rocks. 

Fired up the server, SSH'd in, as root: 

```
mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/sdb1 /dev/sdc1
```

Everything synced up in about 6-7 hours, which isn't bad for a 3TB mirror without touching any settings to enhance the speed as I've read about online. It was late at night when it completed, but I kicked off the rsync command for the backup drive and let it run overnight. Come morning, things were all done.

What I did was I put the old 500GB drives into external SATA enclosures that I have. I could have put them in the server, mounted them, and rsync'd that way but I just chose to drop them in the enclosure and push the data from my desktop. At this point I ran this as root:

```
rsync -a --progress /media/storage/* jason@192.168.1.20:/media/storage/
```

The data rsync'd overnight onto the array (mounted as /media/storage on the server). Woke up and everything was there as I expected. 

Bam. Done.

---

