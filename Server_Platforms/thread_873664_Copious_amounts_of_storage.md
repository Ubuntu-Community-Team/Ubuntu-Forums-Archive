---
title: "Copious amounts of storage"
date: 2008-07-29
forum: Server Platforms
---

### Post by cravenc on 2008-07-29
Hello,

I don't have any plans yet but thought I'd see how much work this would take.  At some point I would like to offer some services off of my ubuntu server (or several in a cluster if it comes to that) and I was wondering if there is a way to universally store information.

For instance, could I have all my MySQL DBs and web files stored on a networked hard drive and then point the cluster's servers at that?  

I'm a bit undereducated.... Is there a way to string several hard drives together to make an uber large one?  I guess I just want to learn the basics of creating a datacenter with clusters.

Thanks

---

### Post by Cadmus on 2008-07-29
I've been looking into something similar, I too am inexperienced (so don't take me at face vaule :) ) and this is what I have so far.

LVM (Logical Volume Manager) is a program that lets you combine HD partitions into one larger partition that you can then mount like any other hard drive.

Something you could use with LVM is iSCSI, this allows you to use storage space on a specialised device (or another computer with software like OpenFiler) as though it was a local HD. So you could combine several iSCSI targets and then use LVM to make them one big super-partition.

What I'm still not too clear on is how you replicate data between different servers and keep it concurrent, as obviously having just one huge server creates a single point of failure.

---

### Post by cravenc on 2008-07-29
Right.  I didn't think about having a single point of failure with the file system.  There is a ton of variables to think about here.

I'm thinking that one could have a master cluster, which would serve most of the time, and then a few slaves with their own separate network shares(on separate machines).  Then do something like a replication or something with the web app's code to make sure all the systems are up to date.  Probably could even have something within the web app's code to use a slave DB instead of the master if it's overloaded or down for whatever reason.

---

### Post by Cadmus on 2008-07-29
Hmmm, it doesn't see as though there is a brilliant file replication solution. At the moment the best candidate seems to be using a kernel module called 'inotify' which monitors changes to files, one could (in theory) use this to ensure that changes are propagated between replicas.

---

### Post by Cadmus on 2008-07-29
There seems to be a promising program reaching maturity called tsync which can synchronise files across dodgy links and so forth. Still looking at how it handles conflicts, but so far the only thing it doesn't claim to handle well are files in a state of constant flux (like logs on a busy server).

---

### Post by redraiderbum on 2008-07-29
If you just want to string together numerous hard drives you could try just using mdadm to raid the drives together.  A raid 5 will give you the possibility of losing a single disk without any loss of data.  I have 9 500 GB hard drives put together in a software raid 5 which ends up giving me approximately a 3.6 TB volume.  Here's a link for a quick setup.

