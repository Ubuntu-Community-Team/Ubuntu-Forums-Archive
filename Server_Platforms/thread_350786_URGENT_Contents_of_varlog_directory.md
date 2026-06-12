---
title: "URGENT: Contents of /var/log/ directory"
date: 2007-02-01
forum: Server Platforms
---

### Post by sindows on 2007-02-01
Hi Guys,

My server was hacked today but a turkish cracker, he got in through some insecure php code on my box. On his departure he deleted the /var/log directory.

This is who did it (i along with many other people have been hacked).

[http://www.zone-h.org/component/option,com_attacks/Itemid,43/filter_defacer,iskorpitx/](http://www.zone-h.org/component/option,com_attacks/Itemid,43/filter_defacer,iskorpitx/)

I am trying to re-create all the files and directorys in the /var/log directory so that everything can start loggin as it normally did before.

Could someone please advise all of the files/directorys in the /var/log directory on Ubuntu server Drapper Drake.

Cheers in advance.

---

### Post by almostlinux on 2007-02-01
It depends on what apps you have installed. Here's my list:
```

/var/log$ ls -ltr | grep dr
drwxr-xr-x 2 root     root       4096 2006-07-27 23:04 unattended-upgrades
drwxr-xr-x 2 root     root       4096 2006-10-12 04:03 dist-upgrade
drwxr-xr-x 2 root     root       4096 2006-10-25 18:56 fsck
drwxr-xr-x 2 root     root       4096 2006-12-20 16:15 installer
drwxr-sr-x 2 news     news       4096 2006-12-20 17:38 news
drwxr-xr-x 2 root     root       4096 2006-12-22 14:41 cups
drwxr-xr-x 2 ntp      ntp        4096 2007-01-01 13:54 ntpstats
drwxr-x--- 2 root     adm        4096 2007-01-07 08:27 samba
drwxr-xr-x 2 root     root       4096 2007-01-20 08:26 proftpd
drwxr-xr-x 2 www-data www-data   4096 2007-01-24 19:01 lighttpd
drwxr-xr-x 2 root     root       4096 2007-01-29 11:16 gdm
drwxr-xr-x 2 root     root       4096 2007-01-29 11:33 apache2
drwxr-s--- 2 mysql    adm        4096 2007-02-01 08:27 mysql
drwxr-xr-x 2 root     root       4096 2007-02-01 13:47 zope2.9
```

---

### Post by MJN on 2007-02-01
Do you really need to create everything manually? I would expect that as services start they will create a logfile if one doesn't already exist (just like they do everytime logrotate goes through its motions).
 
For any services that can't do this, they'll tell you!
 
On second thoughts, given you've been hacked the **least** of your worries is restoring your logfiles. Get that machine stripped and rebuilt now - who knows what else he's left behind that you don't know about?
 
Mathew

---

### Post by sindows on 2007-02-01
> **MJN said:**
> Do you really need to create everything manually? I would expect that as services start they will create a logfile if one doesn't already exist (just like they do everytime logrotate goes through its motions).


I would agree, but nothing has bitched (however i havnt rebooted the box as its in the DC and i dont feel like going and fixing it if it doesnt come back up).
 
> **MJN said:**
> 

For any services that can't do this, they'll tell you!
 
On second thoughts, given you've been hacked the **least** of your worries is restoring your logfiles. Get that machine stripped and rebuilt now - who knows what else he's left behind that you don't know about?
 
Mathew

I am planning to re-install sometime this weekend, i must say after further investigation, the server wasnt hacked as such, they did not get in using a username/password, they simply used a php injection attack.

However after i spent half the night working on most of the sites, i have cleaned most of it up now.

However the only weird thing is i cant su - to different users. Could this be because there is no sudo log file?

---

### Post by MJN on 2007-02-01
> **sindows said:**
> I would agree, but nothing has bitched
 
You have no way of knowing that.

> I am planning to re-install sometime this weekend, i must say after further investigation, the server wasnt hacked as such, they did not get in using a username/password, they simply used a php injection attack.

And so how did this remove root-owned files/directories?

Just rebuild the box - it'd be quicker than trying than any cleanup operation. (you have backups right?)

Mathew

---

### Post by sindows on 2007-02-02
> **MJN said:**
> You have no way of knowing that.
Just rebuild the box - it'd be quicker than trying than any cleanup operation. (you have backups right?)


Yes to backups of the db and site content, no to everything else.

I will keep you posted, thanks for the help!

---

