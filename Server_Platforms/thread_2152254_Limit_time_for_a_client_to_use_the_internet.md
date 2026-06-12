---
title: "Limit time for a client to use the internet"
date: 2013-06-07
forum: Server Platforms
---

### Post by MBekkers on 2013-06-07
Hi,

I am currently in college and I need to set up a network using Ubuntu, I've done it in the past using Windows but never really touched my hands on Linux.

We basically need a program that we can place on our server, and that people can internet on it when they have a valid Ticket ID. After filling in this ticket ID they will be able to browse the internet for 2 hours before they get disconnected and their voucher is no longer valid.

Does anyone knows a program I can install on my server?

Best regards,

Michael

---

### Post by sandyd on 2013-06-07
Try FreeRadius + 802.1X

---

### Post by suiyiguang on 2013-06-08
well...:KS

---

### Post by MBekkers on 2013-06-11
I could not find a tutorial on how to do this, does anyone has a link available to install this in a Linux OS?

---

### Post by newbie-user on 2013-06-11
If you're coming from Windows and have never really used Linux, I'd recommend using [pfSense]("http://www.pfsense.org/"). It has web-based configuration, so you won't have to spend a lot of time in the command line. I use it for timed access at my work.

---

### Post by sandyd on 2013-06-11
> **MBekkers said:**
> I could not find a tutorial on how to do this, does anyone has a link available to install this in a Linux OS?

There are a lot of tutorials of turorials:
[http://abechik.wordpress.com/2007/03/15/freeradius-disconnected-user-when-time-limit-exceed/](http://abechik.wordpress.com/2007/03/15/freeradius-disconnected-user-when-time-limit-exceed/)
[http://wiki.freeradius.org/modules/Rlm_sqlcounter](http://wiki.freeradius.org/modules/Rlm_sqlcounter) (limits packets)

just to name a few.

these require you to set the router to use 802.1x auth against the radius server

---

