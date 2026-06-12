---
title: "Logs and stuff"
date: 2007-06-06
forum: Server Platforms
---

### Post by Geir102 on 2007-06-06
Hi im new to linux. And i have sett up a server, just to learn. Im running SSH for remote login. Can any one give my some hints on how to see if people are trying to/allredy have borken in? What logs to read and what to look for. And if there is any exploits i have to look out for

---

### Post by rich.bradshaw on 2007-06-06
cat /var/logs/auth.log

will tell you who's logging in and what they are doing.

To avoid people guessing password

sudo apt-get install fail2ban

will block people who get pass wrong 5 times for 5 mins. This prevents guessing the password.

There is no need to disallow root logins, as there is no root account in Ubuntu.

Changing the port from 22 to something else can be done in sshd.conf, but I wouldn't bother, just use fail2ban.

---

### Post by Geir102 on 2007-06-06
Oka tanks i have read that i have to disable X11 in ssh i this nessesary?

---

### Post by PetePete on 2007-06-06
only if you dont plan on using X fowarding.

comes from the principle of 'if you dont use it, disable it' .... or something like that!

---

### Post by Geir102 on 2007-06-07
OK idont. What is X forwarding?

---

