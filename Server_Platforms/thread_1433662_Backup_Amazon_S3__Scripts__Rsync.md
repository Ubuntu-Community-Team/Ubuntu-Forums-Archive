---
title: "Backup Amazon S3 / Scripts / Rsync?"
date: 2010-03-19
forum: Server Platforms
---

### Post by ksudbury on 2010-03-19
Just wondered if any of you guys are using Amazon S3 for your backups and if so, what scripts are you using? Rolling your own or is there some half decent open source solutions? 

I want to try it out for backing up flat files / MySQL dumps. 

TIA!

---

### Post by ushills on 2010-03-19
Personally I use Jungledisk but it is not free, for FOSS I would go with duplicity.  Uploading can be slow but restoring from off-site is great.

---

### Post by ksudbury on 2010-03-19
I have used JungleDisk before however it has no command line? It's gui only?

---

### Post by falconindy on 2010-03-19
Short Version: Whatever you choose as your backup method, **stick with it**. If you are going to be making substantial usage of S3, I recommend a service like s3rsync or jungledisk.

**Long Version:**
Some time in the 3Q of last year, I toyed with the idea of an rsync based backup script for S3 at my brother's request. While it worked, it was slow and mildly unreliable. I'll blame this on the connection medium ([s3fs](http://code.google.com/p/s3fs/)), not my script.

rsync generates a lot of extra bandwidth determining what files it needs to transfer before it actually does the transfer, particularly when it has no rsync daemon on the other end to communicate with. In my testing, roughly the same bandwidth was used doing an update of only a few files versus blindly rsync'ing the entire bucket up to S3.

My major concern with S3 is that a directory does not have a standard definition. I'll expand on that. While a bucket is a bucket and is defined by Amazon, a directory within a bucket does **not**. This is determined by your backup agent, and **is not guaranteed to be (read: won't be) compatible with multiple backup agents**. In other words, if you do your backups with JungleDisk and then switch to another method, you'll see an empty bucket because the new software doesn't understand the directories put in place by JD.

---

### Post by ushills on 2010-03-19
> **ksudbury said:**
> I have used JungleDisk before however it has no command line? It's gui only?

Incorrect, the latest desktop edition has reintroduced CLI support and there is a server edition.

---

### Post by ksudbury on 2010-03-20
> **ushills said:**
> Incorrect, the latest desktop edition has reintroduced CLI support and there is a server edition.

Ohh, I might check it out then, does it have a 5GB file size limit still?

---

### Post by doogy2004 on 2010-03-21
> **ksudbury said:**
> Ohh, I might check it out then, does it have a 5GB file size limit still?

[http://www.jungledisk.com/personal/desktop/faq/default.aspx](http://www.jungledisk.com/personal/desktop/faq/default.aspx)

> What is the maximum file size that can be stored with Jungle Disk?

There is no limit to the total number or size of files you can backup. For the Network Drive feature, there is a file size limit of 5GB. Note that package files on the Mac, such as Aperture vaults or iPhoto libraries, are actually directories made up of many files. The 5GB limit does not apply to the total package size, which can be virtually unlimited.


This seems to have to do with the way that the files are cached on disk when using the Network Drive feature.

---

### Post by the0ther on 2010-04-08
> **ushills said:**
> Incorrect, the latest desktop edition has reintroduced CLI support and there is a server edition.

i have been having a REAL hard time getting jungledisk setup so that i can mount it at /mnt/jungledisk and access the files as a regular (non root/non su) user. it's very hard to find instructions. could you point me somewhere or do you have any tips?

the error message i'm getting follows:

Failed to mount volume

Warning Details (Jungle Disk Desktop 3.06 Linux Console i386)
------------------------
xDriveMapFailed - fuse_mount(/mnt/jungledisk) failed: fuse: failed to open mountpoint for reading: Permission denied

Exception Code: xDriveMapFailed (51)
Time: 04/08/2010 08:28:07 PM (GMT-4)
Detailed Message: fuse_mount(/mnt/jungledisk) failed: fuse: failed to open mountpoint for reading: Permission denied

Error Location: JungleFuse.cpp:1468 
   via JungleFuse.cpp:1569

---

### Post by the0ther on 2010-04-08
i finally got this working. i had to add myself to the fuse group, and then i had to change up the permissions on my /etc/fuse.conf file. i THINK this is what got it working ultimately. 

but it's weird...if i edit files with gedit, i cannot save them, but with nano on the command line it works fine. that's good enough for me.

---

### Post by fogNL on 2010-09-13
I know i'm reviving an old thread here, but, I had a question that maybe someone could answer, without me starting a new thread.

I have a home setup with a Ubuntu 10.04 server and a desktop and laptop that dual boots between windows/ubuntu.

If I went with the jungledisk personal desktop edition, can I use it for all of my machines, the server included?  Or do I need a separate one for the server (just a small server hosting a few websites, sql, etc.)?

I'm currently using free dropbox (2GB) but i'm approaching its limit now and want to move to something a little bigger, but I don't need Dropbox's next tier of $10/month for 50GB.

So, main question, what's the difference between the desktop edition and the server edition in my setup?  Any?  Will desktop edition work on all 3 systems?

---

### Post by michaelzap on 2010-10-03
> **cquilliam said:**
> I know i'm reviving an old thread here, but, I had a question that maybe someone could answer, without me starting a new thread.

I have a home setup with a Ubuntu 10.04 server and a desktop and laptop that dual boots between windows/ubuntu.

If I went with the jungledisk personal desktop edition, can I use it for all of my machines, the server included?  Or do I need a separate one for the server (just a small server hosting a few websites, sql, etc.)?

I'm currently using free dropbox (2GB) but i'm approaching its limit now and want to move to something a little bigger, but I don't need Dropbox's next tier of $10/month for 50GB.

So, main question, what's the difference between the desktop edition and the server edition in my setup?  Any?  Will desktop edition work on all 3 systems?

Just stumbled upon your question. Dunno if you've already answered it or moved on by now. I've used a single desktop version of JD to synchronize files on multiple machines on several occasions and it's never been a problem. The Network Drive feature works very well for this, although it's not the preferred method for backups. I have been backing up all of the files on my file server (including local machine backups) to JD for a long time now, and it's saved my butt more than once. Plus I just sleep a lot better knowing that all of our files are there in the event of a fire, robbery, or multiple drive failures.

---

### Post by zereshk on 2011-09-07
I use [s3cmd]("http://s3tools.org/s3cmd"). Pure Python, small intuitive command-line, open source and cool :)

---

### Post by mikaelcrocker on 2012-01-05
I don't know if you've had a chance to do this already, but I would use s3fs, and mount your s3 bucket as a normal file system.  There is a fair amount of documentation on doing all of this.  You can also use fstab to have it mount at boot.  So backing up your files can be as easy as copy pasting into a file on your desktop.

---

### Post by Habitual on 2012-01-05
> **mikaelcrocker said:**
> I don't know if you've had a chance to do this already, but I would use s3fs, and mount your s3 bucket as a normal file system.  There is a fair amount of documentation on doing all of this.  You can also use fstab to have it mount at boot.  So backing up your files can be as easy as copy pasting into a file on your desktop.

One of my setups is a CentOS5 bacula host with a fuse-mounted s3 bit bucket as our bacula backups. (fuse://s3-bucket/)

I had issues with the fuse module ("modprobe fuse") on Ubuntu, but it was flawless with CentOS5.x

---

