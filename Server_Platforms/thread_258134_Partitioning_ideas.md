---
title: "Partitioning ideas???"
date: 2006-09-15
forum: Server Platforms
---

### Post by charles.g.moore on 2006-09-15
I'm kicking around the idea of setting up a little lab in my house and wanted a web server to start...
I know NOTHING about servers but wanted to do some light admin, maybe a simple web page and see if I could access it and stuff...
I plan to install ubuntu server onto a 30gig P2 400Mhz system

My question is does anyone know of some special partitioning requirements or tricks before I install to make the HDD more administratively friendly?
Im assuming ill need more than 2 partitions.
If anyone could point me to a how-to or if you know some ballpark numbers of how large and which partitions I should make it would be greatly appreciated...

---

### Post by bluefrog on 2006-09-25
to begin with a web server in your house, just let the autopartitioning tool do its job.

When you are more familiar with Linux, google a bit regarding partitioning.

James

---

### Post by Elrohir on 2006-09-25
you could just use the default partitioning given by Ubuntu or you could use this:

30GB HDA

SWAP (depends on RAM, but RAM + SWAP should be 1.5 GB)
/var/www (or /web, this is where you place your files to publish) -> 512 MB
/ (root filesystem) -> 28 GB

this should use the entire disk...
when installing Apache (the web server), you should create an alias file for pointing out to where the files are... if you use /var/www you should do nothing, but if you put the files somewhere else, follow the steps mentioned [here]("http://tinyurl.com/elqag")

Cheers...

---

### Post by Child of Wonder on 2006-09-25
Here's how I have a production web server set up.

Swap - Make this at least double your RAM.  1GB would be ideal (although you'll never need that much)

/home - 10GB
Every webpage can simply be put inside the home directory of the user who admins it.  Simply have each Virtual Host point to a folder in the user's home directory.

For example, say you eventually have 3 websites on your server and you have two users who control them.  This is a great way to limit access to the webpage roots and make sure they don't fill up your hard drive and you can set up quotas for that partition for each user.

Eventually you'll have /home/user1/webpage1, /home/user1/webpage2, /home/user2/webpage1, etc.  When users FTP into your box they can be limited to their home directory only and still get to their web page folders.

/ - Remaining space.

---

### Post by Macchi on 2006-09-25
Warning: I don't want to complicate things too much, but this is my
present partitioning solution for a Ubuntu server. I have designed 
it for increased reliability and to facilite recovering the system
and most information in case my wild experiments would destroy the 
running system.
 
Here is my partitoning scheme:

mount point | filesystem | ~ Size | Explanation
----------------------------------------------------------------------
/boot         ext2         128MB    facilitates to boot multiple OS
/             ext3         6GB      root file system
(hidden)      ext3         6GB      hidden copy #1 of the /
/home         ext3         20GB     easier backup with separate /home
/home2        reiserfs     200GB    "bulk" storage

Remarks:
1) Different / partitions allow keeping one active copy and one standby copy of the whole system. The fallback copy can be activated simply by rebooting the system and choosing the right partiton on grub. 
Later you can copy the stable version back to the active partition, and then adjust /etc/fstab and grub/menu.lst on /boot. Finaly reboot the system again to go back to a stable ground. 

2) A separate /boot partition facilitates booting from multiple / partitions or multiple server operating systems.

3) The reserve partition with a copy of the stable system is not mounted in order to reduce risks. 

4) The /boot/grub/menu.lst and /etc/fstab have to be adjusted manually upon every update or system recovery. This could be later arranged by a script.

5) Actually I keep the root file system an /home on a software RAID 1 distributed on two harddisks for increased reliability.

6) The extra /home2 partition is used for storing media, music, videos, and also snapshots of /home and /etc. It can assigned to a separate (third) harddisk, that could be moved to another machine in case of serious trouble. The ReiserFS facilitates efficient  storage of a large number of small files.

7) I keep websites (different virtual hosts) on /home as a separate user so that they are kept on RAID and get regular backups.

Hope this wasn't too confusing.

---

