---
title: "Keep external backup copy of an ubuntu server installation."
date: 2012-02-28
forum: Security
---

### Post by Beto on 2012-02-28
Hi, I have an old notebook as a home server.

Today my Hard Drive died. I was poorly prepared for this and only had a cron job which backed up the important folders to an external hard drive. However, I still have to install a new hard drive an reinstall ubuntu server and then copy the information back.

I would like to have a system which works daily copying the entire hard drive (all partitions included) to an external hardrive, so in case of a new hard drive crash scenario I would only have to put the copied hard drive on the notebook and everything is working again.

Is it possible? How would I go about that?

Regards,
--
Beto

---

### Post by drmrgd on 2012-02-28
I personally like [rsnapshot]("http://rsnapshot.org/") for this.  It's super easy to setup, keeps any combination of daily/weekly/monthly backups, plus it'll keep as many versions of the backup as you can or want to store.  You can keep 1 backup for each day so that if you only want to roll back 1 day you can, but if you had to, you could also roll back just 2 days or whatever. It runs rsync as either a cron or anacron job so, you can basically just set it and forget it.  

I've only been using it to backup home and a few other directories so far.  But, I'm sure you can easily backup up the whole system. Have a look to see if that fits your needs.

---

### Post by WasMeHere on 2012-02-28
Hi Beto,

I guess you want a system that works while your computer is running.

I suggest that you make a backup system using ***rsync***. The built-in manual is quite well written and gives several examples.
```
man rsync
``` You can also browse the internet for ***linux backup*** and for ***rsync tutorial*** or something similar.

But if you want a complete and perfect clone, you should do it when you boot from another drive, for example from a live CD or USB drive with Clonezilla.

Maybe you can combine the two:

1. Make a complete clone of your system as it is now.
2. Make updates with rsync to another drive or another computer.

and when you have to restore the system:

1. install the cloned drive (which is a very fast operation)
2. restore the rsynced data (overlay onto the installed clone)

But it is also rather fast to install your basic system from a boot CD or USB drive, and restore the rsynced data onto that basic system.

I am looking forward to what other people will suggest :-)

Have fun finding out
Olle

---

