---
title: "Easy solution for encryption and online storage"
date: 2009-06-28
forum: Security
---

### Post by norman_ on 2009-06-28
Hi everyone, 

I was hoping someone could point me to an easy way to accomplish a task I need to do in the next few weeks. 

I have a rather large amount of data (+/- 60GB of mostly media and datasets I use for work), and I need to upload it to an online storage service for a few weeks before I can download it to another computer. The files are absolutely critical, and this will be the only copy in existence. I really NEED to get them back, and there is no simple way for me to keep backups elsewhere (long story).

My problem is that some of the data is quite sensitive, and I would not want anyone snooping. I'm hoping there's a way to create multi-part archives (for ease of upload with my slow connection) and then encrypt them in a way that's easy for me to recover, but hard for unauthorised eyes to read. 

Any suggestion would be much appreciated!

Thanks a lot

Norman

---

### Post by unutbu on 2009-06-28
Are you using Ubuntu 6.10?

---

### Post by Agent ME on 2009-06-28
60 gb of data? Not even trying to figure out where you'd host that, it would also take forever to upload.

---

### Post by norman_ on 2009-06-29
> **Agent ME said:**
> 60 gb of data? Not even trying to figure out where you'd host that, it would also take forever to upload.


I was thinking of using jungle disk which works with Amazon s3. You pay about 15 cents per GB, which is not that bad at all. It will take forever to upload for sure.

---

### Post by norman_ on 2009-06-29
> **unutbu said:**
> Are you using Ubuntu 6.10?

Hehe, I just haven't updated my profile in a while :)

Using 9.04 64bit at the moment

---

### Post by HermanAB on 2009-06-29
Get a hard disk and a USB adaptor.  Uploading 60GB of data will take weeks and something is bound to go wrong before you are done.

---

### Post by mdebusk on 2009-06-29
> **norman_ said:**
> The files are absolutely critical, and this will be the only copy in existence.

If you'll permit only one copy to exist, then they *aren't* critical files.

If they *are* critical files, you'd *better* have multiple copies.

Your best solution is to buy two or more external hard drives, put big-enough Truecrypt containers on them (or encrypt the entire volume of each), back up to the encrypted volumes, and store the drives in separate places.

The online thing just won't do what you want it to do.

---

### Post by norman_ on 2009-06-29
Thanks for the feedback everyone. I'm afraid you are right. I'll have to find an alternative that involves a physical copy.

---

### Post by Dr Small on 2009-06-29
It seems to me that you are putting a lot of stock in a remote backup on some offshore server that could care less if your only existing critical backup gets lost when they have a hard drive failure.

Buy a small external drive, and do what the rest of the guys suggested. Setup a truecrypt container and move your backups to this drive.

Dr Small

---

