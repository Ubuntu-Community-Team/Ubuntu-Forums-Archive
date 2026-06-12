---
title: "Syslog-ng archive, email, and remove log file automatically"
date: 2012-04-30
forum: Server Platforms
---

### Post by derricks on 2012-04-30
System Info
 OS: Ubuntu Linux 11.10
 Kernel & CPU : Linux 3.0.0-17-server on x86_64
 Syslog : Syslog-NG 3.2.4

I'm using Syslog-NG to collect logged events from my Cisco equipment. I'm looking for a way to keep logs organized and to also e-mail me copies of the logs each night.

So right now what I've done is created the below bash script to make a copy of the original log file with a date appended to it. It then will erase the contents of the original log file and restart the syslog service.

> 
#!/bin/bash
/etc/init.d/syslog-ng stop
cp /var/log/cisco.log /var/log/ciscologs/`date +%d%b%Y`_cisco.log
cat /dev/null > /var/log/cisco.log
/etc/init.d/syslog-ng start


I have a cron job set to run this script each night. But after it creates the copy of the log file, I would like it to e-mail me the copy of the log file. I would also like a way to remove the copied log file automatically after each month from the ciscologs folder.

Can someone provide me with knowledge to get this working?

---

### Post by Jonathan L on 2012-04-30
Hi Derricks

> 
I have a cron job set to run this script each night. But after it creates the copy of the log file, I would like it to e-mail me the copy of the log file. I would also like a way to remove the copied log file automatically after each month from the ciscologs folder

I'd recommend logrotate, which is already designed to do these things like the rotation and the mailing.

[http://manpages.ubuntu.com/manpages/oneiric/man8/logrotate.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/logrotate.8.html)

Hope that's helpful

Kind regards,
Jonathan

---

### Post by derricks on 2012-04-30
Thanks for the info! I think I got it setup correctly but I might be missing a package for the mailing bit. I get the following error:

> error: mail command failed...

Is there something I need to install?

---

