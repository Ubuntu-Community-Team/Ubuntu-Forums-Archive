---
title: "Riad Cards that work with Linux"
date: 2009-04-22
forum: Server Platforms
---

### Post by Dragonbite on 2009-04-22
I am setting up a home Ubuntu Server (8.04) and am thinking of getting a RAID card and 2 hard drives. The server is actually a Dell Dimension 4600 desktop I want to set up as a server.

Home isn't a big operation but I like the idea of redundant hard disk for the data and using the Hardware to RAID them instead of software.

Is there any particular manufacturer which works well with Linux and any manufacturers that DON'T play nice with Linux?

What features/specs should I look for in a RAID card and how do I use it?  

I use Ubuntu desktop fine, but this is my beginning into Servers (Ubuntu Server specifically, CentOS is my second choice).  I have a very basic server running now but it has 1 hard drive for the OS and a 2nd hard drive for my Samba share files.

---

### Post by andrewc6l on 2009-04-22
My experiences with HighPoint RocketRaid cards have been less than satisfactory. They offer binaries and source, but their source doesn't compile, and the binaries for my card were only for some older versions of RedHat FC4 :-(

---

### Post by wkulecz on 2009-04-23
I think software RAID is fine for a home server.  I've 6.06 set up with RAID 1 for the system and four drives in a RAID 5 for data.  Its worked very well and been basically trouble free other than a change in the /dev/md ordering after one of the early updates.

I don't think you can use anything other than RAID 1 on the boot disk, because of grub issues.

Most important thing to remember is RAID is not backup!  You still need a good backup schedule and proceedure.

I do nightly backups to an external drive that is as large as the array uisng rsync.  Once every couple of months I use rsync using  --delete to purge files that have been deleted on the RAID from the backup drive.

--wally.

---

