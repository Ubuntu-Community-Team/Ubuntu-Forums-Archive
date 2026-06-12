---
title: "mysql server remote connection problems"
date: 2005-02-28
forum: Server Platforms
---

### Post by Muffen on 2005-02-28
Hi!

I'm running Ubuntu with KDE and have installed and are running apache, php4 and mysql. Everything works perfectly when I connect to mysql using localhost, but for some reason I can't connect to mysql from another host. I have set privileges to Y and host to % on the user I'm using, but it still doesn't work, even when I try to connect as root from another host. Is there anything I have to do in the settings for Ubuntu or is there a integrated firewall or something I have to configure to be able to open port 3306 and allow remote hosts to connect to my mysql-server?

---

### Post by alastair on 2005-02-28
Check :

/etc/mysql/my.cnf

and remove the "skip-networking" part.

Also - get in the habit of reading the docs installed under /usr/share/doc/<program>

They always seem to have a "README.Debian" that explains some basic stuff.

---

### Post by Muffen on 2005-03-01
Thanks a lot, it works now! As I'm a newbie to linux and ubuntu I didn't know about that /usr/share/doc/ but I do now, and will check there in the future before I ask new questions on this forum! Thanks again!

---

### Post by byenary on 2006-12-26
How do you do this in a newe version, cause the skip networking is gone...

---

### Post by Brazen on 2006-12-26
> **byenary said:**
> How do you do this in a newe version, cause the skip networking is gone...

comment out the "bind-address" line.

---

### Post by rotorboy on 2007-01-16
Thanks for the solution!

So far loving Ubuntu but still lots to learn!

---

### Post by sysctl on 2007-03-25
I have removed 'bind-address' line, made sure to restart mysqld (it listens to 3306 now), added 'mysqld: ALL' to /etc/hosts.allow, configured my NAT properly (my SSH works, MySQL has similar configuration) and I still can't connect from remote host:
```

host$ telnet xx.xx.xx.xx 3306
Trying xx.xx.xx.xx...
telnet: connect to address xx.xx.xx.xx: Connection refused

```
Any further clues?

---

### Post by jaakan on 2007-05-17
in my case the root password has not been set yet.

if remote access disabled if the mysql root password is not set yet?

I'm in the process of rebuilding a system from the ground up along with my other work.

---

