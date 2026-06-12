---
title: "Home Directory Permissions Question"
date: 2008-10-08
forum: Server Platforms
---

### Post by trmentry on 2008-10-08
I have a pretty basic install of Hardy 8.04.1 server.  I have 5 users on this system, each with their own home dir.

I have samba installed so that they can map to their home dir to store files/doc, etc.

I have a few other applications on there as well.  

vmware server 2.0, crashplan pro, apache/mysql/php.

That's pretty much it.

The issue that I'm having is something keeps putting my home dir back to 755 when I change it to 700.  It does this at some point hours after I put it back to 700.  I can't figure out which application is doing this.  But it only does it to my dir not anyone else's.  My account is the one in the sudoer's file to be the admin of the system.. the other's aren't.

Anyone have any ideas on how I can find the offending application that have it quit?

Thanks

---

### Post by lykwydchykyn on 2008-10-08
The first place to check is /var/log/syslog.  If it's happening after hours then it's most likely a cron job, so check /var/log/syslog for any entries related to cron:
```

sudo cat /var/log/syslog |grep -i cron

```

You also want to check your crontab and root's crontab with these commands:
```

crontab -l
sudo crontab -l

```

Finally, I'd search cron.daily for any files containing chmod:
```

grep chmod /etc/cron.daily/*

```

See if that turns up anything for you.

---

### Post by trmentry on 2008-10-09
Not a lot in there. 

From 
cat /var/log/syslog |grep -i cron

```

Oct  9 13:10:01 hoth /USR/SBIN/CRON[12239]: (root) CMD (/root/bin/motd > /etc/motd)
Oct  9 13:17:01 hoth /USR/SBIN/CRON[12247]: (root) CMD (   cd / && run-parts --report /etc/cron.hour
ly)
Oct  9 13:20:01 hoth /USR/SBIN/CRON[12252]: (root) CMD (/root/bin/motd > /etc/motd)
Oct  9 13:30:01 hoth /USR/SBIN/CRON[12266]: (root) CMD (/root/bin/motd > /etc/motd)
Oct  9 13:39:01 hoth /USR/SBIN/CRON[12281]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /
var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r
 -0 rm)
Oct  9 13:40:01 hoth /USR/SBIN/CRON[12289]: (root) CMD (/root/bin/motd > /etc/motd)
Oct  9 13:50:01 hoth /USR/SBIN/CRON[12298]: (root) CMD (/root/bin/motd > /etc/motd)

```

the /root/bin/motd is the following:

```

#!/bin/sh
echo
uname -a
echo
uptime
echo
who
echo
date
echo

```

which just mod's the motd so users will see who's on etc.


Nothing much else that I could find.  So I'm guessing some errant part of a program is doing it.  But what throws me off, is just my logon and no one else's.

---

### Post by Iowan on 2008-10-09
Anything in the **/etc/samba/smb.conf** look unusual? I started looking for a thread explaining where "new Samba" put things, but got sidetracked...

---

### Post by trmentry on 2009-02-11
Can someone please help out on getting something together (script) to watch /home and mark the time that the change occurs?  My script foo isn't the greatest.

This is still happening to me and I've grep'ed all the logs and cron stuff and can't find the offending thing that is doing it.

Thanks

---

### Post by trmentry on 2009-02-12
Figured it out... sabnzbd is changing the directory to 755.  Now to figure out why.

---

