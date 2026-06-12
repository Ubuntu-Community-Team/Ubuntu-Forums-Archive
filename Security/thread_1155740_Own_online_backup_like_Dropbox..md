---
title: "Own online backup like Dropbox."
date: 2009-05-11
forum: Security
---

### Post by ahold on 2009-05-11
Welcome,

I have question, do you know any software what can i use, to backup my /home/user/projects directory ?

It should be like Dropbox, automatically backup file, when modification was made. 

I'm working on my project, when i made some changes to code it should automatically backup it, if i remove something, it should remove it.

When i see, oops, i need this file back, or i need previously version, just open time line and select, this file from 2 minutes.

Any idea ?
[B]
RSYNC is good application, but it cant approve changes on my every click (save file).
[/B]

Dropbox is great !, but it's good if you have 1 gb files. 
I have loot more, i don't have bandwidth to move xx gb/s everyday using internet connection.
I need own, LAN backup application.


If someone can help me, i will be very aprishiated.

Regards
 

I don't need security, my server is inside LAN.

---

### Post by ad_267 on 2009-05-11
If you're writing code you should probably use a version control system like subversion, git or mercurial.

---

### Post by ahold on 2009-05-11
Thank you for reply.
CVS is not this same.
I can use this to commit changes.

What, should i add CVS to cron, and run it every minute ?

I need to have full backup.

Few day's ago i have power fault, and i loose some data.
Yesterday, i have hard drive fault.

No the time is over, i need professional solution.

I'm codding something, i cant stop everything, and manually start copy files to another hard drive, because i can't have backup on same partition. You know, this all should be done, without my attention, in background.

I'm doing my work, and software doing rest.


On my server, i think have good security.
RAID 1  and 2 time in month backup this raid device to external drive.

Bu i can't move my files, using FTP... it's too heavy for me.
I need to delete previous, create new folder, add date, compress it, put it on server.

And i should do it, on every big change.

I need something else from CVS.


Regards

---

### Post by ad_267 on 2009-05-11
I don't think there's anything available that can backup files as soon as you save them. Some backup applications that are available are bacula, afbackup and amanda, but I don't think these meet your needs. I think rsync is probably the best option, just have it run regularly enough through cron.

---

### Post by Paddy Landau on 2009-05-12
Try this:

Run *rdiff-backup* once to create your initial backup. This will take a little time, depending on how much data you have and how fast your network is.

Then, place *rdiff-backup* into a *cron* job to run (say) every five minutes.

* rdiff-backup* will keep your backup area up-to-date as well as allowing you to revert on a timeline. You can use the option *--remove-older-than* in order to clean up older copies that you're no longer interested in.

Use *man rdiff-backup* to see the various options; it's pretty flexible.

(If you should need security, use *duplicity* instead; it's like *rdiff-backup* but encrypts the backups with GPG. It's a little harder to use when you have to restore, though.)

HTH

---

### Post by krendar on 2009-05-12
I wonder if UbuntuOne can do that:

[https://ubuntuone.com/](https://ubuntuone.com/)

I only briefly read about it earlier today. Can't say if its possible with it.

---

### Post by pc-cito on 2009-05-13
rdiff-backup and cron works fine

---

