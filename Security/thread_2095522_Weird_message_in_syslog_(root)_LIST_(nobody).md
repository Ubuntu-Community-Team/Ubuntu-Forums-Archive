---
title: "Weird message in syslog: (root) LIST (nobody)"
date: 2012-12-17
forum: Security
---

### Post by cogset on 2012-12-17
I've seen this weird message in syslog:

```
Dec 16 13:28:46 ubuntu-desktop /usr/bin/crontab[20278]: (root) LIST (nobody)
```that (nobody) looked out of context,so I've examined other logs and found that it matches time-wise exactly this event:

> Dec 16 13:28:46 ubuntu-desktop sudo:   ubuntu : TTY=pts/10 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/sbin/chkrootkit
which I can attribute to myself launching (as root) the rkhunter --update command,if memory serves:so what was going on exactly ?

Both rkhunter and chrootkit report no issues and nmap doesn't find any unusual ports open,auth.log did not show other users logged and  besides ssh is not installed as I don't need it.
So what does that (nobody) stand for ?

---

### Post by Soul-Sing on 2012-12-17
I am on lubuntu (now) It has to do with the /etc/lightdm/'custom users'
or in ubuntu gnome /etc/gdm/'custum users'
There are user1,user2 and nobody in this file.
Maybe disabling guestaccounts will solve this for ya.

---

### Post by chadk5utc on 2012-12-17
In many Unix variants, "nobody" is the conventional name of a user account which owns no files, is in no privileged groups, and has no abilities except those which every other user has.

It is common to run daemons as nobody, especially servers, in order to limit the damage that could be done by a malicious user who gained control of them.

---

### Post by cogset on 2012-12-18
So,keeping in mind that this is not a server but  just a home computer with a single user account (mine,obviously) we could chalk that up to  the system performing some maintenance task or routine check ?

---

