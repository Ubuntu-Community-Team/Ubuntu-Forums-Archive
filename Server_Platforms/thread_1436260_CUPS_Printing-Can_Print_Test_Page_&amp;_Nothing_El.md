---
title: "CUPS Printing-Can Print Test Page &amp; Nothing Else"
date: 2010-03-22
forum: Server Platforms
---

### Post by andrewt522 on 2010-03-22
I recently built a server from an old box using Ubuntu Server 9.10.  This is my first server and I am very new to the server world.

I have an Epson Stylus NX400 connected via USB.  I have managed to configure it to the point where I can see the printer listed on my client laptop and can print a test page.  However, I cannot print anything else.  When I access the job history through the CUPS admin ([http://localhost:631/admin](http://localhost:631/admin)) I can see that the print jobs were recognized and marked as complete, even though the printer never physically engaged.

Thanks in advance for your help.

---

### Post by KB1JWQ on 2010-03-22
My CUPS experience is limited to Mac OS, but is there a log of some sort that it's leaving that you could paste?

---

### Post by andrewt522 on 2010-03-22
From the CUPS Web Interface, under Administration > Manage Printers, my printer comes up as listed.  I click my printer > Maintenance, and receive this information:
> EPSON_Stylus_NX400 EPSON_Stylus_NX400 Error

Error:

     Unknown operation ""!
I'm fairly confident that this doesn't help much.  If there's something specific you'd like me to provide, please let me know.

---

### Post by andrewt522 on 2010-03-22
Ok, so, I don't know why this would make a difference, but after a ```
sudo apt-get update
sudo apt-get upgrade
```on the server, I can suddenly print.  There was that, plus, I logged into my SAMBA share.  I don't know why both of those things would make a difference, but they did.  If anybody could explain it to me, I would appreciate it.  Otherwise, I apologize for wasting anybody's time and mark this problem solved.

---

### Post by KB1JWQ on 2010-03-23
Well, the Ubuntu devs don't release updates just because they enjoy watching us tie up bandwidth.  There are usually patches that fix problems-- presumably you weren't the only person to have this issue.

Updating regularly is a good thing!

---

