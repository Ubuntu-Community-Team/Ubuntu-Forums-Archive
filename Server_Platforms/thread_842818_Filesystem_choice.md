---
title: "Filesystem choice"
date: 2008-06-27
forum: Server Platforms
---

### Post by maartenlameris on 2008-06-27
In a few day's I get my new fileserver witch gives me a mind blowing 9TB disk space in a hardware raid5 (10X1TB)
The controller (a Dell PERC6E) will be capable of online raid extension and will go with a maximum of 45 disks well over any
16TB limit.
The challenge is that I want a stable and reliable filesystem witch is capable to grow with the array up to at least 30TB

The system I'm gonna use will run a custom 64bit 2.6.25 or 2.6.26 kernel (depends on when 2.6.26 is ready)
Is filled with files for 99.9% over 100MB and up to about 40GB
The array will use a GPT partition table as the partition will be way over 2TB

I have done some research and found 3 ext3, ext4, xfs, reiserfs
according to [http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)
ext3 as a 32TB limit but the ext3 wiki says's 16TB witch just won't be enough, on the other hand it's proven tech has the ability to grow and performs reasonably well.

ext4 has a limit of 4EB according to wikipedia but it's still under development and i can't seem to find out if i can grow it.

and then there is XFS witch can do 8EB and growing partitions.
but I've never used it and have no idea about its stability and how robust it is although xfs should give the best performance with big files.

Reiserfs (3.6) will reiser 4 ever be final and stable with Reiser himself in jail?
no support for volumes over 16TB but does support growing a volume.

I will have some time to test (about 5 day's) but it would be nice to have that left for who knows what.
The files on this server are not mission critical but it is to much to backup and its really necessary to grow the filesystem reasonable save.

Any suggestions?

---

### Post by windependence on 2008-06-27
I have not had good luck with reiserfs, and remenber this - when there is a disaster, are you gonna be able to recover, and is there going to be information out there to help you. Many people use "exotic" file systems and I just think they are playing with fire. EXT3 would be my choice because is is proven and ubiquitus. People are gonna tell you it's slow bla bla bla, but if you configure it correctly this won't be the case. You already have a non-standard installation with a custom kernel so recovery is already going to be harder than normal. Make GOOD backups and verify them.

-Tim

---

### Post by maartenlameris on 2008-06-27
As I stated before a backup is out of the question the 9TB i start with is just to much and way to expensive to backup.

besides that ext3 has a 30% penalty in performance when barriers are enabled (i just figured that out) witch is a lot!

choices choices choices.

---

### Post by Chayak on 2008-06-28
That's a nice piece of hardware.  I'd say XFS just because it's very robust and proven in the storage area.

Reiserfs is great for small files but not so great with large ones.

The hardware becomes a single point of failure though.  I've seen quite a few setups like that and have a 20 disk netapp in the lab where I work.  We also have a redhat GFS setup that backs up important data to the netapp.

I've been in the security and IT arena for a while and Mr. Murphy is a constant.  I do my best to avoid single points of failure when it comes to servers and especially storage.

---

