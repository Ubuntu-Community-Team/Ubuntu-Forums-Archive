---
title: "Apache stops serving"
date: 2010-01-28
forum: Server Platforms
---

### Post by cmancre on 2010-01-28
Hi, I have a ubuntu server Hardy installed. Its a simple light webserver, apache2 + php5 + mysql5.0.51a + svn + ssh.
No FTP, no emails, no DNS server.

**Hardware**
Memory: 1GB
CPU: Pentium(R) Dual-Core CPU E5200 @ 2.50GHz


**Apache is running under virtualhosts basis.**
~ 40 websites. Average of 50 visits each one per day.

**MySQL usage**
80-90% selects ; 10%-20% inserts/updates/remove

**break down symptoms**
- trying to access a website takes forever. Looks like apache still alive but does not respond.
- ssh connect keeps available
- if I restart MySQL and sometimes MySQL+Apache, it starts running normally.

This morning happen again, I took a screenshot from MUNIN, maybe could give you a cue.

I restart apache+mysql at Jan 28, 2010 at 10:45 AM.

Does the image below alert you for something before 10:45 AM?

[IMG]http://img52.imageshack.us/img52/2646/system1.png[/IMG]

---

