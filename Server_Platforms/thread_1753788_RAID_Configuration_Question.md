---
title: "RAID Configuration Question"
date: 2011-05-09
forum: Server Platforms
---

### Post by calelettus on 2011-05-09
I'm throwing together a simple server using a spare motherboard I've got laying around - not a true server but a simple, inexpensive way to serve files. I thought I'd try setting the box up in the following way. Please tell me if this will work and/or why it wouldn't:

Since the MB has 4 SATA ports and 1 - IDE I thought I'd use a 160g IDE hard drive for the actual Ubuntu OS install. Then, I've got four 1T SATA drives I would like to configure as RAID 5 to hold my data files - mainly music and large documents. 

In the initial install of Ubuntu server you are given the option of setting up RAID. Can I setup RAID for the four SATA drive AFTER getting the OS installed? Anything wrong with my plan? Thanks!

---

### Post by YesWeCan on 2011-05-09
Yes, you can set the 4 HD RAID up after installing Ubuntu. You need to install mdadm (multiple disk administration) first.

Why do you want RAID at all?
1) Note that striping RAIDs like 5, 6 and 10 can improve your disk read speeds.
2) Mirroring RAIDs like 1 and 10 can improve your data security. But RAID doesn't protect against accidental erasure.
3) Parity RAIDs like 5 & 6 may or may not improve your security, depending on a number of factors. RAID 6 is a lot better than 5 in this respect. Always maintain a backup of critical data.

IMO

---

### Post by NadirPoint on 2011-05-09
Raid 5 is more for availability than security.  If you want availability AND security, with four drives, you could do a 3-drive Raid5 with the 4th as a hot spare.

That would be assuming 2T is sufficient for your storage space requirements.

---

### Post by YesWeCan on 2011-05-09
Also, my understanding is that in a mirroring RAID the system performance is not affected much if a drive fails. In parity RAID some data is actually missing and parity calculations requiring reads of all the remaining disks are needed to reconstruct it, thus causing a significant performance hit. Mirror RAIDs are also faster to rebuild once a replacement disk is added.

---

### Post by calelettus on 2011-05-09
Well, I would still back up, of course. I'm just trying to figure out if it would be worthe the effort.

What about skipping the 160g IDE and simply using the four SATA drives as two mirrored partitions, installing the OS on one? This isn't mission-critical stuff.

---

### Post by YesWeCan on 2011-05-09
It is sort of a personal taste question, so you'll have to decide what configuration you like best.

I like the idea of putting the OS on its own HD in IDE. IDE is a little slow compared to SATA but this is a basic file storage PC you are putting together so maybe not a problem. Then you have the 4 1TB disks as pure data storage. Of course the OS is not in a mirror but its not such a big deal if the OS disk fails - you reinstall it and the apps from your backup. But if you were running a website where interruption of service was a problem then you would want the OS on the RAID too.

It is normal to allow 20GB or 30GB for the OS install but have the /home partition separate. With the OS on IDE you could make a single, 30GB partition for Ubuntu. Later you could make another for another OS you may want to try or just make the whole thing Ubuntu for ease. With the OS on one of the RAID1s you would create a logical volume (volume=partition in this context) of 30GB and then another for the /home of whatever size. With LVM you can even "join" the two RAID1s to have logical volumes spanning across them; so they act like one big RAID1 disk. Or you can keep it simple and avoid LVs and just install the OS on one RAID1 and use the whole space.

Or you could make a RAID1+0 (RAID0 of two RAID1s) in the install and this will give you one big logical disk, faster than separate RAID1s because of the striping.

It's up to you. There is no obvious "best" way to do this. I advise to keep it simple unless you enjoy challenges.

I happen to have 4 1TB disks in RAID1+0 with everything installed to them and multiple partitions using LVM. I wanted high speed and data reliability. I also wanted to see if I could set it up! I enjoy challenges. This is a more complicated thing to set up but I believe the Ubuntu installer will take care of it for you once you work out how to use it.

