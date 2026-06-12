---
title: "Software RAID help - adding a hot spare?"
date: 2008-08-28
forum: Server Platforms
---

### Post by flatline on 2008-08-28
Hi, I have setup my server running 8.04 x64, installed on two 1TB drives mirrored with mdadm/RAID1.  I just got another 1TB drive practically for free.  I figured I would add this drive as a hot spare to my existing RAID1 array.  

My question is, do I need to partition the hot spare to be identical to the RAID's partition?  I know when first setting up the array, I had to partition the drives identically (but "Use for Physical RAID").  I tried googling but came up empty.  Can someone post a quick walkthrough for adding a hot spare?

Alternatively, I'd be interested to hear if RAID5 is a much better solution.  I am using 3x Western Digital GP drives, so they aren't exactly the fastest drives.  Coupled with the fact that they are softRAID mirrored, and I'm wondering if this is handicapping myself?  It's just a simple file/fuppes server, so someone would have to make a pretty convincing argument in order for me to kill my current array and reinstall everything.

As always, thanks in advance for all the help.

---

### Post by FreakTech on 2008-08-28
I am not sure about adding the hot spare, but RAID 5 would have advantages over you current RAID 1 Config.  RAID 5 would give you faster write times as the data is striped over the drives.  And you still have the redundancy from the parity.

---

### Post by fjgaude on 2008-08-28
Your OS is running on raid1? Have you tried stopping one drive and seeing if the machine still runs, boots?

We know you can't boot from a software raid5 array, at least not that I know of. Maybe one of these days when the Linux kernel is designed to handle such a thing.

When you say "hot spare" you mean if a drive fails the spare is automatically used to re-sync the array? Or that while the machine is powered on you can unplug a drive and plug in another in its place?

The only thing I've done is add as a spare an unused drive, with the same sized partition. Then when needed added the spare to the array. Most of my experience has been with raid5, because of read speed and reliability.

---

### Post by flatline on 2008-08-28
I am aware of the performance gains to be had by moving to a RAID5.  What I'm not so sure about - are they big enough to warrant a complete reinstall of my system?  It's not like my server is especially slow or anything in its current configuration.  If I had all 3 of the drives when I first put it together, I would have opted for RAID5, but that's water under the bridge.  Plus, if I did go RAID5, I feel like my OCD personality would force me to buy ANOTHER drive so I have a spare for that array!

Oh!!1  Related question now that I think about it.  I would like my RAID array to be monitored and email me if a drive becomes unhealthy/fails.  I know this can be done but gave up googling this as well.  I did not install postfix/sendmail, so if you know how to set this up, treat me like the obvious noob that I am.  Thanks!

---

### Post by flatline on 2008-08-28
> **fjgaude said:**
> Your OS is running on raid1? Have you tried stopping one drive and seeing if the machine still runs, boots?

We know you can't boot from a software raid5 array, at least not that I know of. Maybe one of these days when the Linux kernel is designed to handle such a thing.

When you say "hot spare" you mean if a drive fails the spare is automatically used to re-sync the array? Or that while the machine is powered on you can unplug a drive and plug in another in its place?

Yes, my OS is installed on the 1TB mirror array.  I have not simulated a drive failure.  I am fearing now that there is something that could go wrong with the MBR maybe?  I have an 80GB IDE drive that I had *intended* to use as the system drive, _[but no matter what I do I cannot get Ubuntu to recognize the drive]("http://ubuntuforums.org/showthread.php?t=762154")_.  

I did **NOT** realize that you can't boot from a software RAID5 - good to know!

