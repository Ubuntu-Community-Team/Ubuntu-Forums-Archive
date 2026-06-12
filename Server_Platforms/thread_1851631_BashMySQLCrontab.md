---
title: "Bash/MySQL/Crontab"
date: 2011-09-28
forum: Server Platforms
---

### Post by Dori922 on 2011-09-28
hey!

Ive written a script thats gets a username and password from a mysql database, then uses those to create and chroot a new user account before sending the date to a log file.

the script:

[http://pastebin.com/7bX3SYDM](http://pastebin.com/7bX3SYDM)

It works fine when i run it "sudo bash addclients.sh" but when i add it to the crontab via:

1.  sudo crontab -u root -e
2. 55 * * * * /home/trofnan4/addclients.sh

the new users in the database arnt added to the server :( 

log says: [http://pastebin.com/1HHsn44H](http://pastebin.com/1HHsn44H)

The time stamps dont make sense to me because crontab should only start 55minutes past every hour.. :s I dont know what the error is refaring to either since the code works when executed from the commandline without cron....(im using 10.04)

---

### Post by papibe on 2011-09-28
By any chance have you set a password for root?

Regards.

---

### Post by Dori922 on 2011-09-28
no :s but wouldents sudo crontab work around that? if not is there anyway to set up a sudo crontab without having to put in my password everytime or opening up root?

---

### Post by papibe on 2011-09-28
I was going to suggest that if so, then may be the root's password was expired.

Sometimes checking this other log shows more clues:
```
/var/log/auth.log
```
Hope it helps,
Regards.

---

### Post by Dori922 on 2011-09-28
Its company policy to leave root login disabled.. :(

Is there a way to configure this cronjob with a sudouser instead of root?

---

### Post by brettg on 2011-09-28
To have a script run as root put it in the system crontab;

sudo vi /etc/crontab

If you want the script to run as another user you can set that there too.

eg, to run as user backup, do something like this;

0 0 1 * *	backup  /store/scripts/mmbackup >> /dev/null 2>&1

---