That's my 2 cents worth.

---

### Post by NadirPoint on 2011-05-09
If as you say, it is not "mission critical," then you have to ask yourself what "is" critical, or at least of some significance to you.  More storage space?  Speed?  You must establish the requirement before you can make the right decision about how to best employ the available hardware.

---

### Post by NadirPoint on 2011-05-09
> **YesWeCan said:**
> Or you could make a RAID1+0 (RAID0 of two RAID1s)
That's a best of both worlds - speed and redundancy combined.  But it wastes disk space and electricity.

Personally, if I had 4 drives and availability and/or redundancy was not the issue, I would run a Raid5 and keep one on the shelf as a cold spare in the unlikely event I ever needed it.

---

### Post by calelettus on 2011-05-09
NadirPoint and YesWeCan, thanks for your comments. I think I'll play for a while and try setting things up both ways for the experience!

---

### Post by a2j on 2011-05-09
I'd just do RAID10 with those 4 1Tb hdds and call it a day. with OS installed on them. otherwise, what are you going to do with that RAID5 when your single EIDE drive (with OS on it) fails?

---

### Post by NadirPoint on 2011-05-09
Sorry, but I never mentioned the old 160 drive because it seemed irrelevant to me.  Wouldn't bother with it at all.  Just slow things down and make them more complicated than they need to be.

---

### Post by rubylaser on 2011-05-09
RAID10 is great and certainly will work well in this case.  The main problem, you'll have is if you want to spin down your hard drives when they're not in use.  With your OS on the RAID array, spinning down can be problematic.  I would personally suggest you just install your OS on the IDE drive, and put the RAID array on on the 1TB drives after the fact.  

As a caveat, if you ever want to add more drives, and expand your RAID10 array, mdadm currently doesn't supporting growing an array like this with an extra disk set.  If you need to allow for the option to add extra disks, you'll want to go with a different RAID level.

---

### Post by YesWeCan on 2011-05-09
> **rubylaser said:**
> As a caveat, if you ever want to add more drives, and expand your RAID10 array, mdadm currently doesn't supporting growing an array like this with an extra disk set.  If you need to allow for the option to add extra disks, you'll want to go with a different RAID level.
Yes.
Alternatively, I presume one can have as many separate RAID arrays of whatever type as one likes. With LVM on the first RAID10 would it be true that a second RAID10 could be added to the original LVM volume group thus effectively expanding the original array size? Just curious.

---

### Post by rubylaser on 2011-05-09
Would that be possible?  Sure, but the overhead would be a fair amount, and troubleshooting a big problem with either LVM or mdadm, could be a real bear to figure out :)  I'd probably just make sure I have the appropriate number of disks from the get go, or just resize with larger disks as they come out.

---

### Post by a2j on 2011-05-10
> **rubylaser said:**
> RAID10 is great and certainly will work well in this case.  The main problem, you'll have is if you want to spin down your hard drives when they're not in use.  With your OS on the RAID array, spinning down can be problematic. 

Using WD "green" hdd in RAID10 and no issues what so ever with that.

---

### Post by rubylaser on 2011-05-10
> With your **OS** on the RAID array
On your boot drive?  It will work perfectly fine with the OS installed on a separate drive. I just can't see that working with your OS on the RAID10 array.  There's always a process running or a file being written, so the array shouldn't be able to spin down.

---

### Post by deconstrained on 2011-05-10
I also vote RAID10. Faster and more reliable.

OP did not say putting the OS on the array was in the plans--but leaving it on the 160GB IDE drive where it was in the first place.

---

### Post by a2j on 2011-05-10
I thought using RAID was to get some redundancy and protect the data and reduce downtime when the drive dies. so putting OS on the single drive will not give you any protection. so unless you enjoy rebuilding the server every time the drive goes down...

I don't see anything wrong with having OS on the RAID10. besides, you can't install /boot to any other software RAID but 1/10.

---

