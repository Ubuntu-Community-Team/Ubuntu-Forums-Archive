---
title: "Best backup system for small network"
date: 2011-12-31
forum: Server Platforms
---

### Post by lykwydchykyn on 2011-12-31
I have a small network at home of 5 (sometimes more) workstations running various *buntus (a couple dual-boot to winXP) plus a server running Debian stable.  Since we seem to have a lot of trouble with hard drives lately, I bought a 2TB drive to put on the server and want to set up regular automated backups.

I'm trying to decide which system to use; I'm not afraid of config files or command lines, but I want to get the system running without having to read a Tolstoy-sized manual.

I tried bacula since I have a webmin module for it, but it looks confusing and the Debian defaults apparently don't work with the webmin defaults.

Anyone have suggestions?

tl;dr -- need a reasonably simple centralized backup system for a home network of 5 linux machines.

---

### Post by Lars Noodén on 2011-12-31
My standard reply for this kind of activity is always rsync over SSH.  It can even do incremental backups:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

If you use sudo and SSH keys the backup can be automated.

---

### Post by lykwydchykyn on 2011-12-31
I know rsync pretty well, and we already have ssh keys set up for my accounts anyway, but frankly I was hoping for something a little more packaged.

---

### Post by Lars Noodén on 2011-12-31
With sudo you can get by with one rsync session per machine.  That's about as pre-packaged as you can get.

---

### Post by lykwydchykyn on 2011-12-31
> **Lars Noodén said:**
> With sudo you can get by with one rsync session per machine.  That's about as pre-packaged as you can get.

No offense, but this solution is really not what I'm looking for.  I appreciate your perspective and desire to help, but if all I wanted was a bunch of rsync scripts I'd have just done that.

I was hoping to get perspectives on systems like bacula, afbackup, backupninja, etc.

Thanks.

---

### Post by Derek Karpinski on 2012-01-01
What about Deja-Dup?  That's about as packaged as you can get.

Edit: Is your server headless?  I don't know how well Deja-Dup operates via command line.

---

### Post by Lars Noodén on 2012-01-01
> **lykwydchykyn said:**
> I was hoping to get perspectives on systems like bacula, afbackup, backupninja, etc.


Which specific features and capabilities did you have in mind?

---

### Post by Paddy Landau on 2012-01-01
It looks as though, contrary to what you said in your first post, you aren't after command line solutions such as rsync or rdiff-backup (although they are easy to use -- I use rdiff-backup).

What about a commercial solution, such as [SpiderOak]("https://spideroak.com/") (which I also use)? It is cross-platform; you can use a single account for all your machines; it does intelligent de-duplication and incremental backup; and it supports synchronising and file-sharing should you choose. The first 2Gb are free, and extra space is cheap.

---

### Post by TwiceOver on 2012-01-01
Look into BackupPC or better yet, Crashplan both are free.

---

### Post by rsvancara on 2012-01-01
Bacula may be a little overkill, but supports windows clients as well.

One thing I like about bacula is that it is client server based and supports both tapes and file based storage platforms.  It can use a MySQL, SQLite, or PostgreSQL backend to track files, jobs, and media.  It has a command line interface as well as several gui front ends.  

I am using bacula at home to backup of my file server, database server, and workstations to a 4TB external storage array running on BTRFS.  Why BTRFS, because it supports internal check sums and hopefully that will tell me when I have a bad block.

---

### Post by Entilza on 2012-01-02
> **TwiceOver said:**
> Look into BackupPC or better yet, Crashplan both are free.

I've been using BackupPC with great success.  I like the incremental version and restoring features, all web based.

It takes a little bit to configure but once setup is solid.

---

### Post by Habitual on 2012-01-02
> **lykwydchykyn said:**
> No offense, but this solution is really not what I'm looking for.  I appreciate your perspective and desire to help, but if all I wanted was a bunch of rsync scripts I'd have just done that.

I was hoping to get perspectives on systems like bacula, afbackup, backupninja, etc.

Thanks.

If I may toss out my 2 cents worth here.
I admin about a dozen AWS Instances and about 50 Applogic Servers. 
My current setup is an Applogic CentOS5 bacula host with a fuse-mounted s3 bit bucket as our bacula backups. (fuse://s3-bucket/)

bacula is very hands on at first, but once you have the understanding of the bacula-dir.conf directives, then you only have to customize like 4 or 5 Templated fields and off you go!.
Client installation is very easy.

<end_Light_and_Fluffy>

It relies on a MySQL db and the .bsr files are a *Proprietary Format.*
The package-manager installed versions on my Ubuntu host and the CentOS host were different enough that I had to make adjustments.

So, In a worse-case scenario (on the bacula server), one would have to restore the fuse://s3-bucket/ mount point, bacula software, AND the bacula mysql db via flat file and THEN be able to restore (which REQUIRES the .BSRs)
(Personally, I have a hard time with any backup that relies on *Proprietary Formats*.)
So now I have on my solution the .BSRs will also be mounted to fuse://s3-bucket/
AND I export the bacula db to fuse://s3-bucket/bacula.sql nightly via cron. and export fuse://s3-bucket/bacula.sql before every job and after every job.

I mean who would know this procedure besides me? Another admin that knows bacula.
The bacula-users mailing list is fairly active and community support is very generous via that medium.

rsync+tar-over-ssh is a very sane alternative for any admin that also thinks that process is insane.

---

### Post by lykwydchykyn on 2012-01-02
> **Habitual said:**
> 
 the .bsr files are a *Proprietary Format.*


That's good to know; I'd like the backups to wind up in some kind sane format like a tarball.  I'm thinking Bacula is off the list.


I guess part of the reason I set up things like this at home is as a "test ground" for doing things at work, though.  It'd be nice to get some experience with a system that could potentially be used in a SME production environment.

---

### Post by peanut3122 on 2012-01-02
> **TwiceOver said:**
> Look into BackupPC or better yet, Crashplan both are free.

I 2nd both above, also adding zmanda

---

### Post by fluca1978 on 2012-01-02
What about [rsnapshot]("http://rsnapshot.org/")? It is based on rsync and seem very promising. PCBSD has a very interesting tool that I hope will be ported also to Linux called life preserver.
In my network I use always a FreeNas appliance to which I do an rsync backup, seem to me rsync is pretty well suited for all occasions.

---

### Post by Paddy Landau on 2012-01-02
> **fluca1978 said:**
> What about [rsnapshot]("http://rsnapshot.org/")?
That looks very similar to rdiff-backup. I looked up the differences between the two and came to the following:
[http://www.saltycrane.com/blog/2008/02/backup-on-linux-rsnapshot-vs-rdiff/](http://www.saltycrane.com/blog/2008/02/backup-on-linux-rsnapshot-vs-rdiff/)

I have been using rdiff-backup for a long time and have been very happy with it.

However, I found a great discussion about which backup system to use; this may help:
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)

---

