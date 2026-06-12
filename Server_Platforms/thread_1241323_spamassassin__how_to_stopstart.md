---
title: "spamassassin : how to stop/start"
date: 2009-08-15
forum: Server Platforms
---

### Post by cbear on 2009-08-15
I am writing a script that needs to stop spamassassin and then restart.  How to I stop/start the daemon (spamd) ?  I know how to "kill" it using the pid, but I need a way to stop/start in a script where I would not know the pid.

thank you.

---

### Post by jocampo on 2009-08-15
What about using the service as an argument? everything that is running, should have a service, which can be stopped or started at will ...

---

### Post by wojox on 2009-08-15
/etc/init.d

[http://www.cs.bgu.ac.il/~piavka/suse/ch13s04.html](http://www.cs.bgu.ac.il/~piavka/suse/ch13s04.html)

---

### Post by cbear on 2009-08-15
I tried to run

```
spamd stop
```

```
spamd reload
```

no matter what option I use, I get the following:

root@LINUX03:/home/tbegehr# spamd stop
[8218] warn: server socket setup failed, retry 1: spamd: could not create INET socket on 127.0.0.1:783: Address already in use
[8218] warn: server socket setup failed, retry 2: spamd: could not create INET socket on 127.0.0.1:783: Address already in use
[8218] error: spamd: could not create INET socket on 127.0.0.1:783: Address already in use
spamd: could not create INET socket on 127.0.0.1:783: Address already in use

---

### Post by Girya on 2009-08-15
this script works for me if I preface it with sudo and specify the absolute path. 

> #!
/etc/init.d/spamassassin restart


kevin

you might want to install nmap if you don't have it and run: 

> nmap -p 783 localhost


to see what is running on that port

---

### Post by cbear on 2009-08-15
spamassassin is already running on the port..which makes sense.  But I can't figure out why SA won't let it go.

```
root@LINUX03:/home/tbegehr# nmap -p 783 LINUX03
```

Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2009-08-15 22:56 CDT
Interesting ports on LINUX03.hsd1.ca.comcast.net. (127.0.1.1):
PORT    STATE    SERVICE
783/tcp filtered spamassassin

---