### Post by rubylaser on 2011-05-10
The OP did mention running off the IDE drive, and I mentioned that as a good idea in a previous post in this thread.  Others started mentioning running the OS from the RAID10 array, so I was just providing a few of the caveats (i.e. not being able to expand a RAID10 array with mdadm, and the spindown issue).

If you read what I posted, I mentioned RAID10 is a great idea, and would work well in this scenario as long as the OP understands the inability to expand the array in the future (other than by swapping out to larger disks).  The fact is that most home users don't have the money to make a large investment in disks all at once, so they need to ability to add disks to the array in the future.  This is possible with RAID5/6 in mdadm, but not RAID10.  The other problem is that most home users want maximum storage space, so RAID10 is less than ideal in this scenario.

---

### Post by rubylaser on 2011-05-10
> I thought using RAID was to get some redundancy and protect the data and reduce downtime when the drive dies

It is...This is a home server application, so a little downtime to restore the server from the snapshot you have of your OS install isn't going to be too difficult (you do have a backup of your OS and data on your array right?).

I understand that you can only boot from RAID 1/10.  I was simply stating that running 4 hard drives full time would draw more energy than running 1 boot drive with the ability to spin down the other drives.  The energy savings was a caveat, not a recommendation on my part.

---

### Post by deconstrained on 2011-05-10
> **a2j said:**
> I don't see anything wrong with having OS on the RAID10. besides, you can't install /boot to any other software RAID but 1/10.
Neither do I, and I in fact have my OS on a RAID 10. The extra work to get it to boot properly may be a bit of a hassle for the OP though.

On the other hand, setting up an exotic/unorthodox root FS environment (i.e. some combination of mdadm, dm-crypt and/or lvm2) is a great way of taking off the training wheels and learning more about the boot process, and how to repair/correct it if it stops working.

---

### Post by a2j on 2011-05-10
> **deconstrained said:**
>  and I in fact have my OS on a RAID 10. The extra work to get it to boot properly may be a bit of a hassle for the OP though.


I do too, on the server and on the laptop. I didn't have any hassle to make it boot properly. Unless I'm missing something. :?

---

### Post by klavmanian on 2011-05-10
If I may introject, you mentioned that you were booting from a linux software raid / lvm. (RAID 10) Do you care to explain how you did this. 11.04 is giving me errors during grub installation. 

I am using the 11.04 alternate installer and configuring the computer to use a RAID 10 for "/". So this will be where everything resides.

