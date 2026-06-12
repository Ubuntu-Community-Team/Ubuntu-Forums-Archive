---
title: "How to Cleanup an Install/Remove Mess?"
date: 2006-04-20
forum: Server Platforms
---

### Post by rem1010 on 2006-04-20
Help, :confused: 

The answer is probably somewhere, but not sure how to search for it.

This is on a 5.10 Ubuntu SERVER install not a desktop.

I installed dhcp3-server and configured it for a subnet.
It started OK.

But the clients did not have a route to the gateway, nor to the DNS servers.

NOW, my problems escalated.

I edited the dhcp-conf file and put what I thought was correct entries for the subnet I created --- at least it looked OK per documentation.

I saved it and restarted/started the server ---- It failed and came up with some errors that did not make sense.

OK, I removed the server using apt-get remove dhcp3-server, it said it did it OK.

I then apt-get -f install dhcp3-server and it said it installed OK, but when starting, I got the same errors as previous.

OK, time to skin the duck, I apt-get remove dhcp3-server and then I went into the /usr/sbin and deleted dhcp3-server and then removed all other entries in /etc and /etc/init.d

Alright, Think I have a clean system ready to re-install and get going again.

EXCEPT! apt-get -f -y install dhcp3-server FAILS and complains that /etc/init.d does not have any dhcp3-server script!

So here is the 64k question.

How does a person clean up a bad install of a program and put the system back into pristine order so that people like me can screw up and then be forgiven?

Thanks for you help in advance and forgive any spelling errors please

---

### Post by netkid91 on 2006-04-20
OK, a hint for you: NEVER remove, change, edit, or do anything (well most anything, edit config files, etc.) installed by dpkg/apt-get.  I don't know HOW to fix the mess you just made. but in the future run dpkg --purge <package name> to remove the package and config files.   Since you did apt-get remove, it ran  dpkg -r(remove) on the package.  Now dpkg -r simply removes everything but the config files, and keeps it stored in it's DB that the config files are still there so it doesn't overwrite them without asking.  On the other hand dpkg --purge removes everything, including the config files from its DB.  So now when apt-get calls dpkg(or howerver it works), it assumes the config files are still there.  Give me a moment and I'll try and find a fix.
Edit:
Try running dpkg -s dhcp3-server and post the output.

---

### Post by rem1010 on 2006-04-20
# dpkg -s dhcp3-server
Package: dhcp3-server
Status: purge ok installed
Priority: optional
Section: net
Installed-Size: 1024
Maintainer: Eloy A. Paris <peloy@debian.org>
Architecture: i386
Source: dhcp3
Version: 3.0.2-1ubuntu7
Depends: debconf, debianutils (>= 2.8.2), dhcp3-common (= 3.0.2-1ubuntu7), lsb-base, libc6 (>= 2.3.4-1), libcap1
Conflicts: dhcp
Conffiles:
 /etc/dhcp3/dhcpd.conf 2c6d17418db15a6a5565e0157d894443
 /etc/init.d/dhcp3-server 6d96fde41f6b63a7fa01b212830e9241
Description: DHCP server for automatic IP address assignment
 This is the DHCP server from version 3 of the Internet Software
 Consortium DHCP package. For more information visit the ISC web
 site at [http://www.isc.org](http://www.isc.org).
 .
 Dynamic Host Configuration Protocol (DHCP) is a protocol like BOOTP
 (actually dhcpd includes much of the functionality of BOOTPD!). It assigns
 IP addresses to clients based on lease times. DHCP is used extensively
 by Microsoft and more recently also by Apple. It is probably essential
 in any multi-platform environment.
 .
 Multiple Ethernet Interfaces are supported by this DHCP package.
 .
 Note: This package _requires_ a 2.2.x or later Linux kernel. 2.0.x kernels
 are _not_ supported.

---

### Post by netkid91 on 2006-04-20
Good, so just run sudo dpkg --purge dhcp3-server and see if it works.

---

### Post by rem1010 on 2006-04-20
# dpkg --purge dhcp3-server
(Reading database ... 21317 files and directories currently installed.)
Removing dhcp3-server ...
invoke-rc.d: unknown initscript, /etc/init.d/dhcp3-server not found.
dpkg: error processing dhcp3-server (--purge):
 subprocess pre-removal script returned error exit status 100
Errors were encountered while processing:
 dhcp3-server

---

### Post by netkid91 on 2006-04-20
OK then...
```

sudo dpkg --force-all --purge dhcp3-server

```
Try that

---

### Post by rem1010 on 2006-04-20
I fixed it --- I cheated --- I installed dhcp3-server on another debian sarge system and copied the init.d files and then did the purge.
I then reinstalled using apt-get -f install dhcp3-server and all is ok again.
Thank you for your help.

---

### Post by netkid91 on 2006-04-20
No problem, but remember what I said, never mess with the files (blah blah) your package manager installs.

---

### Post by NAKLOV on 2008-04-24
Hi,

I know the topic is like 2 years old now, but sorry.

Im having exact the same problem, already tried the things mentioned above but no solution at all.

Tried searching on the internet, but cant find it.

Hope someone else can help me here cause I really dont know what 2 do.

:-P

---

### Post by NAKLOV on 2008-04-28
Anyone?

---

### Post by NAKLOV on 2008-04-28
Please?

---

