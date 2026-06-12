---
title: "HOWTO: Backup Your System Before You Upgrade (To Rollback if Need Be)"
date: 2009-06-25
forum: Tutorials
---

### Post by guywithcable on 2009-06-25
Here are some commands that you can use to backup your system prior to an upgrade. You can do this in case anything during the upgrade goes wrong, or you just don't like the new version.

First of all, to save time, you can run these commands to clean up a little first:

```
sudo apt-get autoremove
sudo apt-get autoclean
```Now for the backup. Depending on how much free disk space you have, you might want different levels of compression, so here are a few options:

-No compression (fast, big file)
```
sudo tar -cv --one-file-system --exclude=/home/* --exclude=/dev/* --exclude=/proc/* --exclude=/sys/* -f /home/system-backup.tar /* && sudo chown `whoami`:`whoami` /home/system-backup.tar
```-Medium compression (slow, small file) (recommended)
```
sudo tar -cvz --one-file-system --exclude=/home/* --exclude=/dev/* --exclude=/proc/* --exclude=/sys/* -f /home/system-backup.tar.gz /* && sudo chown `whoami`:`whoami` /home/system-backup.tar.gz
```-High compression (very slow, very small file)
```
sudo tar -cvj --one-file-system --exclude=/home/* --exclude=/dev/* --exclude=/proc/* --exclude=/sys/* -f /home/system-backup.tar.bz2 /* && sudo chown `whoami`:`whoami` /home/system-backup.tar.bz2
```When that finishes, you should have a nice backup of your current system. :)
I've found that it's always a good idea to do this before an upgrade, because the new version might be incompatible with your hardware. You can recover your system using a live cd, but unfortunately, the commands will be different depending on your system, so you can make a post here if you need help recovering your system.

---

### Post by Roanoke on 2009-06-25
Interesting. I wouldn't exclude /home/* though.

---

### Post by guywithcable on 2009-06-25
> **Roanoke said:**
> Interesting. I wouldn't exclude /home/* though.

/home usually contains a lot of data, which doesn't really need to be backed up before an upgrade. Probably the only thing that could cause problems is the configuration stuff stored in /home being updated, then not working when you roll back, but that's not too big a deal for me. I tried to include /home/`whoami`/.* but that matches the "." entry (current dir) and ends up including all the regular folders too.

If someone wants to write another command to back up just the configuration stuff (all "dot" dirs except ".wine" should work), please post it here. :)

Does anyone know if there is a way to match include files for tar using regular expressions? Then this should work:

include config dirs: ^/home/[^/]+/\.[^(/|wine)].*

And that would cover all the users too, unlike /home/`whoami`/.*

---

### Post by Roanoke on 2009-06-25
Well, keeping config files in between upgrades is a little risky as I have found. Perhaps if you didn't back up system configs, in which case some more precise exclude rules should back up only program configs. And the files in /home are not files that I would like to lose if bad things happen.

---

### Post by philcamlin on 2009-06-25
cool will use this in a while before upgrading to karamic :popcorn::popcorn::popcorn:

---

### Post by xxlray on 2012-11-14
I am thinking about upgradig my Ubuntu. I remember that I had a lot of issues getting the tv-receiver and my graphic card running. Will this method also backup my working kernel and drivers.
How do I recover my system from the archive?

---

### Post by wildmanne39 on 2012-11-14
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

