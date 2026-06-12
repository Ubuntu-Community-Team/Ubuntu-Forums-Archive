---
title: "Recovering MySQL data files"
date: 2011-01-28
forum: Server Platforms
---

### Post by painejake on 2011-01-28
We ran into some problems with our Ubuntu server yesterday. It crashed and when it came back up it drops me into a recovery console and locks the filesystem to read only. I have tried using some of the recovery tools to no availe.

I have tried booting from a live CD and removing in the fstab file where it says to boot to readonly filesystem if errors occur however I still can't get the issue sorted.

If I can't get it sorted by this morning I will have to re-install, which brings me to my next question, How can I recover the MySQL data files under as they are locked when using the live CD and it won't let me copy them onto a USB hard disk using the read only filesystem.

Any help apriciated!

---

### Post by SeijiSensei on 2011-01-28
> **painejake said:**
> We ran into some problems with our Ubuntu server yesterday. It crashed and when it came back up it drops me into a recovery console and locks the filesystem to read only. I have tried using some of the recovery tools to no availe.

I have tried booting from a live CD and removing in the fstab file where it says to boot to readonly filesystem if errors occur however I still can't get the issue sorted.

If I can't get it sorted by this morning I will have to re-install, which brings me to my next question, How can I recover the MySQL data files under as they are locked when using the live CD and it won't let me copy them onto a USB hard disk using the read only filesystem.

Any help apriciated!

1)  Don't force things.  Linux won't mount the root filesystem read-write if it has errors.  Boot from a rescue CD or  [Knoppix]("http://www.knoppix.net/"), then run fsck against the filesystem to recover from any errors it can find.  Once the filesystem is clean it should mount again at boot.

2)  If you're lucky, everything will be intact.  What matters are the structures under /var/lib/mysql.  If they're okay, the server should come back up.  

3)  If you do have to re-install mysql, you might find the current versions are ahead of what you were running.  Last time I had to do this, mysql detected that the files were from an older version and rebuilt them on-the-fly.

4)  Start running a [mysqldump backup job]("http://ubuntuforums.org/showpost.php?p=10368151&postcount=3") each night from cron.  It's a lot easier to rebuild if you have a nice plain-text backup file to start from.

---

