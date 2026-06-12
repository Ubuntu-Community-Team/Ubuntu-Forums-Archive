---
title: "mdadm Raid 1 using Webmin on Server 10.04 Issues"
date: 2011-03-09
forum: Server Platforms
---

### Post by shadowhacker on 2011-03-09
Hello.

I apologize in advance if this information already exists on these forums. I have spent 3 days fighting this thing and looking for answers and have yet to find one that works.

I recently purchased a Tyan Tomcat K8E semi-server motherboard to build a new file server for my home/small business network. Like an idiot I thought I was going to save some money by buying two 2TB WD20EADS hard drives. Boy was that a mistake. Furthermore, I bought the hard drives on eBay as two identical units, but wound up with two 2TB WD20EADS with different suffixes on the model number. Basically, one is advanced format, and the other is not (according to their labels - this could be incorrect.)

Anyway; I installed Ubuntu server 10.04 LTS, Installed Webmin and its required packages, removed DMwhatever raid (the NVidia fakeraid on this board is not the best,) and installed mdadm.

I first tried using Webmin to set-up the raid. It failed repeatedly on every step. So then I read about the partitioning 4k boundaries for the advanced format drives. I downloaded the latest Gparted CD and set both drives on GPT starting at 1MB (cyl 2048.)

Webmin was then able to raid the drives, but failed to create an ext4 partition on the new array. Back to Gparted live, it created and formatted an ext4 partition on the raid array no problem. Back to webmin, it can't mount the newly formatted array - it says VFS: can't find ext4 filesystem.

All I want is a 2TB raid 1 array made up of two 2tb drives. Speed would be nice but is not make or break like redundancy is in this application.

I have only been using Linux for a couple years, so please take it easy on me. I only really know enough about it to be a little dangerous. :p

---

### Post by shadowhacker on 2011-03-09
Sorry, I guess there wasn't really a question in there. I guess I am wondering if Webmin or Ubuntu 10.04 could be causing my problems with these particular drives (advanced format compatibility.) I could just be royally screwing it up too, or maybe the drives just won't work in raid, period.

I think I have the partitions right. They are Identical starting at 1MiB to wherever Gparted ended them, 1.82TB, EXT4. My understanding is that this should work for both drives because 1MiB has as multiples 512 bytes and 4KiB.

This part is kind of confusing to me though. I partition the raid device (md0) too, right? This is where Webmin has failed for me the last time.

Also, do I need to do something to the mkfs.ext4 routine that the various programs run to make it work on these drives?

Sorry for being all over the place. I have read so many guides and how-tos over the past few days this is really a mess in my head.

Any nudges in the right direction or explanations of this stuff would be much appreciated.

---

### Post by coffee412 on 2011-03-09
> **shadowhacker said:**
> Sorry, I guess there wasn't really a question in there. I guess I am wondering if Webmin or Ubuntu 10.04 could be causing my problems with these particular drives (advanced format compatibility.) I could just be royally screwing it up too, or maybe the drives just won't work in raid, period.

I think I have the partitions right. They are Identical starting at 1MiB to wherever Gparted ended them, 1.82TB, EXT4. My understanding is that this should work for both drives because 1MiB has as multiples 512 bytes and 4KiB.

This part is kind of confusing to me though. I partition the raid device (md0) too, right? This is where Webmin has failed for me the last time.

Also, do I need to do something to the mkfs.ext4 routine that the various programs run to make it work on these drives?

Sorry for being all over the place. I have read so many guides and how-tos over the past few days this is really a mess in my head.

Any nudges in the right direction or explanations of this stuff would be much appreciated.

First some questions:

Are you looking to raid the two drives together and then install Ubuntu on them or do you have an existing drive with ubuntu installed and just added the two drives for raid?

My understanding is that if your going to install Ubuntu to the drives then you setup your raid using your motherboard bios and then boot the install disk and hopefully the raid shows up for an install point.

If your going to use mdadm to setup a raid then here are the steps in a nutshell:

1. Fdisk the drives and choose the "linux raid auto " (fd) partition scheme when fdisking the drives. Then write changes to disk. This should be done on both disks and make them one big partition.

