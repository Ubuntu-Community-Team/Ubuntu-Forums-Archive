---
title: "RAID 1 on 2-3 additional drives"
date: 2011-06-18
forum: Server Platforms
---

### Post by khaffner on 2011-06-18
I'm planning on building a file server. I want do have one decent SSD as a system drive. And in addition to that, 2 or 3 4TB drives(as soon as it hits the market) in a RAID 1 configuration for safety and speed.
I'm probably gonna use [this motherboard]("http://www.asus.com/Motherboards/Intel_Socket_1155/P8H67M_LE/#overview"), in case that matters. 

I have browsed this forum and googled a bit, and all the guides I've found is about installing Ubuntu on a RAID configuration. I want Ubuntu on a single SSD, and _afterwards_ add a couple of disks for RAID 1. I figure my needs are so simple, it can't be more than a few clicks in the BIOS. 

How do i do this?

---

### Post by MrEgg on 2011-06-18
Hi,

I have a configuration pretty similar to what your contemplating : P8H67, ubuntu on SSD, and my /home on 2 drives on raid0. As a side note, I installed Ubuntu 10.10 because I set up my system in Feb. '11 (Natty wasn't available at the time), and I never bothered to upgrade since then because I don't like Unity.

Because we're talking Sandy Bridge here, I installed 10.10 using the Alternate CD on the SSD (/dev/sda) using the whole drive (no separate partition for /home). Then I manually upgraded the kernel. If you choose to install 11.04, it may work out of the box using the conventional iso (this mainly depends on the default kernel version shipped with it).


Once installed, I went to Disk Utility (found under System - Administration). There, I went File - Create - Raid Array, and selected my 2 additional drives (sdb and sdc) and chose raid type 0. You'd opt for type 1.

Then I copied /home (at the time on the SSD, sda) to the root of the raid array. Then I modified fstab to mount the raid as /home. No big deal here.

It may sound complicated as you read my message, but it's pretty easy, really.

I'm subscribing to the thread in case you need additional help.

Cheers,
Egg

---

### Post by khaffner on 2011-06-18
That actually seems as easy as i hoped it would be! Thanks!

---

### Post by YesWeCan on 2011-06-18
If you are using 10.10 one "gotcha" that should be mentioned is that mdadm metadata v0.90 will malfunction if any drives are larger than 2TB. It may malfunction is a way that isn't obvious at first (a bug report has been filed!). According to the man page mdadm still defaults to 0.90!

So when creating the array from command line use the --metadata=1.2 directive. I am not sure how to specify this in Disk Utility - I have never tried. In addition to coping with disks and partitions bigger than 2TB, v1.2 puts the metadata (aka superblock) far enough from the start of the disk that it should not interfere with the disks GPT.

---

### Post by khaffner on 2011-06-19
I see. We'll cross that bridge when we come to it.

But how can i expect the performance to be? I predict the first 4TB Drives will run at 5400RPM. With two of those in RAID 1, what would the file transfer rate be? Approximately of course ;)

---

### Post by a2j on 2011-06-20
file server with gui? 

I'm getting 50-70MB/s over the network speeds to my RAID10  2 drives, 5400rpm. I hope that will change once I get two more drives in.

---

### Post by khaffner on 2011-06-20
The server is going to do more than just share files, but that is what I will begin with.
 
But I might go for 2x2TB in RAID 0, and then a 4TB drive for backup. Any comments on that?

---

### Post by psusi on 2011-06-20
Why the SSD?  Once the server is booted up, it isn't going to touch it again assuming the files it is serving are stored on the big drives.

It is possible to set up a 3 disk mirror, but why bother?  Do you really think you're ever going to have 2 out of the 3 drives fail at the same time?  Also remember, the purpose of raid is to maintain high uptime in the event of a failure; it is not a substitute for backup.

---

### Post by khaffner on 2011-06-20
> **psusi said:**
> Why the SSD?  Once the server is booted up, it isn't going to touch it again assuming the files it is serving are stored on the big drives.

I'm thinking "why not?". This server is going to do more than share files in the long run, I don't want to pinch the pennys that hard ;) Unless you find an argument against SSD besides price, I will buy a SSD.

> **psusi said:**
> 
It is possible to set up a 3 disk mirror, but why bother?  Do you really think you're ever going to have 2 out of the 3 drives fail at the same time?  Also remember, the purpose of raid is to maintain high uptime in the event of a failure; it is not a substitute for backup.
Look at post #7

---

### Post by YesWeCan on 2011-06-20
> **khaffner said:**
> But I might go for 2x2TB in RAID 0, and then a 4TB drive for backup. Any comments on that?
With RAID0 + backup,
+ you have a backup so if you accidentally delete a file you still have a copy, until the next backup.
- system performance suffers while the backup is taking place
- if there is a disk failure your system is going to be unusable for some time while you manually rebuild it.

With RAID10,
+ your system is uninterrupted if a disk fails and rebuild requires minimal intervention.
- you have no backup in case you accidentally delete something

---

### Post by psusi on 2011-06-20
The reason why not is that the money could be better spent elsewhere, such as on more ram, or larger/faster hard disks.  An SSD is certainly a nice thing in a desktop or laptop, but for the kind of server you describe, it will add nothing.

---

### Post by MrEgg on 2011-06-21
You'll find below the performance tests on my SSD (Crucial C300 - the new M4 is even better), as well as on my raid0 (composed of 2 x Samsung HD502HJ). The SSD is Sata III, the Samsungs are Sata II.

[[img]http://s4.postimage.org/2rk2zgwro/Performance_Crucial_SSD.jpg[/img]](http://postimage.org/image/2rk2zgwro/)
[[img]http://s4.postimage.org/2rkrsj46c/Performance_Raid0.jpg[/img]](http://postimage.org/image/2rkrsj46c/)

---

### Post by psusi on 2011-06-21
> **MrEgg said:**
> You'll find below the performance tests on my SSD (Crucial C300 - the new M4 is even better), as well as on my raid0 (composed of 2 x Samsung HD502HJ). The SSD is Sata III, the Samsungs are Sata II.

[[img]http://s4.postimage.org/2rk2zgwro/Performance_Crucial_SSD.jpg[/img]](http://postimage.org/image/2rk2zgwro/)
[[img]http://s4.postimage.org/2rkrsj46c/Performance_Raid0.jpg[/img]](http://postimage.org/image/2rkrsj46c/)

Just sharing for the heck of it or was there a point?

---

