---
title: "Wierd connections"
date: 2010-08-24
forum: Server Platforms
---

### Post by gzipper on 2010-08-24
Hello.
There's something wrong with my server since it has maybe 200+ connections to an adress 192.168.1.:microsoft-ds. Entries look like this:
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        1      0 192.168.1.96:51885      192.168.1.:microsoft-ds CLOSE_WAIT
tcp        1      0 192.168.1.96:51537      192.168.1.:microsoft-ds CLOSE_WAIT
tcp        1      0 192.168.1.96:48573      192.168.1.:microsoft-ds CLOSE_WAIT
tcp        1      0 192.168.1.96:40050      192.168.1.:microsoft-ds CLOSE_WAIT
tcp        1      0 192.168.1.96:36200      192.168.1.:microsoft-ds CLOSE_WAIT
tcp        1      0 192.168.1.96:36208      192.168.1.:microsoft-ds CLOSE_WAIT
tcp        1      0 192.168.1.96:42214      192.168.1.:microsoft-ds CLOSE_WAIT

```
Wondering what may cause this. Is there any way to check which application that makes these connections? There are also IPv6 connections from 192.168.1. though they come and go. Something's wrong since 192.168.1. shouldn't be valid.
Using ubuntu Server 10.04.1 with:
OpenSSH
Apache
Samba
Tomcat6
MySQL

---

### Post by gzipper on 2010-08-24
It's samba playing up.

---

### Post by cdenley on 2010-08-24
This command is a little more informative, for future reference.
```

sudo netstat -tnp

```

---

