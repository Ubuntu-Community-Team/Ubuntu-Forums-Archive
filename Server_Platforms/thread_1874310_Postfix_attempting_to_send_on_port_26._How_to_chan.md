---
title: "Postfix attempting to send on port 26. How to change it to send on 25?"
date: 2011-11-02
forum: Server Platforms
---

### Post by Achetar on 2011-11-02
I'm attempting to fix a broken mail system on an Ubuntu Server so that our PHP mail() function will work. (because thats all we use this for). I've been trying to fix it for almost two weeks now and cannot figure out what the cause of the problem is.

Every mail that attempts to get sent times out. Every mail is also attempting to be sent to port 26. I've already purged and re-installed postfix in an attempt to fix this, but it did not succeed. A sample of  the error:

```

Nov  2 08:38:22 truwow postfix/smtp[28979]: connect to alt3.gmail-smtp-in.l.google.com[209.85.227.26]:26: Connection timed out

```

It doesn't matter which service I try to send to (gmail, hotmail, etc), they all time out. In addition, they all try to go to port 26. I can telnet in to port 25 of all of the services from the server, so the port is not blocked.

What's causing it to attempt to send on port 26 and how can I change it so that its sending on port 25?

Repost of [http://ubuntuforums.org/showthread.php?p=11418146#post11418146](http://ubuntuforums.org/showthread.php?p=11418146#post11418146) because I posted in the wrong section.

---

### Post by vasile002 on 2011-11-03
did you try /etc/services?
```

root@izghitu:~# cat /etc/services |grep smtp
smtp            25/tcp          mail
ssmtp           465/tcp         smtps           # SMTP over SSL

```

---

### Post by Achetar on 2011-11-03
```
smtp            26/tcp          mail
ssmtp           465/tcp         smtps           # SMTP over SSL

```

I guess that would be the problem, eh?

EDIT: Now how do I change that? Google isn't pulling anything up.

---

### Post by Achetar on 2011-11-03
Bump with some more info:

For some reason postfix is running on port 26 instead of 25. Port 25 is not in use and hasn't been as far as I can tell.

```
Starting Nmap 5.00 ( http://nmap.org ) at 2011-11-03 16:45 CDT
Interesting ports on localhost.localdomain (127.0.0.1):
Not shown: 992 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
26/tcp   open  rsftp
80/tcp   open  http
443/tcp  open  https
3306/tcp open  mysql
6667/tcp open  irc
7001/tcp open  afs3-callback
9418/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.42 seconds

```

If I /etc/init.d/postfix stop:

```
Starting Nmap 5.00 ( http://nmap.org ) at 2011-11-03 16:46 CDT
Interesting ports on localhost.localdomain (127.0.0.1):
Not shown: 993 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
443/tcp  open  https
3306/tcp open  mysql
6667/tcp open  irc
7001/tcp open  afs3-callback
9418/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.38 seconds
```

Any clues? The problem (as far as I can tell) is that postfix is binding to the wrong port. In all of my searching I can't find anything that says there is a configuration option for that.

---

### Post by jmacgowan on 2011-11-04
Edit your /etc/services file and change

```
smtp            **26/tcp**          mail
```

to

```
smtp            **25/tcp**          mail
```

then restart postfix.

Postfix's master.cf file references /etc/services to figure out what port it should run smtp on.  You could actually hard code postfix to listen on port 25 in your master.cf if you want, but I wouldn't bother.

---

### Post by Achetar on 2011-11-04
> **jmacgowan said:**
> Edit your /etc/services file and change

```
smtp            **26/tcp**          mail
```

to

```
smtp            **25/tcp**          mail
```

then restart postfix.

Postfix's master.cf file references /etc/services to figure out what port it should run smtp on.  You could actually hard code postfix to listen on port 25 in your master.cf if you want, but I wouldn't bother.
Thanks! Worked perfectly.

---