2. Now create your raid 
To make the device:
mdadm --create /dev/md0 --level=raid1 --force /dev/hdb1 /dev/hdc1

Change the devices to match your two drives.

3. Now format this raid

mkfs.ext3 /dev/md0

4. Add the raid to your fstab file in /etc/fstab

/dev/md0 /mymountpoint ext3 defaults 0 0

5. create your /etc/mdadm.conf file so it starts when booting.

mdadm --detail --scan --verbose > /etc/mdadm.conf

I think I covered the basics here. If you google you can find lots of help with mdadm. Its not really that hard.

coffee:)

---

### Post by shadowhacker on 2011-03-09
Thank you for the response.

The system files are on a separate 6GiB IDE disk, the raid array is only for storage for home media sharing and my business files.

The first time I attempted this setup I went with pretty much the method you described. It didn't work, but now I know that's because I didn't specify the correct parameters required for the advanced format drive.

However, through reading many many many Google search results, I was under the impression that if I do chose to use Fdisk, and inherently the msdos partition table, I would not be able to upgrade my array in the future to say raid 5 or 1+0 by adding more drives due to the 2tb limit. That's why I was sticking with gparted and the GPT partitioning scheme.

GPT does not however have the option for autodetect raid file systems. Am I to understand that mdadm only works with this file system?

---

### Post by srs5694 on 2011-03-10
> **shadowhacker said:**
> GPT does not however have the option for autodetect raid file systems. Am I to understand that mdadm only works with this file system?

First, it's important that you understand that MBR and GPT are both partitioning systems, not filesystems. Partitioning systems let you carve up a hard disk in whatever way is convenient, whereas filesystems enable access to specific files in defined ways.

RAID (and hence mdadm) can either modify the way disks look to the OS (in the case of hardware RAID) or can be used to merge disks or partitions into new devices that can be used to store filesystems or that can be used like disks and partitioned.

