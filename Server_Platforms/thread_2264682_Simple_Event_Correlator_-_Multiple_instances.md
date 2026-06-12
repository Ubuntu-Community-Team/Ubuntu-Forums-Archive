---
title: "Simple Event Correlator - Multiple instances"
date: 2015-02-09
forum: Server Platforms
---

### Post by djdiper on 2015-02-09
Hi everybody :)

Im hopeing that somebody out here have some tips and clues for me...

I've installed SEC into my system, and have setup the config files. I have successfully been able to watch over a logfile and print the results of the expected pattern. 
But, I want to have multiple instances of SEC running.. Why, well, beq then I can have separate logfiles, pid-files and config for each logfile I want SEC to check. That makes it alot easier when you are creating context's and rules when you can followup in seperate logfiles. Much more efficient. 

Here is my Dilemma:
in /etc/default/sec (for RedHat/CentOS this is /etc/sysconfig/sec), I want to add more DAEMON_ARGS to the file:
```
#Defaults for sec
RUN_DAEMON="yes"
DAEMON_ARGS="-conf=/etc/sec/sec.fail2ban.conf -input=/var/log/fail2ban.log -pid=/var/run/sec.fail2ban.pid -detach -debug=6 -syslog=daemon -log=/var/log/sec.fail2ban.log"

```

In CentOS, this can easy be achived by adding more "ARGS" to the line, like this:
```

SEC_ARGS[0]="-detach -conf=/etc/sec/sys/*.sec -input=/var/log/messages -log=/var/log/sec -intevents -pid=/var/run/sec.sys.pid"
SEC_ARGS[1]="-detach -conf=/etc/sec/mail/*.sec -input=/var/log/messages -log=/var/log/sec -intevents -pid=/var/run/sec.mail.pid"

```

Why doesn't this work with Ubuntu server? 
I have tried multiple solutions and the end result is that the startup script says: "file not found" when added 
```
DAEMON_ARGS[0]="-conf=xxxxxx
DAEMON_ARGS[1]="-conf=xxxxx
``` and so on. 

I have also tryed varibles like this:
```
DAEMON_ARGS_1
DAEMON_ARGS_[1]
DAEMON_ARGS_sometext
```
...but none of them are successfull.. 

Is there anyone out here that have set this up successfully and wouldn't mind giving me the recipe? 

Some details about the OS:


Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

SEC (Simple Event Correlator) 2.7.5



Br
./ Michael

---

### Post by rv18 on 2015-02-21
hi Michael,
I have never used sec on Ubuntu 14.04 production server, and also don't have a Ubuntu laptop currently at hand to have a closer look.
Nevertheless, SEC allows to configure a workaround for this problem that works on any distribution -- you can start one master instance from init script which in turn spawns several child processes. Suppose you have the following SEC configuration file called parent.conf with just one rule:

type=Single 
ptype=RegExp 
pattern=^(?:SEC_STARTUP|SEC_RESTART)$ 
context=SEC_INTERNAL_EVENT 
desc=start sec child processes on startup and on SIGHUP
action=shellcmd /usr/bin/sec --conf=/etc/sec/*.sec --input=/var/log/log1.log --pid=/var/run/sec1.pid --log=/var/log/sec1.log; shellcmd /usr/bin/sec --conf=/etc/sec/*.sec --input=/var/log/log2.log --pid=/var/run/sec2.pid --log=/var/log/sec2.log


If you start the following sec process from init script

/usr/bin/sec --conf=/home/risto/parent.conf --intevents --detach

the process will have no input log file to monitor, but it will rather start two child processes:

/usr/bin/sec --conf=/etc/sec/*.sec --input=/var/log/log1.log --pid=/var/run/sec1.pid --log=/var/log/sec1.log 
/usr/bin/sec --conf=/etc/sec/*.sec --input=/var/log/log2.log --pid=/var/run/sec2.pid --log=/var/log/sec2.log

When you send SIGTERM to master process, it will take down child processes with SIGTERM. The same happens when you send SIGHUP to master, but in that case two new child processes are spawned.

Hope this helps,
risto

---

### Post by djdiper on 2015-03-31
Hi risto! 

Hmm, this I hadn't considered.. Nice tip! :) 

Might be some problems though, since I'm using the Action part, to pipe to a SMS script I have to alert me when there is problems.
But I will try this out and see how I can config this into place! 

Thanks!

Br
Michael

---

