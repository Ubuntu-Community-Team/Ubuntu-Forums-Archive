---
title: "[SOLVED] cups xp"
date: 2008-01-07
forum: Server Platforms
---

### Post by gishaust on 2008-01-07
Hi everyone

I have looking over this issue for a couple of hours and need some direction. I have ubuntu 7.04 server that I have built from scratch.
I have installed samba and cups. I can access the share over the network. With cups I can see the printer on the freebsd box and can print to the printer not and issue but on the window xphome box I can't. I can access the share on the server. but when I go to print a test page on the windows machine it asks for the  driver, I try install the windows driver but no go. What I want to know is will the xp windows driver for the hp pc 1600 printer going to work or do I have to get another one and install it  on the xpbox so that it can talk to the printer over samba.  

Any information would be great

gishaust

---

### Post by Swmmrman on 2008-01-07
Hmm  I dont think the windows driver will install with wine.  I think your goign to have to go looking

---

### Post by Maxtorm on 2008-01-07
If you can see the printer -- and assuming you have permission to print to it -- the Windows XP driver should work fine.

---

### Post by PerJensen on 2008-01-08
Maybe I don't understand correctly, but what I do on Windows boxes when printing to a CUPS server is to use IPP and completely bypass the Samba server. For me that has proven to be very reliable.

In Windows XP start adding a new printer
Select network printer and select the nondefault option, can't remember the exact wording. You must give a URL to the CUPS server

Example:
[http://192.168.1.10:631/printers/queuename](http://192.168.1.10:631/printers/queuename)

where 192.168.1.10 is the IP address and 'queuename' is the CUPS queue name you have defined. Test the URL first in a webbrowser to make sure it is correct. You will get a webpage to administer the printerqueue.

Windows XP will barf at you and require you to install a printer driver. Install it and you are good to go.

Hope that helps

/Per

---

### Post by gishaust on 2008-01-08
Thanks for your information. You were right the printer driver worked great but I am wondering why I had to do the following to get it to work.

Could not get the driver to install over the network no matter what i did.
I got hold of another  xpbox  and installed the driver on that. To test if it would share. Straight away on the xphome it install a driver that it asked for from the computer that was sharing the printer. I then changed the printer to the ubuntu server and tried to share it. And straight away  the  xphome worked. I found out that window boxes don't need to know where the printer is attached to so why do I have to use the driver that the other xp computer gave it instead of what was on the disk, They are the same as i use the same disk?

---

### Post by PerJensen on 2008-01-08
The XP box doesn't need to know where the printer is. Thats for CUPS to handle. I forgot to mention that the CUPS queue in this solution is a raw queue which simply forward preformatted printjobs to a printer. Thats why you must install a printerdriver on the XP box.

---

### Post by gishaust on 2008-01-09
thanks for your help

---

