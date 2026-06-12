---
title: "Print Server Problem"
date: 2013-06-06
forum: Server Platforms
---

### Post by RobUK on 2013-06-06
Hi All,

I have an ancient AthlonXP-based machine running as a file / print / mail server. I set it up several years ago, as a test (since I know approximately nothing about server setup), on Ubuntu Server 9.10, and until today it's performed flawlessly. This morning, however, I come to print for the first time in several days and.. nothing. From both my XP-based desktop and XUbuntu laptop, the document just sits in the local queue but is never passed on to the server.

I'm able to connect to the CUPS (v 1.4.1) admin on the server by HTTP, which shows nothing in the queue. I am able to print a test page from the admin, and successfully remove and re-add the printer (HP Lasterjet 1100A). Both my XP dekstop and XUbuntu laptop can connect to the SAMBA shared folder on the server and browse the files there, but when I try to add a network printer they can't see any - the browser just shows WORKGROUP -> SERVER1, but no available printers.

I've rebooted the server, of course, but that didn't help either. As I mentioned above, I know next nothing about server setup / admin, so at this point I'm pretty much out of ideas.

Any suggestions would be very welcome!

TIA

Rob.

---

