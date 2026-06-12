---
title: "[SOLVED] mysql"
date: 2008-03-15
forum: Server Platforms
---

### Post by loldrup on 2008-03-15
Hi
I've lost root access to mysql and I have failed to reset the password*. Is there a way to wipe the slate clean and start all over? I have tried reinstalling mysql-server but it doesn't change anything.
I'm using Ubuntu gutsy gibbon and mysql-server 5.0.45


* I followed this guide:
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix)

---

### Post by faulkes on 2008-03-15
> **loldrup said:**
> Hi
I've lost root access to mysql and I have failed to reset the password*. Is there a way to wipe the slate clean and start all over? I have tried reinstalling mysql-server but it doesn't change anything.
I'm using Ubuntu gutsy gibbon and mysql-server 5.0.45


* I followed this guide:
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix)

you can remove mysql with

```

sudo apt-get remove mysql-server
sudo dpkg -P mysql-server

```

and then re-install with

```

sudo apt-get install mysql-server

```

Faulkes

---

### Post by mmichalik on 2008-03-15
> **ung/xunil said:**
> Debian has its tricks for this things. Since you are using Ubuntu 6.06 LTS (dapper) you should try:
```
sudo /etc/init.d/mysql reset-password
```
That should work until Ubuntu 7.04 Feisty (dapper-edgy-feisty).

Starting with Ubuntu 7.10 Gutsy, resetting the mysql password can/should be done via dpkg (it was included there so the root mysql password is set on install and to never be left unset):
```
sudo dpkg-reconfigure mysql-server-5.0
```

These two will help you reset your password, if you haven't already re-installed.

---

### Post by loldrup on 2008-03-15
> **mmichalik said:**
> sudo dpkg-reconfigure mysql-server-5.0

Yes!! That was the code that solved my problems. Thank you :)

---

### Post by mmichalik on 2008-03-15
no problem.

i came across this by accident a few days ago and it's worth it's weight in gold!

thanks to ung/xunil for posting it.

---