This last point is important because, depending on how you configure software RAID, you could have either one or two partition tables (or conceivably even none, but that's unlikely):


[list]
[*]Typically, you'll partition your disks into one or more partitions each. These partitions will be Linux RAID partitions, so they'll hold RAID data, and you'll merge together partitions from multiple disks into single RAID devices (/dev/md0, etc.).
[*]You can optionally partition the RAID devices, producing partitions called /dev/md0p1, /dev/md0p2, and so on. Typically, you'll only do this if you put one big partition on each component device, merge them together into one big RAID device (/dev/md0), and you want to subdivide it, rather than put multiple partitions on each component device that you then combine together and use more directly as multiple RAID devices (/dev/md0, /dev/md1, etc.).
[/list]


If your physical disks are under 2 TiB in size, you'll be able to use MBR with them. The only need for GPT on physical disks is if they exceed 2 TiB (or, more precisely, 2^32 sectors) in size. That said, RAID issues aside, GPT has certain advantages over MBR, but they're mostly pretty minor on sub-2TiB disks. Overall, I wouldn't hesitate to use MBR on sub-2TiB physical disks if the GPT/RAID combination is causing problems.

If you want to create a second partition table within your RAID array, and if the RAID array does (or might eventually) exceed 2 TiB in size, the using GPT makes sense. If you split your physical devices into multiple partitions and then put filesystems on the main RAID devices (/dev/md0, /dev/md1, etc.), then there's no need for that second partition table and hence no need for GPT.

My understanding of the interactions of RAID and GPT is rather limited, since I've not done much with RAID since getting into GPT, and I only dabbled with software RAID before that. (My own personal need for RAID features is very limited.) That said, my understanding is that Linux's RAID tools don't work too well with GPT on physical disks, but you can use GPT on the RAID devices themselves. For the moment, this is fine; however, once disks of over 2^32 sectors become more common, Linux's software RAID tools had better work well with RAID.

---

### Post by coffee412 on 2011-03-10
> The system files are on a separate 6GiB IDE disk, the raid array is only for storage for home media sharing and my business files.
I was under the impression that if I do chose to use Fdisk, and inherently the msdos partition table


Your not going to use a MSDOS partition. Just set the partition as linux raid auto. To make it easy, Make one large partition on each drive using fdisk and change the partition type to "linux raid auto" with is listed if you use the menu option L in fdisk. Remember to write your changes to disk before leaving fdisk. Then follow up with the mdadm commands I gave you with the correct devices (/dev/sd*) substituted in. 

When you have assembled your raid with mdadm then you can format it. I used ext3 just because it is kinda standard. But if you want to use ext4 thats fine.

coffee

---

### Post by shadowhacker on 2011-03-10
Thanks for the replies. I think I am understanding this better now.

If I understand correctly, I should partition my drives with MBR (msdos partitioning system not a file system,) set them at 1MiB start, and use the Linux raid autodetect file system. Then, since I want just 1 large 2TB partition, I should just raid these partitions and NOT partition the new md0, correct?

I guess this would work for future expandability because it would make the most sense to add more 2TB drives in the future, which MBR would work on. So, I should just leave GPT alone until the GNU kernel supports it better or until I have bigger hard drives.

So, if at some point I do add more 2TB drives, and change from raid 1 to raid 1+0 or raid 5, I would set them with the same MBR parameters, and just use GPT on the array itself (md0,) right?

Sorry if my nomenclature is not accurate. Like I said I'm fairly new to Linux, but I've been using PC products since IBM DOS 4 and MS-DOS 5. The concepts stay the same it's just the names that keep changing. :-k

---

### Post by coffee412 on 2011-03-10
> **shadowhacker said:**
> Thanks for the replies. I think I am understanding this better now.

If I understand correctly, I should partition my drives with MBR (msdos partitioning system not a file system,) set them at 1MiB start, and use the Linux raid autodetect file system. Then, since I want just 1 large 2TB partition, I should just raid these partitions and NOT partition the new md0, correct?

I guess this would work for future expandability because it would make the most sense to add more 2TB drives in the future, which MBR would work on. So, I should just leave GPT alone until the GNU kernel supports it better or until I have bigger hard drives.

So, if at some point I do add more 2TB drives, and change from raid 1 to raid 1+0 or raid 5, I would set them with the same MBR parameters, and just use GPT on the array itself (md0,) right?

Sorry if my nomenclature is not accurate. Like I said I'm fairly new to Linux, but I've been using PC products since IBM DOS 4 and MS-DOS 5. The concepts stay the same it's just the names that keep changing. :-k

No your not understanding perhaps. There is NO ms-dos file system/partition scheme.

YOu will create a linux-raid-auto partition on each drive by using fdisk.

You will then use mdadm to create the raid like I told you. This will give you an unformatted device called /dev/md0 . The device called /dev/md0 is your raid made up of the two drives. Now you format it

mkfs.ext3 /dev/md0

Now after its formatted and all you have to do is mount it.

mount -t ext3 /dev/md0 /mnt/somedirectory-you-made

Be sure to follow my earlier post on creating your /etc/mdadm.conf file and adding your settings for the raid to your /etc/fstab file.

HOpe that makes it clearer for you.

coffee

---

### Post by shadowhacker on 2011-03-10
In fact there is an msdos partition scheme/table, it is called MBR which fdisk uses by default. This has been used by PCs since the 8-bit days (I can pull out my IBM PC XT to verify if necessary.) This is not to be confused with the MS-DOS (fat) file system. If I caused this confusion, I do apologize.

So pretty much what I said in my previous post is EXACTLY what I need to do with the exception being that my raid array (md0) needs to be formatted after creation with mkfs.

Thank you. It makes it CRYSTAL clear.

I'm sorry that I've wasted your time.

---

### Post by coffee412 on 2011-03-10
> **shadowhacker said:**
> 

Thank you. It makes it CRYSTAL clear.

I'm sorry that I've wasted your time.

You didnt waste my time. YOur learning and that makes it all worthwhile. 

There are all kinds of partitions available to be made by fdisk. But in linux we dont care about dos or windows or anything but linux partitions. In our case we want linux raid auto partitions. So, What I was saying was - forget about dos. We are not concerned about it and dont need it. We are doing it in linux.

Good job so far - Hope it works out ok for you.

---

### Post by shadowhacker on 2011-03-10
> **coffee412 said:**
> There are all kinds of partitions available to be made by fdisk. But in linux we dont care about dos or windows or anything but linux partitions. In our case we want linux raid auto partitions. So, What I was saying was - forget about dos. We are not concerned about it and dont need it. We are doing it in linux.

I think this is where we were talking past each other. I was talking about partition tables, and not the partitions themselves or the file systems or OSes on them. Sorry for the confusion.

Anyway, after creating new msdos partition tables on the drives and deleting the raid array and super blocks with the Gparted Live CD, I rebooted to Ubuntu and set up identical Linux RAID partitions on SDB and SDC with an extent of 2048-243201 under Webmin. This is located at Hardware > Partitions on Local Disks > SATA Device X > Add a Primary Partition, and is just a fancy front end for fdisk as I understand it.

I then used Hardware > Linux Raid (mdadm front end) to create a forced raid 1 array from sdb1 and sdc1. I used the default 4k chunk sizes, but I'm not sure what that does?

The array is resyncing now, and is 9% built. Should be done in about 8 hours. ](*,) These drives only do about 50MiB/s on rebuild.

