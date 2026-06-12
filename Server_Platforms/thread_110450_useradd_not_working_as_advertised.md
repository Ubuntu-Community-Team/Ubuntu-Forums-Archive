---
title: "useradd not working as advertised?"
date: 2005-12-30
forum: Server Platforms
---

### Post by mrt on 2005-12-30
```
mike@linus:~$ sudo -s
Password:
root@linus:~# useradd -D
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=
SKEL=/etc/skel
root@linus:~# useradd test
root@linus:~# cd /home
root@linus:/home# ls
mike
root@linus:/home#

```
It's my understanding that if *useradd* is used without options, it should use the default values as defined by "*useradd -D*".  Yet, the home dir was not created and the /etc/skel files were not copied over.

I know about adduser, I'd just like to know what's happening here.

---

### Post by mrt on 2005-12-30
oh, it looks like I need the -m option, sorry

---

