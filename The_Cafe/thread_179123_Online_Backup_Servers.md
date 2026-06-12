---
title: "Online Backup Servers"
date: 2006-05-19
forum: The Cafe
---

### Post by gushy on 2006-05-19
After a bit of a disk failure / backup disaster I'm looknig into using an online backup facility as part of my new backup strategy (this is personal use not work so I'm looking for free / cheap services).

I'm looking for a service where I will be able to schedule non-interactive backups so it really needs rsync / ssh / ftp access or WebDAV access that'll let me mount the 'drive' and just cp to it.

So I was wondering if anyone had any experiences using any online backup services with linux as most of the sites only seem to mention windows.

The services that seem pretty good are (from my initial investigations):[LIST]
[*][mozy]("http://www.mozy.com/") - 2Gb free (email supported) or $19.95 pa - 5Gb
[*][ibackup]("http://www.ibackup.com/") $9.95 pcm / $99.95 pa - 5Gb
[*][Amazon S3]("http://aws.amazon.com/s3") - $0.15 per GB per month storage & $0.20 per GB transferred
[*][Box.net]("http://www.box.net") - 1Gb free, 5Gb $4.99 pcm / $49.99 pa, 15Gb $9.99 pcm / $99.99 pa
[/LIST]

Of these the only one that I know can definitely be used with linux is Amzon S3 by using [Jungle Disk]("http://www.jungledisk.com/") althugh I've yet to read enough to determine whether you have to use the Jungle Disk interface.

Obviously I'd love to hear about any other services if they support linux.

---

### Post by JonnyRo on 2006-08-28
I'm starting to experiment with Jungle Disk/S3 myself.

---

### Post by jdong on 2006-08-28
Wouldn't it be cheaper and more convenient to buy an external hard drive or two or three?

---

### Post by bruce89 on 2006-08-28
> **jdong said:**
> Wouldn't it be cheaper and more convenient to buy an external hard drive or two or three?

Not to mention safer and quicker (bandwidth wise).

---

### Post by jdong on 2006-08-28
Also, don't forget about DVD-R's.... dual-layer (and even single-layer) DVD's are great for backing up, unless of course you have a 500GB anime collection, in which case I'm not sure you want to be waiting to upload that to an online drive anyway :)

---

### Post by gushy on 2006-08-29
for me this kind of solution is for essential data only - so only a small amount.  Encryption is enough for me to satisfy the safety issue and bandwidth is not a problem.

I currently use a mixture of external hard-disks, DVD-Rs and DDS4 tapes to backup however as this my home stuff and the backups are at my house as well, so in the event of a fire or theft it's all gone.

Keeping only the essential files in an online backup system would be great emergency backup.

JonnyRo: I'll be very interested to find out how you get on.  I haven't actually moved forward on this since my original post, as it's not an urgent requirement.

---

### Post by Michael_aust on 2006-08-30
I agree with the harddrive solution.  By a new harddrive and use the amanda backup utility to schedule a daily back up to the second harddrive or something.

---

### Post by Louwe Louwe on 2009-02-07
> **Michael_aust said:**
> I agree with the harddrive solution.  By a new harddrive and use the amanda backup utility to schedule a daily back up to the second harddrive or something.

What happens when you have a fire that toasts your computer, the external harddrive and your DVD backups?

---

### Post by michaelzap on 2009-02-07
I have a local backup on a secondary network drive, a periodic dump to a USB hard drive that I store offsite, and I do incremental backups to Amazon S3 via Jungle Disk (can you tell I've been burned by data loss before?).

I highly recommend Jungle Disk. Their software allows you to mount your Amazon S3 bucket as a drive on your system, and then you can access your data any way that you like (directly by opening the mount point in your file manager, via your browser using the web interface, using (g)rsync, or using the Jungle Disk Monitor software, which pretty much does the same thing that Grsync does). If you set an encryption key then any way that you access your data it will be encrypted so that only you can read it (I believe it's 256-bit AES), as well as being sent via SSL.

I paid $20 for Jungle Disk's software (they give you lifetime updates and programs for Linux, Mac, and Windows), and I have about 15 GB on Amazon's servers now (or something like that - I pay a little less than $7/month). It's definitely a bargain if you value your data. Once Gdrive is public I may consider switching to that, but really only because it will probably be free.

---

### Post by ahelmick on 2009-02-26
the external hard drive backup is no more useful, usually, than the original copy of the data... especially if you use a laptop and travel frequently...

Online backup is the only way to go...

---

### Post by binbash on 2009-02-26
Wow it was a little old thread : ) Anyways i am using dropbox, it is fine

---

### Post by gushy on 2009-02-26
You're right this is an old thread! 

I'll definitely have to look into Jungle Disk.  I too am currently using dropbox which I love, however the only issue is encryption.  I had the bright idea of creating truecrypt containers and using them, the only problems being that it's a big file to re-upload for any small change, and if I forget to unmount the container before leaving the office, I won't see any updates at home.

---

### Post by frrobert on 2009-02-26
For online backup I am using Amazon S3 and I use S3cmd command line tools to transfer the files.  s3cmd has options to transfer the files with http or https.  It also has the  option to encrypt the files with pgp.

---

### Post by jwooton on 2009-04-27
Here is a new service that offers unlimited storage for only 2.99 a month.  It's very linux friendly in that it supports RSYNC, SFTP, and SCP.  You can get a free month trial without giving any financial information.

[http://www.datastorageunit.com]("http://www.datastorageunit.com")

---

### Post by jgt157 on 2009-11-14
try spideroak...2G free online backup...and a really good interface.

---

### Post by gushy on 2009-11-14
I've started using [Crashplan]("http://www.crashplan.com").  Which I think is great.  For free you can only back up to other PC's across the internet (which has been fine for me), however I'm impressed enough that I'm also going to take out their backup package which is $5 a month.

---

### Post by TDFZ on 2011-01-11
Get **DropBox**!  It integrates with nautilus perfectly. 

[http://www.dropbox.com]("http://www.dropbox.com")

---