So, when this is done, I need to format md0, mount it, and make it persistent. Are there any special parameters for mkfs I need to use to optimize for the 4k sectors on the advance format drives?

Thank you for all of the help. I am learning, just a little slower than most. :p

---

### Post by shadowhacker on 2011-03-10
Wow! Ok, the GPT does apparently have major issues with mdadm. Now that I am using the old msdos style MBR in conjunction with the linux raid autodetect filesystem and the correct partition alignment, I am getting a steady 100MiB/s on the resync!!! Before it always started at 150 and dropped to 50 by the end.

Hopefully the format and mounting will work and I will be golden. I will know in 253.7 minutes lol.

---

### Post by srs5694 on 2011-03-10
> **shadowhacker said:**
> If I understand correctly, I should partition my drives with MBR (msdos partitioning system not a file system,) set them at 1MiB start, and use the Linux raid autodetect file system. Then, since I want just 1 large 2TB partition, I should just raid these partitions and NOT partition the new md0, correct?

Yes -- at least, that's one way of doing it. Another would be to create partitions on /dev/md0. Personally, I don't see much point in doing that -- it just adds another layer of complexity.

> I guess this would work for future expandability because it would make the most sense to add more 2TB drives in the future, which MBR would work on. So, I should just leave GPT alone until the GNU kernel supports it better or until I have bigger hard drives.

Yes. FWIW, the Linux kernel (the GNU kernel is Hurd) supports GPT just fine. My understanding is that it's the mdadm utilities that have GPT-related problems.

[quote=coffee412]No your not understanding perhaps. There is NO ms-dos file system/partition scheme.[/quote]

Terminology on this score is rather confusing because several different names have been applied to the [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) partitioning system over the years. My own preferred term today is "MBR;" however, my view is not universal. For instance, consider what happens when you clidk "Advanced" in the dialog box that GParted presents when you tell it to create a new partition table:

[IMG]http://www.rodsbooks.com/gparted.png[/IMG]
Note that GParted is calling the partition table type "msdos". This is an MBR partition table type, though, and it can be used to hold nothing but Linux or other non-DOS partitions (or to hold DOS partitions, Windows partitions, etc.). Some people also use the term "BIOS partition table" to refer to this partition table type, although the BIOS really has very little to do with it.

Linux's fdisk utility mainly edits MBR partition tables, although you can adjust it to handle a couple other types. Since the original question involved a choice of MBR vs. GPT, though, it's important to note that Linux's fdisk can't handle GPT, except to detect GPT data and display a warning if it's found. To deal with GPT disks, you need either a tool based on libparted (such as GNU Parted or GParted) or a GPT fdisk tool (gdisk or sgdisk).

---

### Post by coffee412 on 2011-03-10
> **shadowhacker said:**
> Wow! Ok, the GPT does apparently have major issues with mdadm. Now that I am using the old msdos style MBR in conjunction with the linux raid autodetect filesystem and the correct partition alignment, I am getting a steady 100MiB/s on the resync!!! Before it always started at 150 and dropped to 50 by the end.

