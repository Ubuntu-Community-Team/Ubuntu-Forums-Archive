---
title: "[SOLVED] I want to backup to /var/backups but permission denied"
date: 2008-09-19
forum: Server Platforms
---

### Post by samona on 2008-09-19
How do i make backups to /var/backups.  It is owned by root.  Will i have to change that in order to backup to that file, or do I backup using root?

---

### Post by Friek on 2008-09-19
Change the mode to either 1777 or 777, by issuing  the command 'sudo chmod 777 /var/backups'. After that it should work just fine. I hope you're aware that if you're filesystems get wiped, your backups will be gone as well. If you want to be certain you have good backups, use an external backup device such as a USB disk.

By the way, it may be useful to back up to a different location, as /var/backups is already used to backup essential system files to..

---

### Post by MJN on 2008-09-19
Such open permissions as 777 is usually a very bad idea. If even a low-level account was compromised then this location would be completely open to having malicious files dropped in which could then be a source for future damage/compromise should the whole lot ever be restored (on the same system or another).

You would be much better off keeping the permissions as root only and using sudo to elevate permissions for the backup (and restore). This would also enable you to retain full ownership/permissions for all the backed up files regardless of who owns them.

Mathew

---

### Post by cariboo on 2008-09-20
If you want to backup your system an external drive would be a much safer place to backup your data. Changing permissions in /var could possibly make your system unusable.

> from [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

Several directories are `reserved' in the sense that they must not be used arbitrarily by some new application, since they would conflict with historical and/or local practice. They are:

    /var/backups
    /var/cron
    /var/msgs
    /var/preserve

Jim

---

