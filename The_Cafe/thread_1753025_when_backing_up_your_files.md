---
title: "when backing up your files"
date: 2011-05-08
forum: The Cafe
---

### Post by polardude1983 on 2011-05-08
I have been backing up my /home dir and my /etc dir to an external hard drive. Question is which do yall think is better backing them up from folder to folder? or from folder to a .tar archive?

I also try to upload whatever files I have to my google docs account too.

---

### Post by Thewhistlingwind on 2011-05-08
Honestly, it never occurred to me to use a .tar archive. I always just backed up folder to folder, I guess tar.gz.bz WOULD save quite a bit of space.

---

### Post by Paqman on 2011-05-08
> **polardude1983 said:**
> which do yall think is better backing them up from folder to folder? or from folder to a .tar archive?


Depends. The only reason to pack them into an archive is if you want to conserve space. If your backup destination is big enough then just leave the files as is.

---

### Post by polardude1983 on 2011-05-08
Thinking of creating a simple backup script with rsync to do incremental backups to my external hard drive at night.

I think I can pretty much get away with this script here?

```
#!/bin/sh

rsync -avh /home/ /media/My\ Book/Backup/home/
```

---

### Post by YuiDaoren on 2011-05-08
Both.

I use rsync for a daily mirror, and tar/bzip2 to make a weekly snapshot.

---

### Post by speedwell68 on 2011-05-08
I just select the files and folders I want, copy them and paste them into a backup folder on my external drive.

---

### Post by KingYaba on 2011-05-08
I simply tar -cf my Pictures and Documents folders and then move it to my storage drive. I password 7z my e-mail, alternatively. ```
-mhe=on
``` encrypts the file list, too, which I like.

---

### Post by Retlol on 2011-05-08
Select folder. Copy. Open 2nd internal harddrive. Paste over previous backup.

Win.

*I don't see the point in encryption and archives for my backups. The stuff that need backups are text files and a few pics. Encryption is for serious business, archives are not needed for 100 mb or so.*

---

### Post by Irihapeti on 2011-05-08
Big thing is that you're doing a backup. That puts you ahead of about 90% of the forum membership. :)


[SIZE="1"]Source of figure: I just guessed...[/SIZE]

---

### Post by cgroza on 2011-05-08
I put them in a folder on Ubuntu One or Dropbox. No need to archive them.

---

### Post by aysiu on 2011-05-08
I'm not sure why you would back up the /etc folder. Isn't that just system files?

I think /home has the only stuff specific to your installation. Anything else you can bring back with a reinstall.

---

### Post by polardude1983 on 2011-05-09
> **aysiu said:**
> I'm not sure why you would back up the /etc folder. Isn't that just system files?

I think /home has the only stuff specific to your installation. Anything else you can bring back with a reinstall.

AFAIK the /etc folder holds your systems settings. So if i were ever to do a fresh installation i can have my /home (apps and personal files) and my /etc (systems settings) but correct me if im wrong :P

---

### Post by aysiu on 2011-05-09
/etc does hold the system settings, but they are not settings specific to your installation. They are general Ubuntu settings. If, for example, you change the layout of your Gnome panel, your changes will be stored in your /home folder. The default settings are, however, stored in /etc

---

### Post by polardude1983 on 2011-05-09
> **aysiu said:**
> /etc does hold the system settings, but they are not settings specific to your installation. They are general Ubuntu settings. If, for example, you change the layout of your Gnome panel, your changes will be stored in your /home folder. The default settings are, however, stored in /etc

well thank you for clarifying :D

---

### Post by Irihapeti on 2011-05-09
Some files in /etc will be specific to your installation, such as password, hosts, fstab and ppp if you use it. If you've installed anything that requires tweaking config files in /etc then those will also be specific to your installation, and you might want to have backup copies of them.

Rather than backup /etc, I take a snapshot of the system minus the home directory every 2 weeks or so (probably ought to do it more often) so that if I bork my system I can restore it quickly.

---

### Post by Sean Moran on 2011-05-09
> **polardude1983 said:**
> I have been backing up my /home dir and my /etc dir to an external hard drive. Question is which do yall think is better backing them up from folder to folder? or from folder to a .tar archive?

I also try to upload whatever files I have to my google docs account too.

Typically, it should all be in your /home directory, with /etc fairly easily replaceable with a new install.  Don't forget /var/cache/apt/archives for any .deb files you might have added. Keep all your .deb filesand it can save on future bandwidth if you can **sudo cp **them back again before installing software you have installed before.

More on-topic, think in terms of days, weeks, months, and years.

Assume you have one or more spare partitions on your primary hard disk, one or more external HDDs and/or some USB drives, and a DVD ROM.  The more the merrier.

Most important of all is to know how to categorise all of your data as you acquire it each day, and store it in your ~/home directory.  Be it Desktop,Downloads,Documents,Music,Pictures, etc. or subdirectories as you prefer, make it a habit to save ANYTHING you do over each day in those specific directories.  (bookmarks tend to wind up somewhere in the /home/~/.mozilla directory or somewhere like that).
Know which subdirectories are changing as you work each day.

Every night, you could write a simple shell script for this, but copy your 'tainted' data directories to another partition on your hard disk.  This is the minimal daily backup to prevent accidental deletions.

Every Sunday night, copy that data on the backup partition to a USB drive or DVD, or hopefully a nice big external USB HDD.  Create a new directory and give it a name such as 2011-05-wk1 or something pertaining to that particular week.

To be safe, it is good to have twin USB hard disks to double-care for reliability, or at least make a double backup onto a DVD or two if you need to. 

At the end of the month, you can combine those into a single monthly archive, if you remember to copy the earliest backup first, and then overwrite until you reach the end of month.

The weekly backups are probably fine to overwrite after a month or two, (to make sure you didn't delete anything half way through the month accidentally).  Then at the end of the year, you should have 12 month's worth of backups.

Compress that year into 12 separate 7z or tar files. and copy that to somewhere reliable or two.  Then you can start a new year.

---

### Post by Irihapeti on 2011-05-09
If you are working hard for a period of hours on something important, back it up every hour or even half-hour. You don't want to have to re-do several hours' worth of work if something goes wrong and you're on a deadline.

Been there, done that. Not fun.:cry:

---

