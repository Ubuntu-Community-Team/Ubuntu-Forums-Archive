---
title: "Move Ubuntu 14.04 server to another box - any pitfalls?"
date: 2016-06-20
forum: Server Platforms
---

### Post by vonner2 on 2016-06-20
Hi there
New to the forum, and have had a search for any threads about this matter.

I've been running ubuntu 14.04 server on a small AMD x2 minitower, with 8GB of RAM.  I'd like to get it one something beefier, so I've got a 16GB Xeon arriving in the post.

The last time I did a complete hardware upgrade was on Mandriva about 5 years ago.  I simply swopped the drive over to a new PC and booted up. From what I remember it was pretty easy, so I'd like to do the same thing again.  

I will be moving 3 physical drives over, all SATA.  A 500GB with / and /home, plus two 1TB drives mounted as /galaxy and /nebula.  The motherboard will be completely different, the graphics card will move from an onboard Nvidia to a PCI-E AMD, but since I run the whole thing headless I hope this won't be a concern.

I will of course plug in keyboard/mouse/monitor after the migration, Can anyone advise me of any pitfalls I may encounter?  The network card is set to a static address, not DHCP so the MAC address shouldn't matter, but will I have to redetect the new NIC?

I'm also prepared for the two 1TB drives to mount the wrong way round, but I can sort that out.  

As far as skills go, I'm confident in a terminal and have no problem with command-prompt utilities.

Cheers

Dave

EDIT: Forgot to mention. Both old and new systems are x64, so no change of architecture

---

### Post by howefield on 2016-06-20
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by LHammonds on 2016-06-20
If it were me, I'd do an fsarchive of my partitions and restore them on the new server just to ensure there are no issues or at least give me time to research and document what needs to be done before doing the actual move.

If unfamiliar with backing up and restoring partitions, I have a section dedicated to that on my Ubuntu Server link in my signature.

---

### Post by vonner2 on 2016-06-20
Unfortunately LHammonds, I don't have any other spare space anywhere to backup 500GB's worth of the boot drive to.  Thanks for the info though.  Also, all it would do is enable me to get my data back if moving the drive over didn't work.  It would still leave me in the situation where I don't know if a straight drive move is possible or not.

There's not a huge amount of customisation in the installation, and to be honest I could flatten /, keep /home and reinstall totally from scratch (I've built three ubuntu servers over the last few months so it's a walk in the park).  I'd just rather not if I didn't have to.

---

### Post by LHammonds on 2016-06-20
I wasn't sure if you had drives you could test with.  My thoughts were to backup your current system and restore them to the new system (with different drives) and see if it worked.  If it booted just fine or if you had problems and could correct them, you would have the confidence of moving the original drives over without problems with the new hardware AND you'd have a backup set. ;-)

Still, I'd recommend having a backup before doing anything though.  At least get a 1 or 2TB external USB drive and fsarchive your partitions to that.

LHammonds

---

### Post by vonner2 on 2016-06-24
Hi LHammonds.  Yes, I can do all that (If I buy an external drive to do it to), but my original question remains.

What potential pitfalls could I encounter swapping drives?  I'm already prepared for the two storage drives to be mounted the wrong way round, but that's simply a case of editing fstab. However will my new network card be automatically detected and assigned to dhcp?  If so, then again easy to edit network settings and get it back onto the same IP.  Or will I have to redetect it manually?

EDIT: Scrub that, I went ahead and did it anyway.  Network card no longer worked, but I deleted the file **/etc/udev/rules.d/70-persistent-net.rules **and rebooted. Found the new card as eth0 and assigned it the same IP.  Everything else works fine (and faster now).  Good old linux.

---

