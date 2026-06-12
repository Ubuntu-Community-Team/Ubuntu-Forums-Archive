---
title: "invoke-rc.d: initscript dhcp3-server, action &quot;force-reload&quot; failed."
date: 2009-07-27
forum: Server Platforms
---

### Post by Avinash.Rao on 2009-07-27
Hi Guys,

I am trouble setting up LTSP and DHCP. I was trying to setup LTSP on my ubuntu 8.04 installed on Laptop. Just before the LTSP installation was complete, the internet connection disconnected due to power failure. 

So, I removed ltsp-server-standalone using apt-get remove and tried to install it again, but i am getting the following error. 

Setting up ltsp-server-standalone (5.0.40~bzr20080212-0ubuntu7) ...
 * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3                                           [fail] 
invoke-rc.d: initscript dhcp3-server, action "force-reload" failed.

I also tried starting dhcp manually from /etc/init.d/dhcp3-server start, but it fails.
I also reinstalled dhcp3-server..but no use.

Can anybody help me.
Avinash

---

### Post by yourarunbabu on 2010-01-28
I am also having the same problem with ubuntu 9.10 . someone pls fix it
> root@arun-desktop:/home/arun# sudo apt-get install ltsp-server-standalone
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  wine-gecko amarok-common kdemultimedia-kio-plugins libkcddb4
  libqtscript4-core libqtscript4-gui libqtscript4-uitools
  ttf-mscorefonts-installer media-player-info cabextract libqtscript4-sql
  libqtscript4-xml libtag-extras1 liblastfm0 amarok-utils libqtscript4-network
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ltsp-server-standalone
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B/43.3kB of archives.
After this operation, 94.2kB of additional disk space will be used.
Selecting previously deselected package ltsp-server-standalone.
(Reading database ... 226558 files and directories currently installed.)
Unpacking ltsp-server-standalone (from .../ltsp-server-standalone_5.1.90-0ubuntu3_all.deb) ...
Setting up ltsp-server-standalone (5.1.90-0ubuntu3) ...
 * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]
invoke-rc.d: initscript dhcp3-server, action "force-reload" failed.


Thanks in advance.

---

### Post by Avinash.Rao on 2010-01-31
Hi,

From what i understand, your seems more like a problem with DHCP, there is a document which tells how to repair this. I remember reading this on the net. 

If i find the link, i will let you know

Avinash

---

### Post by yourarunbabu on 2010-02-01
don't know if it was a coincidence.. 
anyway the above mentioned problem was solved after making the ip static.
still I am unable to setup the LTSP server.

---

### Post by Avinash.Rao on 2010-02-02
Uninstall LTSP and DHCP, restart server and install ltsp.

---

### Post by yourarunbabu on 2010-02-02
so avinash have you setup the ltsp server.
It would be of great help for me if someone already done this be there for help..

---

### Post by Avinash.Rao on 2010-02-06
Yes, its one of the most easiest thing to do. Which version of Ubuntu are you using and what exactly is your requirement? 


> **yourarunbabu said:**
> so avinash have you setup the ltsp server.
It would be of great help for me if someone already done this be there for help..

---

### Post by yourarunbabu on 2010-02-10
i will pm you the details

---

### Post by Avinash.Rao on 2010-02-11
Its better you post the requirements.

---

### Post by yourarunbabu on 2010-03-04
Sorry that I was so late in responding.

Mine is Ubuntu 32 bit and thin clients are 32 bit .
All are using ubuntu 9.10

---

### Post by Avinash.Rao on 2010-03-05
Ok, LTSP is tested in Ubuntu 9.04.

---

