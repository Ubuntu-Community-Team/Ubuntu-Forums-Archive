---
title: "Lotus SmartSuite Millennium Edition Works with Jaunty and WINE 1.1.20!"
date: 2009-05-01
forum: Wine
---

### Post by 8oluf7 on 2009-05-01
I've been encouraging a friend to switch to Linux (and, specifically, Ubuntu). The one thing holding her back has been that the whole history of her business is held in files created in old versions of Lotus SmartSuite applications e.g. Approach, 1-2-3, WordPro. 

I've made several previous attempts to get SmartSuite to install under WINE - with limited success. My friend bought Crossover and, although they were very helpful, they failed to get an install to work either. 

The good news is, that with WINE 1.1.20 installed under Jaunty, Lotus SmartSuite Millennium Edition (version 9) installs easily and seems to work without any problems.

I set the Windows version in WINE to Windows 98 before attempting to install SmartSuite and I declined offers to install extra goodies. Apart from that, I accepted the defaults I was offered and the installation went smoothly. Of course, the installer wanted to restart the system at the end!

One question: When I finished the install, the SmartSuite application icons appeared in the notification panel. After logging out and back in again, they've disappeared. Anyone know how to get them back?

---

### Post by asdfoo on 2009-05-01
Hi

I believe there is a native linux replacement for Smartsuite called Lotus Symphony and it's free to download.

[http://symphony.lotus.com/software/lotus/symphony/home.nsf/home](http://symphony.lotus.com/software/lotus/symphony/home.nsf/home)

I'm guessing they're not in the notification panel because they run on startup and Wine might not be running...


[http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e](http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e)

---

### Post by 8oluf7 on 2009-05-02
> **asdfoo said:**
> hi

i believe there is a native linux replacement for smartsuite called lotus symphony and it's free to download.

[http://symphony.lotus.com/software/lotus/symphony/home.nsf/home](http://symphony.lotus.com/software/lotus/symphony/home.nsf/home)

YABUT - It would be more correct to describe Lotus Symphony as a successor to Lotus SmartSuite - with significant differences. Lotus Symphony doesn't include a database! Key elements of my friend's business are documented in Lotus Approach. Like most databases, Approach uses a unique-to-it file format. So - although we could find a work-round for other elements of SmartSuite, such as 1-2-3 and WordPro (e.g. OOo3) we were stuck when we came to the all-important databases - until now.

---

### Post by Alex James on 2009-09-13
Thanks 8oluf7.  Lotus Approach from SmartSuite Millennium (i.e. version 9.5) Edition works with Jaunty and WINE 1.1.20, installed under Windows 98.  Organizer did not work.  Also, Smartsuite 9.8.2 could not be installed with Wine under Windows XP.  I haven't tried later versions of Wine. They may work too.

---