Hopefully the format and mounting will work and I will be golden. I will know in 253.7 minutes lol.

(coffee gives shadow 3 "ata-boy's" )

You will be on your way soon! 

I played around with webmin a bit but found that doing it in a term window is actually alot easier for me. But to each his own I guess. Glad things are starting to "jell" for you. After you get it all done you can run a command like: mdadm --examine /dev/md0 and check out your raid. 

Dont forget to setup your email in mdadm so that if a drive dies or starts to have "issues" it will email you and let you know. I will let you look that up as its not too hard to do. 

Have fun!

coffee ;)

PS - Climax / K-zoo is old stomping ground for me. My home town is Marshall, Mi

---

### Post by shadowhacker on 2011-03-11
Thanks for the help and encouragement all.

Unfortunately, this is what the format resulted in:

```
Executing command mkfs -t ext4 -b 4096 -q /dev/md0 ; partprobe ..

/dev/md0 alignment is offset by 512 bytes.
This may result in very poor performance, (re)-partitioning suggested.
device-mapper: deps ioctl failed: No such device or address
Segmentation fault

.. command failed!
```

Somehow I can still mount md0 though, and it appears fine???

I am very weary of using it though having errors during creation.
Any ideas?

I tend to agree with you about CLI being more convenient than Webmin. I usually use CLI only on my workstations, but on the servers I don't use them enough. Webmin remembers all of the changes I made and keeps nice backups of all the config files, so I don't have to remember what I did. :D

I saw that email option on mdadm and was very excited about that. Do I need to set up an SMTP server on the box too or can it just email from the program?

It's pretty cool to meet a local. Actually it's kind of ironic. Growing up, my stomping grounds were Bellevue and Marshall. :P

Take care,
Andrew

---

### Post by shadowhacker on 2011-03-11
> **srs5694 said:**
> ...FWIW, the Linux kernel (the GNU kernel is Hurd) supports GPT just fine. My understanding is that it's the mdadm utilities that have GPT-related problems.

Thank you for that srs5694. I've had it backward all along. We are running some GNU software on the Linux kernel, not the other way around. Duh! :oops:

I realize now that the problems are either in mdadm or the drives themselves. Sorry if I falsely accused anyone's software. Really I expect to do some tweaking on free software anyway.

[IMG]http://www.rodsbooks.com/gparted.png[/IMG]
Yes, this is what I was talking about.

> **srs5694 said:**
> ...Personally, I don't see much point in doing that -- it just adds another layer of complexity.
Yes! This is what has been confusing me so bad I think. How does hardware raid do it? Doesn't it just give you volumes based on settings for it using the raw drives with no partitions? Can I do this with mdadm?

The cost of a hardware raid card is seeming like less and less of a factor as the days wear on.

---

### Post by srs5694 on 2011-03-11
> **shadowhacker said:**
> Thanks for the help and encouragement all.

Unfortunately, this is what the format resulted in:

```
Executing command mkfs -t ext4 -b 4096 -q /dev/md0 ; partprobe ..

/dev/md0 alignment is offset by 512 bytes.
This may result in very poor performance, (re)-partitioning suggested.
device-mapper: deps ioctl failed: No such device or address
Segmentation fault

.. command failed!
```

It looks like you're using the parameters for mkfs.ext2 with mkfs; the two utilities have very different options. In your case, my suspicion is that mkfs is trying to interpret "-q" as the device filename. (Although maybe not; the error message does mention /dev/md0.)

> Somehow I can still mount md0 though, and it appears fine???

If you can mount it and it seems fine, then you didn't need to issue a mkfs on it, unless you wanted to change from one filesystem type to another or if you had reason to believe that the original filesystem was so badly damaged that creating a new one was in order.

You could always try an fsck on the device to confirm that it's OK.

> How does  hardware raid do it? Doesn't it just give you volumes based on settings  for it using the raw drives with no partitions? Can I do this with  mdadm?

The cost of a hardware raid card is seeming like less and less of a factor as the days wear on.

