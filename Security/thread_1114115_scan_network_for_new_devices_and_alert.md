---
title: "scan network for new devices and alert"
date: 2009-04-02
forum: Security
---

### Post by dragonslayr on 2009-04-02
I managed to find autoscan but for the life of me, I can not see where to put the email address to send to when a new device is detected on the network.

Was wondering what tools might be around to alert when a new device ie a laptop is plugged into the network..

---

### Post by kryptikos on 2009-04-02
There are lots of tools that you can use to watch your network and report items or discover during preplanned scans. Nmap ([http://nmap.org/]("http://nmap.org/"))is one of the most powerful and best tools out there. A good place to start is insecure.org. I've included a link to their top 100 network security tools:

[http://sectools.org/]("http://sectools.org/")

Good descriptions as well as what platform the app will run on and whether it is proprietary (read $$$) or oss.

---

### Post by gombadi on 2009-04-02
arpwatch may be useful

```

lroger@dave:~$ apt-cache show arpwatch
Package: arpwatch
Priority: optional
Section: universe/admin
Installed-Size: 468
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: KELEMEN Péter <fuji@debian.org>
Architecture: amd64
Version: 2.1a13-2.1
Depends: adduser, debianutils, libc6 (>= 2.4), libpcap0.8 (>= 0.9.3-1)
Recommends: mail-transport-agent
Suggests: snmp
Filename: pool/universe/a/arpwatch/arpwatch_2.1a13-2.1_amd64.deb
Size: 127940
MD5sum: 8f78720c12f60a60b4b73553f6dc3591
SHA1: 1c3018c14484d70ff09b3cf9a81fa598383af08f
SHA256: fb003a78e96755aeafe6d1de3572e0b7dea440f9a7fd136541aa6294abc0ef40
Description: Ethernet/FDDI station activity monitor
 Arpwatch maintains a database of Ethernet MAC addresses seen on the
 network, with their associated IP pairs.  Alerts the system administrator
 via e-mail if any change happens, such as new station/activity,
 flip-flops, changed and re-used old addresses.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


```

---

### Post by dragonslayr on 2009-04-03
I can not see where nmap would be usefull for alerting of new devices. However, arpwatch seems to do exactly that, with other benefits as well. Nice to plug in a new printer and have an email waiting on me telling me the ip so I can go set it static etc..   :)

However, it'd be nice to have more options.. Beeping for an alert etc..


Thanks

---

### Post by kryptikos on 2009-04-06
> **dragonslayr said:**
> I can not see where nmap would be usefull for alerting of new devices. However, arpwatch seems to do exactly that, with other benefits as well. Nice to plug in a new printer and have an email waiting on me telling me the ip so I can go set it static etc..   :)

However, it'd be nice to have more options.. Beeping for an alert etc..


Thanks

Nmap is extraordinarily useful for watching your network. It is one of, if not the first tool any security admin, network engineer or hacker (white/gray/black) hat will use to look at and scope out what's on a network. :)

Another tool that is good for watching real-time communication is etherape. It is graphical and will represent how much data is being piped between devices by thickness of the colored line. As new devices communicate across the LAN the ips and data pipes will appear.

---

