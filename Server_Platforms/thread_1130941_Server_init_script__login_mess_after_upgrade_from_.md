---
title: "Server: init script / login mess after upgrade from 6.06 lts to 8.04 lts"
date: 2009-04-20
forum: Server Platforms
---

### Post by scachi on 2009-04-20
Hello,

the upgrade did work fine (update of openldap hung, killing this one update script did help - I removed it and reinstalled it later after a reboot) and almost everything is working.

Only something with some init scripts seems to be wrong.
The last one before the "faxmail1 login: " prompt is the kernel log daemon.

After that the login prompt is shown but there are still init script starting up after that - printing output like the script before the prompt.

The init script after the login prompt (in this order):
-isdn capi
-sshd
-cupsd
-ppdev parralel port driver
-slapd
-spamd
-courier.. (.. like authdaemon,...)
-isdn service
-atd
-rc.local

So it looks really garbled. Any ideas what is wrong here ?


(.. hope this is the right place to ask - as it is a server lts..)

---

### Post by cdenley on 2009-04-20
What version of upstart do you have?
```

dpkg -l upstart

```
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/65230](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/65230)
> 
upstart (0.3.9-2) hardy; urgency=low

  * Start the getty on tty1 after the rc script has stopped rather then
    at the same time it starts to avoid overwriting by console messages.
    tty2..6 will still be active if you want an early login. LP: #65230.
  * If the recovery menu is available start that instead of sulogin when
    entering single-user-mode.

 -- Scott James Remnant <scott@ubuntu.com> Fri, 11 Apr 2008 13:38:50 +0100


---

### Post by scachi on 2009-04-20
Well, 
```
dpkg -l upstart
```
tells me that I have version 0.3.9-2.

I don't know if the tried to fix this with the patch in this [comment]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/65230/comments/18").

My /etc/event.d/rc2 file does not have this patch applied as there still is the line 
```
start on runlevel 2
```
instead of
```
start on stopped rc2
```
in it.

Do I use a wrong mirror or something like that ?

---

### Post by cdenley on 2009-04-20
The "fix" in that comment is a hack, not the fix that was used in the package in the repos. I'm guessing the file that changed is:

/etc/event.d/tty1
```

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty1

```

---

### Post by scachi on 2009-04-21
Is the above the complete content of the /etc/event.d/tty1 file of this version ?

Mine is almost the same but has additional lines add the bottom.
```
start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5
```

I have removed those (added a '#') and everything looks fine now on init.

---

