---
title: "ubuntu built-in backup in preferences"
date: 2014-09-16
forum: Ubuntu Development Version
---

### Post by ivo-welch on 2014-09-16
my perl backup script ran into all sorts of trouble (setuid-related), so I decided to switch to a "standard" solution, presumably the ubuntu backup that is built into ubuntu preferences.  I turned it on, to backup to a directory on another hard disk.  this was easy.   it probably did its first backup, and its probably using duplicity, because of the names that I see in the backup folders

the following information is helpful:  [https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto) .

alas, I am now looking for a better manual.


I did figure out how to list the backed-up files

duplicity list-current-files file:///mnt/elsewhere/ubuntu-backup-directory/
 
works, but only with the three slashes in the front, or a

cd /mnt/elsewhere/ubuntu-backup-directory ; duplicity list-current-files file://.

this is good.    but I need the manual for the ubuntu-ified version.

1. the GUI "Restore..." button in the Settings is grayed out.  Is there a GUI for this that I could use?

2. I also would prefer to get hourly backups, but this does not seem to be available.

3. can it autostart on boot?

4. can I stop it from splitting the backups into 50MB files?

I should add that I am using 14.10 beta.

regards, /iaw

---

### Post by redrumrogue on 2014-09-17
The backup utility built into ubuntu is called déjà-dup.  If you google that you should find more documentation that could be of use to you.

---

### Post by Bucky Ball on 2014-09-17
*Thread moved to **Ubuntu Development Version**.*

Any and all threads regarding 14.10 should go here for the moment as it is not yet released. Any reason you are using 14.10? Why don't you try a released, supported (until 2019) and stable version like 14.04 LTS if you are not actively testing and helping with hunting down bugs in 14.10 and reporting your discoveries here? 

The behaviour you're getting from backup in 14.10 may not reflect the behaviour it displays in released and supported versions of Ubuntu. 

Good luck. ;)

---

### Post by ivo-welch on 2014-09-17
I wasn't complaining.  I was asking...  deja-dup.  great.  thanks.  time to go read the manuals.

---

