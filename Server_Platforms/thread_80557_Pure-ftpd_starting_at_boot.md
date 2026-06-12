---
title: "Pure-ftpd starting at boot?"
date: 2005-10-22
forum: Server Platforms
---

### Post by logophobia on 2005-10-22
I installed pure-ftp to share some things with my friends but I have to start it manually everytime I boot my pc w/ sudo pure-ftpd. It's running as service but I can't connect to it (with ftp localhost) unless I start it manually. 

How can I auto-start it when my pc boots?

---

### Post by tcort on 2005-10-22
Try this:
$ sudo update-rc.d pure-ftpd defaults

---

### Post by logophobia on 2005-10-22
it says:
 System startup links for /etc/init.d/pure-ftpd already exist.

how else can I check what's wrong with my installation?

---

### Post by TomB on 2005-10-23
Yes I've been having the same problem with pure-ftpd :(

---

### Post by ubernoob on 2005-10-23
Same problem here.

```
user@localhost:~$ sudo update-rc.d pure-ftpd-mysql defaults
 System startup links for /etc/init.d/pure-ftpd-mysql already exist.
```

This doesn't work either. It gives no output. Maybe the problem is in this script?:

```
user@localhost:~$ sudo /etc/init.d/pure-ftpd-mysql start
user@localhost:~$ ps -A | grep pure
user@localhost:~$

```

---

### Post by logophobia on 2005-10-23
Well, it starts here with sudo pure-ftpd &. That works, but the problem is that there's a script in init.d that `should` start the server when my pc boots but doesn't. There's a pure-ftpd service running but it doesn't seem to be doing anything.

---

### Post by ubernoob on 2005-10-23
Open /etc/default/pure-ftpd-common

Change STANDALONE_OR_INETD to standalone:
STANDALONE_OR_INETD=standalone

After that you should be able to start/stop pure-ftpd with init.d:

sudo /etc/init.d/pure-ftpd start

Or with mysql:

sudo /etc/init.d/pure-ftpd-mysql start

---

### Post by logophobia on 2005-10-23
It's working. Thnx.

---

### Post by TomB on 2005-10-23
Works fine, cheers :)

---

