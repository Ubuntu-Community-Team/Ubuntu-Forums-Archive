---
title: "Heartbeat - Windows - Ubuntu"
date: 2010-03-29
forum: Server Platforms
---

### Post by malarie on 2010-03-29
Good day,

I have a Ubuntu Server 9.1 that contains critical information. I have configured backups, and process monitoring with cron, I am notified each time the process  is down,  but  its not 100% complete. If the machine goes down (no power, or stops responding i would like to be notified ASAP. Since this is my only Linux machine, (others are Windows XP, 2003) and i never configured a heartbeat so im not familiar with it,  I'm curious if there is a tool that will do the work.

As I understand it, obviously it needs to be a Windows tool.

Regards,

---

### Post by Vegan on 2010-03-29
One idea is a UPS to keep the server up, then you can monitor it with whatever and send SMS or emails or something to let you know to put another quarter in the power meter.

---

### Post by malarie on 2010-03-29
I have a UPS, the machine will be connected to a UPS.. I weant to monitor its state.. If it hangs, crashed,   shutdown after  a  sustained electrical blackout during the night.  etc..

---

### Post by fang0654 on 2010-03-29
What you need is a server monitoring application.  I am not sure what is available for monitoring under Windows, but under Linux a few options are ZenOSS, Zabbix, and Nagios.

---

### Post by spynappels on 2010-03-29
Nagios runs on a Linux server, but can be accessed through a web browser fromany client. I used a Nagios server for a very similar setup for a while and it worked very well, I had it email me if there were problems.

It is also highly configurable...

---

