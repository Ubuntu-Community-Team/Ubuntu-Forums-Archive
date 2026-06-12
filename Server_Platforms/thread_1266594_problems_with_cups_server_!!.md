---
title: "problems with cups server !!"
date: 2009-09-14
forum: Server Platforms
---

### Post by oospill on 2009-09-14
hi.  I've got a box upstairs running ubuntu server.  it's hooked up to a wireless router (so my laptop and surf throughout the house), and it's hooked up to a printer.  I'm trying to get CUPS setup so I can print from my laptop (running ubuntu desktop).  

I got cups installed on my server, and it found my printer for me, and printed a test page.  now how do I setup my laptop to use the printer?

thanks,
oospill

---

### Post by tgalati4 on 2009-09-14
Open a browser:

[http://localhost:631/](http://localhost:631/)

Admin-->Add printer

IPP:

Put the URL that shows up in the server:

lpstat -a

[http://YourServerIP:631/printers/HP-OfficeJet-7110](http://YourServerIP:631/printers/HP-OfficeJet-7110)

Substitute HP-OfficeJet-7110 with your printer as shown on the server using lpstat -a.

---

### Post by abaden on 2009-09-14
Is [this]("https://help.ubuntu.com/community/SettingUpSamba#Sharing%20CUPS%20Printers") of any help to you?

Your windows or apple machine should be able to just search for the printer. In Ubuntu 9.04 when you hit "New" in the printer options you should also get a search for a new printer. From there you can enter a host to search that host for a network printer. 


Alex

---

### Post by tgalati4 on 2009-09-14
Yea, but that's cheating.

---

### Post by oospill on 2009-09-15
> **tgalati4 said:**
> Open a browser:
[http://localhost:631/](http://localhost:631/)
Admin-->Add printer
IPP:
Put the URL that shows up in the server:
lpstat -a
[http://YourServerIP:631/printers/HP-OfficeJet-7110](http://YourServerIP:631/printers/HP-OfficeJet-7110)

Substitute HP-OfficeJet-7110 with your printer as shown on the server using lpstat -a.

<quote off>

okay I tried that, and I think I did it right.  but it won't print anything..  so I browsed to "http://localhost:631" and selected "manage printers" .. the printer showed up, but with an error: "Unable to get printer status (Forbidden)!" ..

this doesn't really suprise me.  when I try to logging in to 192.168.1.3 (my server box) port 631 I get a "FORBIDDEN" error, NOT a "cannot connect" error..  the forbidden error says that there IS something on that port, it just seems like I'm not allowed to access it.  does that make ANY sense?

thanks for any help!!

---

### Post by tgalati4 on 2009-09-15
What version of CUPS do you have on the server?  What version of CUPS do you have on the laptop?  There have been some changes in default security policy in CUPS.

I presume that you have a user account with the same user name as on the laptop.  Failure to set up users on the server can mess up authentication for those programs that rely on user authentation.

I presume that you tried using the GUI print manager to search for the hosted printer and it failed as well?

To log into your server remotely ([http://192.168.1.3:631/](http://192.168.1.3:631/)), you need to make a few changes in your /etc/cups/cupsd.conf to allow remote administration.  By default you can only add printers as a user/admin through localhost:631.  On a server this is difficult because you don't have a graphical environment.  So you make a few changes to the cupsd.conf, reboot or restart cups:

sudo /etc/init/cupsys restart

The changes you make depend on what version of CUPS you are running.

Also, depending on your router, you may have to put a port-forward for port 631 to 192.168.1.3.  This is not normally needed if you are inside your LAN.  I presume your laptop is inside 192.168.1.X.  But because it is wireless, the router may have a different security policy and not allow two-way 631 communication.  One way to isolate is to physically plug in your laptop into the router with an ethernet cable and make sure you can print normally.

---

### Post by oospill on 2009-09-15
wait a second.  I feel like an idiot.  I only installed CUPS on my server, not on my laptop.

brb

nevermind.  it's already installed.  okay, lemme read the previous post real quick.

---

