---
title: "Backup scheme for domain controller/file server"
date: 2008-08-08
forum: Server Platforms
---

### Post by shizakapayou on 2008-08-08
I'm about to deploy Ubuntu Server 8.04 64-bit as my domain controller (OpenLDAP and Samba) and file server.  The server itself is a Dell Poweredge 2950 with 6 x 500 GB drives for a total of ~2.5 TB usable.  The machine has 8 cores (Xeons) and 8 GB RAM.  Before I get started, I want to get rolling on a backup plan.

The filesystem itself has several partitions which I can list if needed, but the largest is /home - 2.3 TB.  This is where all Samba shares are located.  The rest of the machine should stay fairly static - the only files that should change is smbldap configs as I add or remove users and machines to/from the domain.  This is a small company, so once everyone is on the domain, there won't be many changes.

In reading, it seems using tar would be a pretty straightforward way of accomplishing this.  My idea was to run two tar jobs - one daily during the day to get everything except home, and then one nightly Monday-Friday backing up home.  I'm not sure, but I may need two for /home, since the single file size could exceed 2 TB.  That's no problem, my /home has a few top-level folders, so it wouldn't be hard.

My question here is: is this a good way to approach this?  What hardware would you recommend backing up to?  I do need something removable, though I'm not entirely entertained by the idea of attaching tapes to this server.

---

### Post by cdtech on 2008-08-08
Although I don't run as much space as you, I did create a tar script that does this type of backup. I've set mine up using cron and does full, monthly and incremental to a ro external drive. Your more than welcome to check it out, just pm me.

---

### Post by shizakapayou on 2008-08-09
Thanks, I'll send you a message on that soon.

However, I still need hardware advice - anyone?  My original thoughts were backup to a second server nightly, and then maybe once weekly create a removable backup that can be stored elsewhere.  Obviously if another server is the best route I can pick anything with lots of space myself, but I'm not all that experienced in backups - no idea what the best route is.

---

### Post by windependence on 2008-08-09
The only problem with tar is that you will be backing up the same stuff every time you do it whether it has changed or not. I would use rsync. The first time you use it, it will back up everything, but then after that, when it runs, it will only backup what has changed from the last time. This saves time bandwidth,and CPU. 

The way I do it is to mount a separate hard drive in mt servers that is not in RAID or LVM with any other storage and I mount it as /backup. Then, all my backups are rsynced to that drive with a cron job every so often. If I wanted to, I could then back up to tape or other media from the backup file instead of the live server, so this would not interfere with the performance of your production stuff. Try to have the backup drive on a different I/O channel which is even better.

-Tim

---

### Post by cdtech on 2008-08-09
> **windependence said:**
> The only problem with tar is that you will be backing up the same stuff every time you do it whether it has changed or not.

That's not true. Using the --newer flag only backs up changed data.

---

### Post by shizakapayou on 2008-08-13
If the --newer flag in tar works as claimed, that sounds good enough to me, so long as it doesn't overwrite the old stuff as well.  One of my goals is to be able to recover a file from a few days ago, not just yesterday.

Unfortunately the server does not have room for more drives so hard disk space will have to be external, either external drives or another server.  I would like something removable as well, but honestly have no experience backing up this much data.  I've also had less than pleasing experiences with tapes before, so I'm not sure they're the route to go.  Thoughts?

---

### Post by windependence on 2008-08-13
Well it will depend on how the removable media is attached. If it is flash media, that would be the fastest and easiest. SATA II drives in removable cages are also good but the drawback is it will probably mess up your device order and give you all kinds of trouble. USB is too slow IMHO, as well as firewire. 

Seriously, unless you are worried about fire or catastrophe, I would just install an additional drive, mount it raw (no RAID, LVM etc) and mount it as something like /backup. If it must go offsite, then you don't have a lot of options. What I do is back it up to another drive first, and then take it off to tape from there. That way, the backup is quick to the drive with little impact on the prod stuff and then the tape backup can go on as long as it wants with no effect and the files are also not in use. The added benefit of this is that I then have a hot backup on site if I need it.

If you are wanting to have several days worth of backups, rsync or the tar flag aren't gonna help you because you will be writing the whole file every time unless you do incrementals, and if you are going to do that, you should use something like Bacula or Amanda so you can at least find the file you want to restore (which backup is it in?).

-Tim

---

### Post by shizakapayou on 2008-08-13
> **windependence said:**
> Seriously, unless you are worried about fire or catastrophe, I would just install an additional drive, mount it raw (no RAID, LVM etc) and mount it as something like /backup. If it must go offsite, then you don't have a lot of options. What I do is back it up to another drive first, and then take it off to tape from there. That way, the backup is quick to the drive with little impact on the prod stuff and then the tape backup can go on as long as it wants with no effect and the files are also not in use. The added benefit of this is that I then have a hot backup on site if I need it.

That's actually along the lines of what I was thinking of.  However, since I'm out of drive space, it'd have to go to a second machine (which I have no issue with, though I know it'll take longer).  From there, I could put it on tapes (autoloader hopefully) which would allow for a few days of backup.  Let the next night's backups overwrite what's on the server, as previous days will be on tapes.  If I split it into a few jobs, I should be able to fit everything on 3 LTO3 (or 4, whichever does 800 GB) tapes, while the previous day remains as a hot recovery on the server.

It seems to me using tar or rsync should be simple, since the --newer flags would overwrite only what's changed on the backup server, so once an initial backup is moved to the backup server, bandwidth should stay low.  If that's wrong, I'll definitely look at Amanda or Bacula.  I think I've seen cron jobs that name the backup file according to the day it runs - I'll look into that as well.

---