[http://www.howinthetech.com/quick-and-dirty-linux-software-raid5/](http://www.howinthetech.com/quick-and-dirty-linux-software-raid5/)

With mdadm you can also expand an array that is already online or if the system crashes it can assemble the array in another system without losing data.

If you want to mirror data across multiple systems concurrently, you could try something like Unison or even rsync.  You would setup one system as a server and the other as the client and have them to check their file system differences every so often.  I'm not sure this is what you're looking for.

If you want to have a single instance storage situation, you could try something like having a single nas or san storage server (freenas, for example) that has one or multiple iscsi targets.  Your other server or servers would then be set up as iscsi initiators.  The initiator will mount the remote iscsi target as a local volume and use it as if it were local.  It is a really good way to run a fast san over a regular ethernet network, as opposed to using some crazy expensive solution like fibre channel.

---

### Post by Cadmus on 2008-07-30
> **redraiderbum said:**
> If you want to mirror data across multiple systems concurrently, you could try something like Unison or even rsync.

Isn't the problem with Unison and rsync they have to be set up as scheduled cron jobs to keep things up to date? Wouldn't this cause a problem if you have a very large number of files? I'm thinking of something like a Medical Imaging Directory, thousands of files in the multi-megabyte range.

---

### Post by Cadmus on 2008-07-30
Hmm, tsync hasn't had any changes made to it since about 2006 from what I can see. However a bit of rooting round has found a cluster based file system called GlusterFS which might have what we're looking for. The only concern I have right now is that it' only really happy over Gigabit Ethernet, which would be rather expensive between sites.

---

### Post by fjgaude on 2008-07-30
> **Cadmus said:**
> Isn't the problem with Unison and rsync they have to be set up as scheduled cron jobs to keep things up to date? Wouldn't this cause a problem if you have a very large number of files? I'm thinking of something like a Medical Imaging Directory, thousands of files in the multi-megabyte range.

Both Unison and rsync would require cron, but once the first copy is made only changed are then copied... so the whole database is re-copied. Only changes to files get copied over.

---

### Post by redraiderbum on 2008-08-02
Sorry for taking so long to respond.  Fjgaude is correct.  The first backup may take a lot of resources, but each additional backup is simply incremental so only the new files are transferred.  Also, yes you would need to setup a cron job for automation purposes.  

As an example, on my 3.6 TB array I have about 1500 ripped movies at about 1 GB apiece, 600 TV show episodes at about 300 MB apiece, and 40,000 songs at about 5 MB apiece.  I use rsync to backup the the music and as much as I have room for of the rest on another ubuntu box for fear.  It works perfectly.  I don't set it up as a cron because the two computers are not always on the same network together.

---

### Post by windependence on 2008-08-02
I would definitely NOT recommend software RAID for this.

You need a RAID cabinet and a good hardware RAID card <flame suit ON>

If you are going to be selling services and using as you say (I love it) COPIOS amounts of storage, then you should be using a RAID cabinet that can hold 12 or 18 drives, and RAID 5 or 6. You will get MUCH better transfer speed that way.

My $.02

-Tim

---

### Post by redraiderbum on 2008-08-02
I agree with windependence if the original poster meant services as in selling services.  I was thinking he meant home lan services... for instance, a samba service, a CUPS service, web-based torrent client, etc.  For a home lan, a hardware raid seems a little over kill because the card may cost as much as the hardware (other than the HDD's) to run a good Ubuntu software raid.  This is particular true if you're planning on always running the same OS on that box.  

It is true a software raid is probably not the best solution for an ISP.

---

### Post by windependence on 2008-08-02
You might be surprised. If you are talking SCSI RAID then yes I would agree it's expensive. As a reseller I am showing 58 cards under $100 for SATA RAID.

-Tim

---

### Post by redraiderbum on 2008-08-02
You have 53 raid cards that have 8 or 12 sata connectors for under $100?  That's amazing!  Newegg shows one with 8 sata II connectors for under $100.  

There are a bunch of 4 and 2 connector cards, but a lot of those are the silicon image cards that are actually software raid and unload all of the processing on the primary cpu.  Those shouldn't have any performance advantage over mdadm.

---

### Post by windependence on 2008-08-02
Above 4 gets more expensive, but is doable for RAID5. With the size of drives today, 4 would be usable, but of course more spindles = more speed.

In my case I have a 4U server case with just a PS in it and a whole bunch of removable SATA drive cages. It holds 1.5 terabytes of RAID5 space. That's a lot of space. You can of course buy something like IcyDock for a more independent solution.

As an alternative, I also run a 12 drive SCSI cabinet I bought used $50 with a Dell Perc3 card in the servers $60 each. Works great. eBay is your friend.

-Tim

---

### Post by redraiderbum on 2008-08-02
True 1.5 TB's is a lot, but it's just not enough for me.  I needed no less than 2.5 TB's to hold my whole media library.  Also with the introduction of mdadm you have all of the tools you need in a light weight package.  Running a rack with separate units that only holds drives is more expandable and faster in most configurations, but then I would have had to buy a rack that is $500.  

As is, I spent $310 building my system then bought 9, 500 GB sata II drives for $85 apiece.  It made a 3.64 TB raid 5 cost less than $1100.  It was hard for me to beat a little more than 3 GB/dollar for the whole system.  And it is rackmountable for the future.

---

