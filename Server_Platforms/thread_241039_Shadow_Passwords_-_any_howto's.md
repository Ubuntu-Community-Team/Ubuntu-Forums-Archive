---
title: "Shadow Passwords - any howto's ???"
date: 2006-08-21
forum: Server Platforms
---

### Post by hawkbane on 2006-08-21
Does anybody know of any good howto's out there on shadowing your passwords that work with Ubuntu Dapper?  I would like to harden my system up a bit by not only shadowing my passwords but also applying a MD5 hash to them.  I also do not want to hose my machine over.  Anybody got any links out there?

Thanx guys!
~Hawkbane

---

### Post by sysops on 2006-08-22
dapper uses the shadow file by default (which new distro doesn't?) .. a quick check confirms this.

$ echo $USERNAME
user

$ sudo cat /etc/passwd | grep "^$USERNAME\:"
user:x:1000:1000:user,,,:/home/user:/bin/bash

$ sudo cat /etc/shadow | grep "^$USERNAME\:"
user:$1$zhSPxVb2$xWaaOWWTE.QQsCmZrzdbq1:13323:0:99999:7:::

---

