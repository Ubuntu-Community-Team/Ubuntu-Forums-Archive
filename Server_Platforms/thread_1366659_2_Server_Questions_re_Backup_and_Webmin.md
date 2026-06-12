---
title: "2 Server Questions re: Backup and Webmin"
date: 2009-12-28
forum: Server Platforms
---

### Post by AvvidMe on 2009-12-28
Hi Everyone;

New to Ubuntu (only a few months) and to this site.
Last month I have JUST DE-MICROSOFT'd my entire house now running Mac's, QNAP NAS's and Ubuntu servers and LOVING IT!

Anyways - I'm running Ubuntu 9.04 servers under ESX and running headless (No GUI) with only Webmin (also incredible).  1 x Kerio Email server, and 1 x Web server

**Question 1:** Looking for good backup software that will run nicely under Webmin.  I've seen Bacula, but I LOVE the Flyback option although requires a GUI.   Either that or, if I was to do  a plain old "File Backup" through Webmin, what are the crucial directories (besides my own data) that need to be backed up for a complete restore?

**Question 2:** Is there a good monitoring tool (server health/SNMP etc.) that anyone would recommend?  Either stand alone (dedicated server) or Webmin would be fine.

Thanks everyone, looking forward to spending more time here!
Cheers!

---

### Post by phillw on 2009-12-28
> **AvvidMe said:**
> Hi Everyone;

New to Ubuntu (only a few months) and to this site.
Last month I have JUST DE-MICROSOFT'd my entire house now running Mac's, QNAP NAS's and Ubuntu servers and LOVING IT!

Anyways - I'm running Ubuntu 9.04 servers under ESX and running headless (No GUI) with only Webmin (also incredible).  1 x Kerio Email server, and 1 x Web server

**Question 1:** Looking for good backup software that will run nicely under Webmin.  I've seen Bacula, but I LOVE the Flyback option although requires a GUI.   Either that or, if I was to do  a plain old "File Backup" through Webmin, what are the crucial directories (besides my own data) that need to be backed up for a complete restore?

**Question 2:** Is there a good monitoring tool (server health/SNMP etc.) that anyone would recommend?  Either stand alone (dedicated server) or Webmin would be fine.

Thanks everyone, looking forward to spending more time here!
Cheers!

Hi & welcome - Webmin, being such a small, unused package has about 1 option ....

Okay, maybe I was fibbing a bit :lolflag:

Head over to [http://www.webmin.com/cgi-bin/search_third.cgi?category=System](http://www.webmin.com/cgi-bin/search_third.cgi?category=System)  Just make sure you get Debian based things to 'play' with - they're much, much easier to put onto a ubuntu installation !!!

For monitoring, do you mean checking for attacks, file integrity etc. Then I'd suggest reading the mail logs in Webmin and putting on something like ossec, which will keep an eye on things.

A good introduction to health checking, etc is over here -->  [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

That whole forum is dedicated to security issues, so feel free to ask - Just do take the time to read the stickies.

Regards,

Phill.

---

### Post by Xiuh on 2009-12-28
A few years ago I was really interested in network monitoring tool suites. However, packages like What's up Gold and Solarwinds were way out of any price range that I was comfortable recommending for purchase. This actually lead me into playing around with the Ubuntu server (vs MS server). I started out with Nagios (can't remember what i used for the front end), but decided I wanted something that dazzled my eyes. I found [Zenoss ]("http://www.zenoss.com/")had a really slick management console. It doesn't(didn't?) have compiled debian binaries and required compiling from source code. However, they had detailed instructions on their website on setting things up for Ubuntu. 

After awhile I got bored of tweaking it and it was getting overly chatty on the network (I had setup entirely to many mips and felt I just HAD to install a client on every workstation). I removed it and moved on to other things :P 

Still, you might glance it over. 

One other idea, I believe Webmin can do quite a bit of reporting on Network utilization. I think it just needs some mips defined I thought the module integrated with Nagios as a suggestion (anyone correct me if I'm wrong on that, haven't ever set the two of these up to talk).

---

