---
title: "Backup Recommendations for business use?"
date: 2009-09-13
forum: Server Platforms
---

### Post by diazepam on 2009-09-13
Hi all,
 
I have been looking at backup solutions for network envirionments for ages now. At present I use a roll-your-own rsync/mysqldump/smb script.
 
My networks generally have Ubuntu LTS as the primary server and with other machines such as Windows 2003/08 within vm's to provide specialist software services. Hardware for these servers is HP, Dell (and Clones for smaller networks)
 
I cant seem to find a solution that fits the following requirements and would appreciate any recommendations
 
**Requirements**
* Run on Ubuntu LTS
* Disk based storage
* Capacity to back up Linux, Windows, and VMware Images
* Amazon S3 service integration for offsite backups (amazon only accepts max 5G files on raw transfer e.g. rsync)
* Gui for visual checks and for ease of management
* Capacity to backup open files
* Email reporting (errors)
* GPL 
 
**Desirable**
* Integration into Nagios or Zenoss
* Streamlined configuration - i dont have the time to spend hours and hours on configuring and reconfiguring.
 
**_SO FAR?_**
So far i have looked at (see pros and cons listed below)
 
* **BackupPC** - great disk based backup, simple to administer, web GUI which assists management. Does not backup open files, does not integrate into Amazon S3 easily, can not backup MYSQL without having to hack the configs.
 
* **Amanda **- Integrates into S3, backs up live files, backs up MYSQL, backs up MS2003/08 exchange. Gui only on commercial version, no email notifications that i have found yet. IRC support/forum support seems to be lacking.
 
* **Bacula **- GPL'd, email reporting, capacity to back up open files, great forum and IRC support. No S3 support that allows for the 5Gb limit, disk based storage looks like a pain to set up, requires Bacula to get at backups (cant use standard *nix tools). Forums are filled with people saying this thing is extremely tricky to set up.
 
 
Have I got this right? Or am i overlooking something? I would appreciate any recommendations or success stories! :D

---

### Post by HermanAB on 2009-09-13
"At present I use a roll-your-own rsync/mysqldump/smb script."

That is exactly what everybody else does.  You are on the right track - keep going.

---

### Post by diazepam on 2009-09-13
Yeah - im hoping for something a bit more enterprise ready though. Any suggestions?  What do the REL and SUSE engineers use?

---

### Post by windependence on 2009-09-13
> **diazepam said:**
> Yeah - im hoping for something a bit more enterprise ready though. Any suggestions?  What do the REL and SUSE engineers use?

Amanda is about as close as you're gonna get. If you want real enterprise you could pay for Veritas, but you're really not getting much more features. I am almost positive I saw something in Amanda for e-mail notifications. Let me dig through my notes.

-Tim

---

### Post by windependence on 2009-09-14
Check this:

[http://wiki.zmanda.com/man/script-email.8.html](http://wiki.zmanda.com/man/script-email.8.html)

-Tim

---

### Post by tlarkin on 2009-09-14
Do you need to preserve ownership and permissions of said files from other platforms?  Linux is great for this but I am not sure if you can preserve ACLs, ownerships, and permissions from a Windows box on a Linux server.

However, I currently roll my own as well in a shell script ran by cron (launchd as I am on OS X).

---

