---
title: "cannon ip2600"
date: 2010-10-05
forum: Server Platforms
---

### Post by Mr.O on 2010-10-05
I am having a problem with installing a printer driver I am getting the following error,
[HTML]root@mnpu:/home/matt/printer# dpkg --install --force-architecture cnijfilter-common_2.90-1_i386.deb
(Reading database ... 58493 files and directories currently installed.)
Preparing to replace cnijfilter-common 2.90-1 (using cnijfilter-common_2.90-1_i386.deb) ...
Unpacking replacement cnijfilter-common ...
dpkg: dependency problems prevent configuration of cnijfilter-common:
 cnijfilter-common depends on libcupsys2 (>= 1.2.1); however:
  Package libcupsys2 is not installed.
dpkg: error processing cnijfilter-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common
[/HTML]Any suggestions on what to do to get the driver installed?
Mr. O

---

### Post by druhboruch on 2010-10-05
It looks like a very old package.
It requires libcupsys2.
In the repo we have libcups2.

You could:
dpkg --force-depends.
then you probably would have to link missing libcupsys libary to libcups.so.2 in /usr/lib.
You may find the exact name of the library by searching packages.ubuntu.com of the past versions of Ubuntu.

Have you tried generic PCL5 driver?

---

### Post by Mr.O on 2010-10-06
The force depends didnt work. Where would I find the PCL5 drivers?

---

### Post by druhboruch on 2010-10-06
PCL5e driver is already installed.
Use Printing applet from Administration menu

---

### Post by Mr.O on 2010-10-06
I am working with a server version. That is why I put this thread in the server section of the forum. I need server instructions on how to use the darn thing.

---

### Post by druhboruch on 2010-10-06
You can use cups' web interface to configure printer:
[http://mikebeach.org/2010/06/ubuntu-and-brother-hl-2170w/](http://mikebeach.org/2010/06/ubuntu-and-brother-hl-2170w/)
The instructions are for brother, but it should be close enough.
Of course you would have to install cups and recommended packages.

---

### Post by Mr.O on 2010-10-06
I dont have the web interface! I want COMMAND LINE INSTRUCTIONS. Sorry, I have been having problems with this printer for about four months and have been asking questions and havent been getting good results. I will give more than enough information to tell everyone exactly what my situation is. I have a ubuntu 10.01 p4 nortwood core, 512mb ram 160gb hd, samba, g++, and the base packages installed. It is in a gx270 with an availible sata plug. The printer I want to use has a usb 2.0 connection and is a cannon pixima ip2600. All I am after is some drivers that will work so that I can print over the network with a windows computer. What are your suggestions?

---

### Post by druhboruch on 2010-10-06
Mr.O
In order to print in Linux you must have cups installed.
It is not installed by default.
Your server can be just a command line system wihtout desktop environment, but if you want to print you must have cups.
It comes with embedded web server, so you don't have to install web server of any sort.  It listens on port 631.
You can access web interface from another PC and add remove configure and share printers connected to your server.
Cups comes with hundreds of drivers, many generic.
I only suggest that you try a generic PCL5e driver from hpijs package.



I wish you good luck.

EDIT:
I just checked and IP2000 and IP3000 is supported

---

### Post by Mr.O on 2010-10-07
What package would that be? I have already tried to install cups and got nowhere. I have run lanspy on the thing and the port you said would work is not on the list.

---

### Post by druhboruch on 2010-10-07
Look for cupsd.conf under /etc/cups/

```
Listen localhost:631
```

This is why you don't see it from the outside...

---

