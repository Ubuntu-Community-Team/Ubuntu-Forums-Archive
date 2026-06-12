---
title: "Does RAID really help protect against data loss?"
date: 2008-04-07
forum: Security Discussions
---

### Post by xelapond on 2008-04-07
If I have a Mirrored raid array does it really help protect my data?  If the os corrupts the drive the same corruptions and errors will be written to both drives, so you lost everything.  I think a better backup scheme is rSnapShot(or other software based backups) because if your system gets corrupt you could probably go back a revision.

The only reason I ask is that I am trying to set up a high reliability unmanned server, so I think you would have a better "survival rate" with a software based backup.  Just wondering what you guys though.

---

### Post by tamoneya on 2008-04-07
a mirrored RAID array will prevent against a hardware failure but not the OS corrupting the filesystem.  If you are worried about filesystem corruption you should look at some backup system that backs up to an offsite server.

---

### Post by xelapond on 2008-04-07
Wouldn't a software solution like rSnapShot also prevent against hardware failure(loss of less then the total number of backup drives)?  I am just saying that you are protecting against more scenarios with software vs hardware.

---

### Post by chewearn on 2008-04-07
> **xelapond said:**
> If I have a Mirrored raid array does it really help protect my data?  If the os corrupts the drive the same corruptions and errors will be written to both drives, so you lost everything.  I think a better backup scheme is rSnapShot(or other software based backups) because if your system gets corrupt you could probably go back a revision.

The only reason I ask is that I am trying to set up a high reliability unmanned server, so I think you would have a better "survival rate" with a software based backup.  Just wondering what you guys though.

You are confused between two concepts:
1. hardware redundancy to protect against equipment failures

2. data redundancy to protect against general failures

---

### Post by tamoneya on 2008-04-07
a mirrored RAID drive also allows you to access data faster since the computer is able to access data from both drives in parallel.  It is not just a backup method.

---

### Post by eldragon on 2008-04-07
actually most drives are set to write back, instead of write through.

this means, that if there is still data in the cache, and there is a power failure, there is nothing you can do. chances are slim, but they still exist.

so even if i had raid-1, i would still keep incremental backups just to be sure.
raid-1 seems like a great idea for Uptime reliability and schedule a dying drive replacement intsead of having to rush it when it dies.

---

### Post by rickyjones on 2008-04-08
RAID is NOT backup, nor does it protect from data corruption. RAID protects you from hard disk failures.

For example, in a RAID1 array you can survive the loss of a single hard drive. You will not lose data.

Backups are supposed to prevent data loss from corruption and deletion. You should implement both RAID and backups to ensure total data security.

RAID prevents data loss resulting from a loss of hardware.
Backups prevent data loss resulting from a user or software error.

-Richard

---

### Post by xelapond on 2008-04-09
Thanks everyone for your clarification

So I guess Backups do prevent fom hardware failure, but you have to be there to restore it.  On the other hand, RAID1 will automatically switch disks on a failure.

---

### Post by Shazaam on 2008-04-09
Backups do NOT prevent hardware failure. Backups are used AFTER a hardware failure/data loss.

Raid links......
[http://www.acnc.com/raid.html](http://www.acnc.com/raid.html)
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by kevdog on 2008-04-10
RAID5 -- if one disks fails -- all your data is preserved -- it just warns you that you need to replace the drive to prevent catastrophe and data loss.  If two drives failed simaltaneously, well then your hosed!

Again a data preservation strategy, data backup strategy simply doesnt really on one process.  Its a multiple solution approach.  RAID5 to prevent hardware failure, and unison (rsync) for nightly backups to another computer work well for me.  I don't have an offsite computer or facility for backup, so I guess if there was a fire in my house and everything was burned I'd be out of luck.

---