With hardware RAID, you plug your disks into the hardware RAID controller and the controller then presents the illusion to the OS that there's a single disk. So for instance, if you plug three 2TB disks into a hardware RAID controller and tell it to use RAID 5 with it, the OS will see a single 4TB disk (called /dev/sda or some other standard disk filename in Linux), which you then partition and use as if you had a single 4TB disk. Hardware RAID also has the advantage that any computational tasks are handled by the controller, so your CPU isn't tied up computing checksums and whatnot. Similarly, your computer's I/O bus just reads or writes one copy of the data, vs. writing the data plus checksums or two copies of the data with some forms of RAID.

The drawback to hardware RAID is that your data are held hostage to the specific hardware RAID card you've got. If that card dies, you probably won't be able to replace it with a model from another manufacturer. That could be a problem if, say, your manufacturer goes out of business or discontinues support for whatever format it uses for data on the individual physical disks. OTOH, with all sorts of old stuff available via eBay, you could probably get a used replacement pretty quickly. If you can't afford downtime, though, keeping a backup RAID card on hand might be in order.

You can do something very similar with mdadm, but in this case, you'd group your raw devices (or partitioned raw devices, with one partition per disk) into a single /dev/md0 device, which you'd then partition as you see fit. If you just want one filesystem on a software RAID device, there's very little practical difference between this and doing it the way you've got it now.

---

### Post by shadowhacker on 2011-03-11
[QUOTE=srs5694]If you can mount it and it seems fine, then you didn't need to issue a mkfs on it, unless you wanted to change from one filesystem type to another or if you had reason to believe that the original filesystem was so badly damaged that creating a new one was in order.[/QUOTE]
So, md0 is already formatted linux raid like the 2 source partitions and there is no need to format it again?

---

### Post by shadowhacker on 2011-03-11
> **srs5694 said:**
> It looks like you're using the parameters for mkfs.ext2 with mkfs; the two utilities have very different options. In your case, my suspicion is that mkfs is trying to interpret "-q" as the device filename. (Although maybe not; the error message does mention /dev/md0.)

I checked this out and it appears that mkfs is a front end for all of the various file system making programs. The only switch it is using is -t ext4, which makes it call mke2fs with all of the rest of the parameters being passed to mke2fs. So, -q is putting mke2fs in quiet mode, I think.

---

### Post by srs5694 on 2011-03-11
> **shadowhacker said:**
> So, md0 is already formatted linux raid like the 2 source partitions and there is no need to format it again?

Not quite:


