---
title: "Migrating to new server hardware."
date: 2008-07-12
forum: Server Platforms
---

### Post by RHAnthony on 2008-07-12
So my situation is that I have several home brew websites running off of my own server in my living room.  Being that I built the thing nearly 10 years ago, it's about time some fans and hardware start to give way (I think I got a pretty good life span out of it!).  So now I'm going to replace it with a Dell desktop I have laying around doing nothing, which is about 30x faster than my old 1u anyway.

My goal is to migrate over Apache2, MySQL, Postfix, Bind, PHP, Wordpress, and Gallery2, along with all of the databases and content of the sites. 

I've read quite a few tutorials about ways to do this, and have tried a few things with each program but nothing seems to go over and want to work.

The Dell has a new install of 7.10 (matches the 1u), and I've installed all of the software packages.  I've tried a few tools for migrating MySQL which is my biggest concern, and nothing produces a working copy of my db's on the dell.

As for the others, I've even had it suggested to me to just scp the entire /etc from the 1u to the Dell, and I gave it a shot since it wouldn't hurt the live machine at all.  But yes, it did really bork up the Dell to the point of me just running the install CD again.

I guess what I want to know after all of this, is if there is a magic "move everything from one box to another" program out there that I have somehow missed?  Or can someone at least recommend some good tools for migrating MySQL safely, and the other app configs easily?

Secondly I plan on upgrading the Dell to 8.04 AFTER all of the migration is done, and before I put it online as the main server (testing all sites and apps under 8.04 prior).  Could I just upgrade it before the migration? or is that jumping the gun, as I think it would be?

---

### Post by RHAnthony on 2008-07-12
:bump:

---

### Post by Thirtysixway on 2008-07-13
You may just need to copy the configs and files over to the new system.  It's also possible to just put the hold harddrive into the new machine but that old hardware could fail...

---

### Post by tamoneya on 2008-07-13
I dont know of any magic tools but I would copy the relevant directories of /etc like /etc/apache2.  Also I would highly recommend that you upgrade before you migrate.  This way if anything goes wrong with the upgrade you dont have to migrate twice.  I would recommend not just moving the drive since like the other poster suggested it is probably going to fail shortly.  Also the other reason I wouldnt do it is I would keep the 1U 100% intact for a month or so after the migration.  That way if anything goes south you have it to refer back to.

Please wait 24 hours before bumping a post.

---

### Post by RHAnthony on 2008-07-13
First off, bump advice noted.

secondly, there is very little fear of the hard drives failing as the data drive (250gb) is fairly new, and the system drive (40gb) doesnt have all THAT much time on it (not original to the system, but old still).  The plan has been to move the data drive, which contains the web content on it over to the new hardware after it's configured to read from the pre-determined mount point.  It's the stuff on the system drive (/etc, etc.) that I am wrestling with.  The hardware that is failing are fans, PSU, RAM, and mobo ports (which are a big worry, as the whole mobo can't be too far behind).

I'm not sure if I want to jump up to 8.04 first, worrying that some of the apps will not take the 7.10 configs correctly.  Or is this an irrational fear?

Whatever I do, I'm going to document each step to get it working and hopefully be able to build some kind of script to at least automate a big chunk of this for when it all moves off of this Dell (temp solution) onto my new 4u thats being built in a few months.  fingers crossed tight as ever that it helps/works.

---

### Post by mistypotato on 2009-12-27
Wish you had followed through with this :KS

---

### Post by Vegan on 2009-12-27
I am using 9.10 and when I moved from a smaller disk, I first setup the system with the software stack I use.

Then I extracted from a previous tarball all of the files needed and poof, I was in business.

I use tar to backup everything and then move that to another machine so that I have 2 copies in case a machine does down.

---

### Post by jocampo on 2009-12-28
If your concern is hardware and what you really want to do is to preserve and migrate is data, have you considered "dd" utility? I'm assuming you have network so could be possible dump that to new server or a blank/new partition.

Once you move your old data to new disk and hardware, you can start thinking on any Os upgrade.

Just my 2 cents

---

### Post by almostalive2009 on 2009-12-28
ubuntu kung-fu (a book) says you can use ddrescue to clone any disk and put on another disk. If your hard drives are new enough I dont see why you cant just swap em over

---

