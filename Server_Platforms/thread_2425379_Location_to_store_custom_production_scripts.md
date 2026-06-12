---
title: "Location to store custom production scripts"
date: 2019-08-25
forum: Server Platforms
---

### Post by aljames2 on 2019-08-25
What is best practice on location to save scripts being used by the system such as cron?  They need to be owned by root to run do that seems to imply some location other than an administrators /home location?  Yet it should be somewhere so that a restore isn’t broken..

I’ve read lots of opinions, some from 5+ years ago so not sure current best practice:

```
~/bin
/usr/local/bin
/usr/local/sbin
/var/myscripts
/opt/myscripts
/home/user/bin
```

---

### Post by TheFu on 2019-08-25
If the scripts contain sensitive information, I use /root/bin/
If the scripts are purely for admin reasons, /usr/local/sbin/
If the scripts are for anyone on the system, /usr/local/bin/
My personal scripts go into ~/bin/.  Do not assume that HOME directories are in /home/.  That only applies for tiny installations. Nothing mandates or requires it. Large sites use NFS with autofs for HOME directories which could be mounted anywhere the NFS admin chooses. I've seen /u/a/adam .... /u/z/zack setups for sites with thousands of users, basically 26 different mounts.

The Linux File System Hierarchy covers this stuff.  You can google for it.  [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) has an overview.

I've never seen  "myscripts" used anywhere.

---

### Post by LHammonds on 2019-08-26
My scripts run under the root account and I place them under /var

I create a folder to contain all of them under /var/scripts/
The sub-directories I use are:
/var/scripts/prod (production-ready)
/var/scripts/test (testing only, not ready for production)
/var/scripts/data (data files for the scripts and backups of crontab schedules)
/var/scripts/common (settings/functions/variables often imported into scripts)

Keep in mind this is not an industry standard...just how I have configured my environment and how I have documented my server installs and various applications.  The important thing is to document it and keep it consistent across all your servers and administrators.

LHammonds

---

### Post by SeijiSensei on 2019-08-27
I prefer /usr/local/bin and /usr/local/sbin depending on whether the script runs as root (sbin) or as an ordinary user (bin).  If my scripts have configuration files, I put them in /usr/local/etc.

---