[list]
[*]The fact that /dev/md0 exists at all means that you've got a software RAID array in place. Accessing /dev/md0 (in any way, whether it's by mounting, by using dd on it, etc.) means that the array is functioning, at least minimally.
[*]The fact that you were able to mount /dev/md0 means that /dev/md0 has a filesystem on it. Adding /dev/md0 to a RAID array would technically be possible, but would be pointless, since it already is a RAID array. (There are situations where you might want to do this, but AFAICT you aren't in such a situation.)
[/list]


Remember, /dev/md0 refers to a logical (or virtual or meta-) device -- the RAID array you constructed using mdadm. Accessing this device results in access to one or more underlying physical devices. Keeping the various levels of devices straight in your head is one of the challenges of dealing with software RAID.

---

### Post by shadowhacker on 2011-03-11
> **srs5694 said:**
> Not quite:


[list]
[*]The fact that /dev/md0 exists at all means that you've got a software RAID array in place. Accessing /dev/md0 (in any way, whether it's by mounting, by using dd on it, etc.) means that the array is functioning, at least minimally.
[*]The fact that you were able to mount /dev/md0 means that /dev/md0 has a filesystem on it. Adding /dev/md0 to a RAID array would technically be possible, but would be pointless, since it already is a RAID array. (There are situations where you might want to do this, but AFAICT you aren't in such a situation.)
[/list]


Remember, /dev/md0 refers to a logical (or virtual or meta-) device -- the RAID array you constructed using mdadm. Accessing this device results in access to one or more underlying physical devices. Keeping the various levels of devices straight in your head is one of the challenges of dealing with software RAID.

Right, this is indeed what has been messing with my head.

Ok, Assuming I wiped both disks clean of all partitions and super blocks, put an identical 2tb Linux Raid partition on each, and created md0 with mdadm; would the resulting md0 need to be formatted/partitioned or could it be mounted and used as-is?

I was able to mount md0 after the failed ext4 install, but I did not try to mount it before formatting.

---

### Post by shadowhacker on 2011-03-11
Ok, now some definite weirdness.

I found some tools for the WD TLER feature on these drives (has to do with SMART messing with RAID during error correction.) I made a Windows98 boot cd with the TLER tools on it and rebooted the server. Only one of the drives was able to enable TLER so they are definitely quite different, but identical in size and seemingly dimensions. Both disks are virtually new and have no smart errors whatsoever, so I would assume this is not causing problems for me anyway (yet.)

Anyway, upon rebooting Ubuntu server; I got some complaints about /dev/sda5 (linux swap) and /dev/md0 (raid) taking too long to initialize. I still had md0 mounted, but the raid array was gone. I had them both set to persistent on Webmin, and the WD TLER tools only mess with the drive firmware and should not have touched the data. I'm so confused.

---

### Post by srs5694 on 2011-03-11
> **shadowhacker said:**
> Ok, Assuming I wiped both disks clean of all partitions and super blocks, put an identical 2tb Linux Raid partition on each, and created md0 with mdadm; would the resulting md0 need to be formatted/partitioned or could it be mounted and used as-is?

That depends on how you erased the old data and what sizes you gave to the new partitions. If you happened to reconstruct exactly the old configuration, it's conceivable that your old filesystem would remain intact, despite your having wiped and then re-created the RAID data. This would be analogous to removing the roof and walls of a house, rebuilding the house, walking in and finding your furniture untouched. If you rebuilt the RAID array even slightly differently, this wouldn't work, though -- it'd be like finding your sofa embedded in a wall.

I'm afraid I can't help you with your TLER issue, since I know next to nothing about this subject, and I can't say why your array is no longer functioning.

---

### Post by shadowhacker on 2011-03-13
Hmmm. Well I guess there is some problem between these new drives and Ubuntu's partitioning/file system tools.

I ended up making it work by once again rebooting to the Gparted Live CD. I deleted the old superblocks with mdadm, set up my partitions (sdb1 and sdc1) to 1MiB-end of drive with Gparted, formatted them ext3, and set the raid flag.

Then I created the array from the Gparted live CD:

```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
```

And formatted it:

```
sudo mkfs -t ext3 /dev/md0
```

After it synched I rebooted back to Ubuntu and was once again faced by an fstab mounting wait for the raid volume.

I think fstab gets loaded before the mdadm.conf file?

Anyway, I removed the mount from fstab and I made this script which works nicely: under Webmin System > Bootup and Shutdown > Create a new bootup and shutdown action:

```
#!/bin/sh
# Assembles a raid array (md0) from /dev/sdb1 and /dev/sdc1, and mounts it at /media/2tbraid1

case "$1" in
'start')
	sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
	sudo mount /dev/md0 /media/2tbraid1
	;;
'stop')
	sudo umount /dev/md0
	sudo mdadm --stop /dev/md0
	;;
*)
	echo "Usage: $0 { start | stop }"
	;;
esac
exit 0

```

Now at every boot I have my raid accessible. I also ran e2fsck on it and all looks good.

I had gone through the exact same process using Ubuntu several times and got errors, although the array worked and could be mounted. I don't know if Ubuntu was just complaining for no reason or what, but I didn't want to take the chance with important data.

I am in the process of copying the 800ish GB from my old file server (2 x 500 GB non-raid HDDs) to the new array.

I want to pull the 2 500 GB HDDs from the old server after this transfer and put them in the new server. I want to put them in another raid 1 array, then make an array from the two arrays which is 2.5 TB. This final array would be linear raid, correct?

Thank you so very much Coffee and srs5694. I would not have made it this far without your insights. Having this thing finally work makes the past 10 days seem insignificant all of a sudden.

---