As for the hot spare, yes, that is my definition of hot spare.  ([http://prefetch.net/articles/linuxsoftwareraid.html](http://prefetch.net/articles/linuxsoftwareraid.html))

> A hot spare disk is one that is not used to store data or parity blocks -- it is available to the RAID device for recovery if one of the other disks comprising the device fails. When a disk fault is detected, the operating system begins to resynchronize data from the failed disk onto the hot spare disk. The faulty disk drive can be replaced later. 

That same article suggests using **$ raidhotadd /dev/md0 /dev/hde1**, but I wanted to make sure that this is the correct command, because those instructions are from 2004 and I understand that Linux software RAID has changed a bit since then?

---

### Post by flatline on 2008-08-29
/bump

---

### Post by fjgaude on 2008-08-29
Well, raid5 with have twice the speed, thru-put for a three-drive array, compared to a single drive or a two-drive raid1. The speed for raid5, up to a point, is the speed of one drive times n-1. So a six drive array has five times the speed of one drive.

That add command is old school, not **mdadm**.

It's a good idea to read, study:

 [http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then **/usr/share/doc/mdadm/FAQ.gz**  and **md.txt.gz**
   [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

There's lots to know to successfully run a software raid array, going over all the possibilities, year-after-year. But **backup** is still the number one priority, near-line and off-line, two backups for important data.

---

### Post by flatline on 2008-08-29
Thanks.  So can I just use something like GParted to partition my spare - I have 3 partitions, which come up as md0, md1, and md2 (/, /home, and swap).  Do I need to do
```
mdadm /dev/md0 -a /dev/sdc0
mdadm /dev/md1 -a /dev/sdc1
mdadm /dev/md2 -a /dev/sdc2
```
all as separate commands to add it to the array as a spare?

Also, if I use this
```
mdadm --monitor --mail=me@myemailaddress.com --delay=60 --scan
```
will I need to install postfix, sendmail, either one, or something else?  I'm assuming that it will take care of itself and not need anything else configured to work?

Lastly... looking over the guide you linked, I am thinking that I should have just used the whole of each drive instead of partitioning each one individually... is that correct?  So that I just ended up with one array - md0 - with partitions, instead of 3 different arrays?

Thanks again.  I swear I'm not always this dumb.

---

### Post by flatline on 2008-08-29
nevermind, i just used fdisk to partition the spare disk and the mdadm commands above to add the spare. looks like it worked.

---

### Post by fjgaude on 2008-08-30
Okay, but the acid test is to fail one of the two raid1 drives and then see what happens.

Good raiding.

---

### Post by windependence on 2008-08-31
You cannot boot from software RAID5 because with software RAID, the array is not yet functional when the machine boots. Makes sense right? You could install a small OS drive to use for just the OS and then use the RAID5 array for data. That way you still have the speed advantage and you can rebuild the array if there are problems. I have set up a box like this recently since fjgaude has been telling me software RAID is so wonderful ;). I have the OS on a separate drive and 3 drives in RAID5 software RAID for the data. We'll see how it goes.

One thing I think some people forget. You should probably put full drives in RAID even though you can technically set up just partitions that way. I mean, what if one whoole drive fails? You want to be able to replace it.

-Tim

---

### Post by flatline on 2008-08-31
Ok, another follow-up.   Is there a way in linux/ubuntu to make a bootable backup copy of the system drive?  Something like Carbon Copy Cloner.  After all the tweaking/adding of packages I've done on the server, I'm not really comfortable wiht having no recoverable backup of my system drive.  Can I do something like rsync a copy of my system drive to the RAID5 array?

Thanks for the tips so far.

---

### Post by windependence on 2008-08-31
Sure, you can make an image with dd. 




```
dd if=/dev/sda2 of /path/to/save_to/root.img bs=4096 conv=notrunc,noerror
```

To make a backup of root, and :


```
dd if /path/to/save_to/root.img of=/dev/sda2 bs=4096 conv=notrunc,noerror
```

to write the image of root back to the root partition if you messed up and can't launch the X server, or edited /etc/fstab and can't figure out what you did wrong. It only takes a few minutes to restore a 15 GB root partition from an image file.

Note that your drive may be different than /dev/sda2. My swap file is /dev/sda1 so /dev/sda2 is my root partition.

The file will be as big as your original data so yo may want to compress it like so:

```
dd if=/dev/sdb2 ibs=4096 | gzip > partition.image.gz conv=noerror
```

Makes a gzipped archive of the entire partition. To restore use:

```
dd if=partition.image.gz | gunzip | dd of=/dev/sdb2
```

For bzip2 (slower,smaller), substitute bzip2 and bunzip2, and name the file

```
< filename >.bz2
```


dd is a wonderful tool, BUT:

[B][COLOR="Red"]Warning!! If you reverse the source and target, you can wipe out a lot of data. This feature has inspired the nickname "dd" Data Destroyer.
Warning!! Caution should be observed when using dd to duplicate encrypted partitions.[/COLOR][/B]

-Tim

---

### Post by fjgaude on 2008-08-31
Wonderful advise, Tim. That **dd** command can be intimidating, eh?

BTW, software raid is no more wonderful than hardware. It does remove a point of failure from the system. But, and this is a big "but" in my mind, is the learning curve. The introduction of the superblock really complicates the issue, but it was likely the only good way to create **md** and have it have as much power as it does.

The learning curve would be shortened if a full GUI came into being, but as I've overlooked what it would take, I'm at a loss!

Also to get the speed of multi-drive big arrays actually you need a very fast controller for the drives, and this is only possible with PCI-E or PCI-X motherboards, with fast CPUs and memory.

So, knowledge leads us into the future... <smile>

---

### Post by windependence on 2008-08-31
Well, I'm running this one on a server class mobo using PCI-X so it should be fast. I am testing it right now and will let you know how it does. It will be interesting to see if i can pull a drive out and it stays running like I can with hardware RAID. I haven't tried that yet. ;)

Yes, dd is cryptic, but it is SO powerful and SO fast! I love it. No more GUI disk tools for me.

-Tim

---

### Post by fjgaude on 2008-08-31
Okay, Tim... do let us know how you are doing with software raid, **mdadm**.

Maybe you will write a **tutorial** after you have jumped through all the hoops! <smile>

---

