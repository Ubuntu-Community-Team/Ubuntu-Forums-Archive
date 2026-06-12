---
title: "lucid upstart debugging"
date: 2011-04-27
forum: Server Platforms
---

### Post by fedoraboy on 2011-04-27
I am desperately in search of a clue.

I have a lucid server (10.04.2 LTS) that was updated from a 8.04 LTS server some time ago.  After the update, it worked fine.  At some point in time I began having upstart issues at bootup.  (God only knows when... this system is always up, so reboots are few and far between.  It's likely the update happened weeks before a reboot.)

The symptoms don't even make sense to me.  The system acts differently on every bootup.   Some boots are fine.  Some boots fail to start one or more daemons.  (And by one or more... there are sometimes as many as 20 daemons that don't seem to get started.)

I am assuming there is some oddball race condition.  I am comfortable with sysV startup scripts, but upstart is a new beast to me.  I've been trying to read/digest the info on upstart.ubuntu.com... but have yet to have a eureka moment.  Logs are of very little use -- rsyslog is extremely likely to be one of the non-starting daemons.  

I have tried multiple things I've found in various threads online:
* added "--verbose" to init in /etc/default/grub (and while this generates lots of stuff... none of it makes it to syslog)
* commented out "console output" in /etc/init/*.conf files (supposedly there's a race condition with /dev/console and upstart)
* modified /etc/init/rc-sysinit.conf to start on "( filesystem and started rsyslog and  net-device-up IFACE=lo )" 

I'm stumped and just not upstart knowledgeable enough to debug this.  I'm not entirely sure, when it comes up in it's "almost up" state -- where to go from there.  If I were confident this was a bug... I'd open a bug report... but I don't want to open a vague bug report that sends the maintainer spinning in circles.

---

### Post by Vegan on 2011-04-27
I had issues with 10.04 so when 10.10 surfaced I formatted the disk and installed it fresh and issues disappeared.

I was experiencing file system errors. Motivated me to become very aggressive to backup the machine.

Today I use backups to the backup I am so paranoid.

---

### Post by fedoraboy on 2011-04-27
yeah, the thought has occurred to me... but the entire reason I switched to ubuntu was the LTS release cycle.  If I reload, it will probably be to CentOS.

---

