---
title: "Server Information via Web"
date: 2010-09-28
forum: Server Platforms
---

### Post by Xi0N on 2010-09-28
Hi!
Im currently running an x86_64 server for virtualization purposes.
The thing is that sometimes, i connect via ssh and run htop for checking the server's load and stuff, but i was wondering if there is some kind of software that could show me the server's overall info via web:
Running processess, load, disk space, hardware info... etc..... but all via web.....

Thanks!

---

### Post by linux-hack on 2010-09-28
Yes nagios :D

---

### Post by Xi0N on 2010-09-28
Isn't there anything else more specialized for monitoring the server locally?
I mean: I use nagios, and actually, one of the virtual machines in this server has nagios + cacti installed and running, monitoring 100+ services from my corporate network, but i was thinking about something more stand-alone.... something dedicated in the main server.... something that does not have to be configured in the way nagios has to.... 
I mean: In nagios, i would have to configure a service for the disks, another for the processess.... and how to get the system's info? Get the kernel version, apt updates available (this, i already monitor it from nagios actually) but i was thinking about something more lika a system's dashboard.... a web based control panel with more general info......
Thanks for thie ideda btw :)

---

### Post by linux-hack on 2010-09-28
[http://news.softpedia.com/news/Monitoring-a-Linux-System-With-X11-Console-Web-Based-Tools-51678.shtml](http://news.softpedia.com/news/Monitoring-a-Linux-System-With-X11-Console-Web-Based-Tools-51678.shtml)

[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by Xi0N on 2010-09-28
phpsysinfo will do the trick....

Thanks!!

---

### Post by linux-hack on 2010-09-28
No problem ;). If your problem is solved just put a SOLVED in the title please.

---

### Post by Xi0N on 2010-09-28
Would you mind it if i leave it unsolved for a couple of hours? Just in case someone else has some more ideas? :)
If this cannot be, i will happily close the post...... ;)
Thanks!

---

### Post by linux-hack on 2010-09-28
No problem for me :D :P ...

---

