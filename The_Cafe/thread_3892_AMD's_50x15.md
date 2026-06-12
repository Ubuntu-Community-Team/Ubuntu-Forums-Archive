---
title: "AMD's 50x15"
date: 2004-11-10
forum: The Cafe
---

### Post by costoa on 2004-11-10
The 50x15 PIC (Personal Internet Communicator) is a tiny, low cost, low power usage PC that will be manufactured by AMD. It will retail for $185USD. The "50x15" part is AMD's goal: get 50% of the world on the Internet by 2015. Currently only about 10% of the world is connected.

Specs:
Size: 		5.5 x 8.5 x 2.5-inches
Weight:		< 4 pounds
CPU: 		AMD Geode GX 500 1.0W CPU running at 366MHz
RAM:		128M
HD:		10G
Ports:		four USB, VGA, 56K v.92 modem, audio line out, line in and headphones
Power:		external power "brick"
Supplied OS:	A weird mix of Windows CE and XP

Questions and thoughts:
- Distro distribution: an USB flash drive seems the easiest way. It's a safe bet the PIC supports USB boot and 1G flash drives can be had for ~$80USD (and are quite reusable). IMO not a problem.
- CPU speed: Can Ubuntu happily run on a 366MHz machine or is a customized version needed?
- Networking: I really wished they had included ethernet but you work with what you have. Since there's two USB ports on the back one could add an ethernet, 802.11x or bluetooth adapter. Networking over USB is messy but again, you work with what you have. Luckily these adapters are only $25 to $40. Is anyone running networking over USB here? If so, what hardware and issues.

I guess I could see a custom Ubuntu installation disk image that could be downloaded and written to a flash drive. Since hardware choices are limited the installer could offer the end user very simple and limited choices for a quick and pain free install.

Ubuntu is about community and IMO these machines could be a great way to make it much larger. Even though they were designed for developing nations they have many uses everywhere. Families with one "regular" PC could have one as a second machine and wirelessly network it to the first for file access. Small companies could use it as a replacement for bulky and noisy systems. It could even be carried in a backpack with a battery and used with a HUD (Heads Up Display). IMO if AMD plays their cards right this could be a really big thing. I also believe what's good for developing nations can also be good for "developed" nations (I hate those terms but am at a loss for something else).

Check out [http://www.amd.com/50x15](http://www.amd.com/50x15) or [http://www.google.com/search?hl=en&q=50x15%2Bamd](http://www.google.com/search?hl=en&q=50x15%2Bamd)

Well, what does everyone think? Part of my thinking is if people start with MS Windows changing to GNU/Linux would be difficult for some. Let's get them started on the right foot. =) BTW, attached is a picture of said PC.

---

### Post by HungSquirrel on 2004-11-10
I would love to get my hands on one of these and use it as a router.  Shame it doesn't mention whether it comes with 10/100.

---

### Post by costoa on 2004-11-10
[QUOTE=HungSquirrel]I would love to get my hands on one of these and use it as a router.  Shame it doesn't mention whether it comes with 10/100.[/QUOTE]

Check out the Via EPIA CL motherboard. It's 17cm x 17cm and comes with dual ethernet. Since it's a router and a lot of HD space is unneeded you could skip the standard drive and go with an IDE to CompactFlash card adapter (~$20USD) with a 512M CF card (~$60).

[http://www.viaembedded.com/product/epia_cl_spec.jsp?motherboardId=181](http://www.viaembedded.com/product/epia_cl_spec.jsp?motherboardId=181)
[http://www.mini-itx.com/projects/epiacl-firewall/](http://www.mini-itx.com/projects/epiacl-firewall/)

The VIA EPIA TC similar except it has one ethernet port with built in CF and PCMICIA (cardbus) slots. Excellent if you're building an ethernet to wireless router/gateway. Both boards cost about ~$200USD.

[http://www.viaembedded.com/product/epia_tc_spec.jsp?motherboardId=201](http://www.viaembedded.com/product/epia_tc_spec.jsp?motherboardId=201)

---

### Post by FLeiXiuS on 2004-11-10
I've always loved my old laptop as my router / server.  It handles all of my light work while my main server holds:

apache
sendmail
mysql + php
webmin
ftp
bind

Its always useful to have these services.  Makes for a better service in the end.

[http://69.143.69.173/~fleixius/nick/Screenshot.png](http://69.143.69.173/~fleixius/nick/Screenshot.png)

Bind hasn't propagated yet.  [www.net-critical.com](www.net-critical.com)

---

### Post by costoa on 2004-11-10
[QUOTE=FLeiXiuS]I've always loved my old laptop as my router / server.  It handles all of my light work while my main server holds:

apache
sendmail
mysql + php
webmin
ftp
bind

Its always useful to have these services.  Makes for a better service in the end.

[/QUOTE]

Old laptops are great for stuff like that. Small size and a silent power supply. Sometimes, if you're lucky, you can find one with a bad screen for a cheap price. 

Hey HungSquirrel, think about using one. Most modern laptops have ethernet and pcmcia slots for a second eth card or 802.11x. Most also have vga out so a bad screen isn't a problem.

Good idea FLeiXiuS, thanks.

---

### Post by HungSquirrel on 2004-11-10
Actually, my laptop's LCD just died, so...yeah.  Time to stick OpenBSD on it.  :)

---

### Post by HiddenWolf on 2004-11-11
I've had an old 133mhz IBM for that. It ran debian stable, and my personal-use ftp/mysql servers, 24/7

*sweet memories*

---

### Post by jeremy on 2006-05-05
Does anyone know if Ubuntu has been installed on the 50x15?

---

### Post by 3rdalbum on 2006-05-05
I don't know what type of CPU it is really. It could be x86, it could be ARM. If it's the latter, then Debian might run on it. If it's the former, then Xubuntu could run on it.

---

### Post by Teroedni on 2006-05-05
its an x86processor.
Unfortunally it seems like Linux is getting ignored in this one:sad: 

Here is more about this case 
[http://www.linuxdevices.com/news/NS8339641893.html](http://www.linuxdevices.com/news/NS8339641893.html)

---

### Post by jeremy on 2006-05-05
I e-mailed them, here is what I sent, and their reply:
> 
Thank you for your interest in the Personal Internet Communicator.
Linux is currently being investigated as a possible O/S for PIC, but no
timeline has been set to introduce PIC with Linux.

Regards,

PIC Support Team

-----Original Message-----
From: Jeremy [mailto:xxxxxx@xxxxxx.com] 
Sent: Friday, May 05, 2006 5:04 AM
To: Info, Pic
Subject: OS

Dear Sirs,

I am considering purchase of a number of PIC's for my organization, but
have 
not been able to find confirmation that I will be able to install Linux.
Could you please direct me to any information on this.

Best Regards,
Jeremy


Their address is [email]pic.info@amd.com[/email]
perhaps if they have many enquiries from potential "large corporate clients" (like me, ha ha), they will be encouraged to continue their "investigation".

---

