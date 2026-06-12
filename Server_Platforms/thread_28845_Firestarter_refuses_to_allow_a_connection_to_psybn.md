---
title: "Firestarter refuses to allow a connection to psybnc"
date: 2005-04-21
forum: Server Platforms
---

### Post by [censored] on 2005-04-21
Hi. I have a psybnc at nitro.unixdemon.com. A psybnc is basically a kind of proxy for use on irc. In some places, it's a very good idea not to let people see your IP.

For some reason, though, Firestarter just refuses to allow inbound connections from that source. As a consequence, I can't seem to connect to it either.

I read the tutorial, and I've tried right-clicking and selecting "Allow Connections from Source".

I've tried selecting "Allow Inbound Service for Source".

I've tried selecting "Allow Inbound Service for Everyone".

It's no use. The IP 72.20.15.66 just keeps appearing in the Events dialog for some reason, as blocked.

---

### Post by [censored] on 2005-04-27
Received this email from Tomas Junnonen on the Firestarter Mailing List. His proposed solution did the trick:

> This problem is fixed in Firestarter 1.0.3. Unfortunately Ubuntu's 
version of Firestarter is a little behind. You can however manually fix 
this by editing the file /etc/firestarter/non-routables. Remove the line 
"72.0.0.0/8" and restart Firestarter.

Regards,
Tomas

---

### Post by madmonk3y on 2007-06-20
[http://ubuntuforums.org/showpost.php?p=2829953&postcount=1](http://ubuntuforums.org/showpost.php?p=2829953&postcount=1)

Try the above link.  If you still want to install PsyBNC knowing that and why it won't work correctly, here's the packages you need to be able to make menuconfig and have the compile complete (with warnings and future instability):

[http://ubuntuforums.org/showpost.php?p=2830116&postcount=5](http://ubuntuforums.org/showpost.php?p=2830116&postcount=5)

---