More information here...
[http://ubuntuforums.org/showthread.php?t=1748776](http://ubuntuforums.org/showthread.php?t=1748776)

Sorry to interrupt the current topic.

---

### Post by deconstrained on 2011-05-10
> **klavmanian said:**
> If I may introject, you mentioned that you were booting from a linux software raid / lvm. (RAID 10) Do you care to explain how you did this. 11.04 is giving me errors during grub installation.
GRUB is always the most annoying part. As best I can remember (when I upgraded to 11.04 and everything broke), I reinstalled GRUB to each hard drive, one by one (as described [here](https://wiki.archlinux.org/index.php/Installing_with_Software_RAID_or_LVM#Install_Grub_on_the_Primary_Hard_Drive)) just so I wouldn't have to worry about choosing the wrong hard drive as the primary boot device in the BIOS settings, and I used the --modules=raid flag. The rest (lvm/dm-crypt) is all in properly configuring /etc/crypttab, /etc/fstab and /etc/mdadm/mdadm.conf, and the Debian initrd-building tools plus grub-update parse/analyze those configuration files and automatically do the rest of the work for you.

---

### Post by YesWeCan on 2011-05-10
When I set up my 4 disk RAID10 with OS on it, I read a guide that also set up a 100MB RAID1 across 2 of them for /boot on the premiss that Grub would not boot RAID10 directly. However, I seem to have this idea in my mind that this is no longer the case and Grub doesn't need a separate /boot. Not sure tho. Anyone know?

In any case, I think the Ubuntu Alternative CD installer will do all the work for you (once you get your head around the peculiar logic of the installer).

I still like the OS on IDE drive arrangement in this particular situation. I like the simplicity of it. I like the way the array can be spun down to save power. And it might make upgrading the OS a little less nervy. One can always back up the OS to the array every night for simplicity. Also nice if the OS drive is an SSD (on SATA of course).

---

### Post by YesWeCan on 2011-05-10
> **klavmanian said:**
> If I may introject, you mentioned that you were booting from a linux software raid / lvm. (RAID 10) Do you care to explain how you did this. 11.04 is giving me errors during grub installation. 

I am using the 11.04 alternate installer and configuring the computer to use a RAID 10 for "/". So this will be where everything resides.
I know this works in 10.04:
During install, create 4 equal-sized partitions for RAID10. Create two equal-sized partitions on any 2 of the disks for RAID1 (you could set up 4 but 2 is the minimum needed to guarantee bootability if a single disk fails). The RAID10 should be / and the RAID1 /boot. Grub should be installed to the two disks with the RAID1 partitions.
In hindsight, I'd make the /boot partitions 300MB.
I also set up the SWAP as an LVM partition atop RAID10 so that if a disk failed while the OS was using swap space, the OS would not get screwed. Unlikely event but it was convenient to set up.

---

### Post by a2j on 2011-05-11
you should be able to have /boot on RAID10. I do, and it works. in your case, you don't even need separate /boot

---

### Post by klavmanian on 2011-05-11
I'll take a look at putting the /boot on a RAID 1. However, last night I successfully installed Debian Server 6.0.1a in RAID 10, where the "/" (everything including "/boot") was on the raid/lvm. GRUB still hangs for some unknown amount of time and *sometimes* boots. So, this is not my final configuration but it's a start.

I'll give the 'RAID 1 for /boot and RAID 10 for all else' a try later today.

[QUOTE=a2j]you should be able to have /boot on RAID10. I do, and it works. in your case, you don't even need separate /boot[/QUOTE]

a2j, might I ask if you did anything special in your GRUB configuration (or what OS version you have this working in)? I assumed you could have /boot on RAID 10. However, I got an error where GRUB would not install to /dev/mapper (this was the default location using alternate 11.04 installer).

As mentioned, I have this *sorta* working in Debian 6.0.1a, but I like Ubuntu Server much better for my purposes/experiences.

---

### Post by a2j on 2011-05-11
I did not do anything special with grub, it just works in Ubuntu 10.04/10 and 11.04

I have /boot on RAID10 and / on RAID0 on my laptop. On one of my servers, / on RAID10. And another server with / on RAID10 and /RAID on RAID5.

never had a single issue.

grub writes mbrs to all drives in RAID10 array. iirc

I just let the install do the work.

---

### Post by NadirPoint on 2011-05-17
> **a2j said:**
> I just let the install do the work.
Or, you could install the OS on an old, slow, small IDE drive all by itself to "keep it simple," keep your fingers crossed it doesn't fail, which by definition it is poised to do, and which also by definition, various levels of RAID technology are designed to mitigate the effects of.

---

### Post by dancho on 2011-07-11
In case you decide to go with RAID10 instead of RAID5, I have these guides that I've written. You don't really need a non-RAIDed OS drive which is separate from the RAID array, I would have the OS raided as well for reliability.


Here is a guide on how to convert a running Ubuntu installation to RAID1/RAID10 will help:

[http://iiordanov.blogspot.com/2011/04/how-to-convert-your-single-drive-linux.html](http://iiordanov.blogspot.com/2011/04/how-to-convert-your-single-drive-linux.html)

If you choose to do a fresh install, you can try this guide for making a fresh installation on RAID10/RAID1:

[http://iiordanov.blogspot.com/2011/07/how-to-install-linux-ubuntu-debian-etc.html](http://iiordanov.blogspot.com/2011/07/how-to-install-linux-ubuntu-debian-etc.html)

---

