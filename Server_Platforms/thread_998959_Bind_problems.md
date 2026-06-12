---
title: "Bind problems"
date: 2008-12-01
forum: Server Platforms
---

### Post by putz3000 on 2008-12-01
First, I apologize for posting about SUSE.  I am a Ubuntu fan (although fairly new to Linux) who inherited a SUSE box at work.  I plan this comming year to replace with Ubuntu Server edition.  Still I have a problem, a Problem that I have yet been able to get even the slightest hint of help from the Suse community.  That has never been my experience here so I am hoping that I can get some Bind hints that I can try to make work on this suse box to get it working again until I can replace it with Ubuntu.  Here is the deal:

I inherited a suse based dns server. Unfortunately it appears to be running I believe on suse 9.2 or 9.3 home edition stripped of gui desktop (so I have been told). Everything had been working just fine for a little over a year and then suddenly it stopped working. I am seeing two problems currently that I do not think are related to each other. The first is that evidently, the Primary was not updating the secondary dns server. The other problem (and most obvious one to fix first) is that this box boots up and appears to be working except that dns (bind) is not doing its job. My only real clue at this time is the warning message on boot that says:

Starting name server Bind9 -warning: /var/run/named/named.pid exists! done


Is this something as simple as removing the named.pid so that when it boots it does not find one in that location or is this a deeper problem? I do not have a lot of linux background - as you can probably tell. Any hints or advice would be appreciated. I can connect to the box through telnet and the network cards lights are all correctly lit so I don't see how the card is being faulty.

---

### Post by putz3000 on 2008-12-01
bump?

---

### Post by hictio on 2008-12-01
You might want to try not deleting the /var/run/named/named.pid file, but renaming it, just to be safe.
If the process is not running, that is, bind is not working, as the user root, or thru sudo, if configured, type on a terminal:

```

mv /var/run/named/named.pid /var/run/named/named.pid.ORIG

```

and then, if possible, reboot the box, or start bind.

---

### Post by putz3000 on 2008-12-02
Thanks for the reply.  I did do the copy and also had no problem deleting the named.pid file and I ran a rcnamed start and everything seems to go ok but if I run a "ps ax", there does not appear to be anything related to named at all. The first time I removed the named.pid and then restarted the service, I rebooted and had the same error I described originally. So this time, I stopped the service, then removed the file then restarted the service but when running "ps ax", just not there.

I took a look at the message log, and here is the bottom of the log file (server name/public ip edited out):

Dec 1 18:09:40 <server name> named[4938]: starting BIND 9.2.3 -u named
Dec 1 18:09:40 <server name> named[4938]: using 1 CPU
Dec 1 18:09:40 <server name> named[4938]: loading configuration from '/etc/named.conf'
Dec 1 18:09:40 <server name> named[4938]: listening on IPv4 interface lo, 127.0.0.1#53
Dec 1 18:09:40 <server name> named[4938]: listening on IPv4 interface eth0, <PUBLIC IP ADDRESS OF SERVER>#53
Dec 1 18:09:40 <server name> named[4938]: command channel listening on 127.0.0.1#953
Dec 1 18:09:40 <server name> named[4938]: command channel listening on ::1#953
Dec 1 18:09:41 <server name> named[4938]: unable to rename log file '/var/log/named_querylog.1' to '/var/log/named_querylog.2': permission denied
Dec 1 18:09:41 <server name> named[4938]: unable to rename log file '/var/log/named_querylog.0' to '/var/log/named_querylog.1': permission denied
Dec 1 18:09:41 <server name> named[4938]: unable to rename log file '/var/log/named_querylog' to '/var/log/named_querylog.0': permission denied


I am guessing this a a bad thing, not a good thing.  It looks to me like I have a permission issue?

---

### Post by hictio on 2008-12-02
It doesn't look good :)
Try this, make a backup of the config first!
Stop the DNS service.
Then, edit it, and remove the entry with the logign directive, save it, and the start the service again.

This is a sample of what the logging bit might look like on the config:

```

logging {
        channel query_logging {
        file "/var/named/data/named_querylog.log"
        versions 3 size 30M;
        print-time yes;
        };

```

It's taken form one of my servers, the path to the actual log file can vary :D

---

### Post by putz3000 on 2008-12-03
It does appear to be a permissions issue regarding the query logging.  What does query logging do anyhow?  My "guess" would be that it logs all of the zone query requests that the server gets, would that be an accurate guess?

Anyhow, I made a copy of the named.conf file then rem'd out (#) all of the query logging lines, saved the file and then restarted the service.  All is happy in happy land now.  So I know what part of the named.conf file is tripping the process.  For now I am working around it, but will probably have to fix the permissions if we re-enable before I get a new system built.

Thank you for your help, it helped point me in the right direction and got the system working again.

---

### Post by NDLunchbox on 2008-12-03
FYI, BIND9 has some finicky permissions issues.  I have two internal DNS servers running on Ubuntu 8.04.1LTS and my slave didn't update correctly.  It ended up being because I gave a full path to where I wanted the Zone Files.  Even though the directory had the right permissions, BIND still kicked out a similar error to yours.  I ended up just letting it use the default (removed the path, only gave a zone file name) and it worked.

Go figure - keep that in mind if you rebuild in Ubuntu and use the APT package.

---

### Post by hictio on 2008-12-03
> **putz3000 said:**
> It does appear to be a permissions issue regarding the query logging.  What does query logging do anyhow?  My "guess" would be that it logs all of the zone query requests that the server gets, would that be an accurate guess?

Anyhow, I made a copy of the named.conf file then rem'd out (#) all of the query logging lines, saved the file and then restarted the service.  All is happy in happy land now.  So I know what part of the named.conf file is tripping the process.  For now I am working around it, but will probably have to fix the permissions if we re-enable before I get a new system built.

Thank you for your help, it helped point me in the right direction and got the system working again.

I'm glad it worked for you.
Now that it works, make those logs start working again, the logs are the admin best friend :) (and the backups, and the firewalls, and ssh, and rsync, and emacs, etc, etc :D )

For what I can tell, named does not have the perms to rotate, that is to create the new log file on that directory.

You can either create a new directory on the '/var/log/' destination, say, '/var/log/dns_logs', and then give it perms to named, so it can create and rotate the logs in there, or, you can create the log file on the '/var/named/' directory structure.

---

