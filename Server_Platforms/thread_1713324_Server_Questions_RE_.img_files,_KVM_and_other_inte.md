---
title: "Server Questions RE .img files, KVM and other interesting tidbits"
date: 2011-03-23
forum: Server Platforms
---

### Post by YogiPaolo on 2011-03-23
I'm not sure where to put this post.
I just have a few questions/ideas/musings about system that I'm building. It would be great to hear your impressions/ideas/comments. 

The purpose of this system is for daily use and learning. Under the heading of daily use, I have a mythbuntu-based media PC connected to a 40-class inch plasma. This is used for entertainment and some daily surfing.

Then I have a new supermicro atom-based NAS(SAN?) with 4.5 TB of storage (Linux raid 5). I just got this box up and running with two LACP-bonded 1Gigabit nics. Running this little LAN is an HP Procurve1800 Gigabit switch. 

I plan to build a small virtualization box using Linux KVM. This box will be based on an AMD 6100 series chip and a supermicro mobo. The plan is to have a raid 1 array of 1 or 2TB for storing the disk images. The little SAN box will be used as ISCI target for attaching storage media to the virtual machines. I may also use the SAN to hold actual VM drives.

The VM box will be used as a computer lab in preparation for MS (gasp!) certification exams. The long range goal is also set up a lab that I can use to prepare for the Certified Ethical Hacker exam as well. Right now, I just want to get the thing built (building a budget for that now...)

So far, my question concerns the SAN. I'm playing around with creating the iscsi target(s) following the instructions at the links below:

[http://www.unix-tutorials.com/go.php?id=4547](http://www.unix-tutorials.com/go.php?id=4547)
[http://www.cuddletech.com/articles/iscsi/ar01s04.html](http://www.cuddletech.com/articles/iscsi/ar01s04.html)
[http://linux-redhat.net/Sams-Red.Hat.Linux.Fedora.3.Unleashed/0672327082/ch10lev1sec8.html](http://linux-redhat.net/Sams-Red.Hat.Linux.Fedora.3.Unleashed/0672327082/ch10lev1sec8.html)

It's intriguing to me that one can use .img files as block devices and mount them using LVM. 

Specifically, I wonder about using files as hard drives.

Does this generally make the system more or less robust?
How reliable are file-based hard drives?
What about alignment issues with the .img files and the filesystem? (It was intense to create a properly aligned raid array using Caviar green drives w/ 4k sectors)
Given the fact that the .img files are a filesystem within a filesystem , does this layer of abstraction create a more or a less reliable system?

I can see the power in terms of flexibility - .img files can be migrated and/or backed up to another machine on the fly OR incrementally copied to another system for failover. 

At this point, I'm going to use .img-based volumes because I find it cool. It would be great to get more practical viewpoints. 

I'll update the thread when I get moving on the KVM box. That's an exciting prospect as well.

---

