---
title: "log files"
date: 2008-08-19
forum: Server Platforms
---

### Post by johan.alfa on 2008-08-19
Hello all,

Could not find this ifo.
I have ubuntu server 8.04 and would like to know a bit more about the log files.

Are they secure in a sense that they all are limited in size?
I see some off them get zipped after some time.

Any comments?

greetins,

---

### Post by MJN on 2008-08-19
They are not limited in size - rather they are rotated periodically (time based) for management purposes (large logs become unwieldy to use amongst other reasons). To minimise disk space older logs are are also compressed as you've seen.
 
Logging can be done in many ways - usually either directly by the applications themselves, or via a centralised logging utility such as 'syslog'. In the former case the log rotations are usually performed by the logrotate tool, whereas syslog looks after its own in a similar way.
 
Google for some of these terms and you'll soon pick up what they're all about.
 
Mathew

---

### Post by johan.alfa on 2008-08-19
Hello,

I understand what you say and I already googled a lot but would like to know if that rotation and compression system is eternal or does it stop after x number of files. How much disk space could it use at maximum?

greetings,

---

### Post by MJN on 2008-08-19
All the parameters are configurable - for logrotate these settings are in /etc/logrotate.conf and /etc/logrotate.d/* (there may be an additional /logrotate/ folder in those paths - I'm not at my machine right now), whereas for syslog the settings are in /etc/syslog.conf.
 
Applications whose logs are rotated by logrotate are free to define there own parameters (stored in files in /etc/logrotate.d/) about how often to rotate files, when to compress them, how long to keep them, etc.
 
See the man pages for logrotate, logrotate.conf, syslog and syslog.conf for further details.
 
For what it's worth however, it is unlikely that the default behaviour is to keep logs indefinitely (most will likely keep, say, a month's worth).
 
Mathew

---

