---
title: "is ltsp supported at ubuntu-server 10.04 ?"
date: 2011-04-01
forum: Server Platforms
---

### Post by qmax on 2011-04-01
In internets there are lot of successless stories installing ltsp on ubuntu 10.04.
Most problems are in ndb, init scripts and somewhere else, which are hardly debuggable.
It seems like ubuntu 10.04 has ltsp packages completely broken and abandoned.

Have someone succeeded to install ltsp on 10.04 without hard brainfucking?

Maybe it's better to install ltsp from scratch, or choose another distribution?

---

### Post by MikeUK on 2011-04-01
> **qmax said:**
> In internets there are lot of successless stories installing ltsp on ubuntu 10.04.
Most problems are in ndb, init scripts and somewhere else, which are hardly debuggable.
It seems like ubuntu 10.04 has ltsp packages completely broken and abandoned.

Have someone succeeded to install ltsp on 10.04 without hard brainfucking?

Maybe it's better to install ltsp from scratch, or choose another distribution?

The 10.04 is the LTS version I have running LTSP at home, works fine, no issues, no probelms.
The only issues I had was I looked in the 'old' places to update my files, the DHCPD should be updated/edited in LTSP not DHCP, and the right tftp setup is under SRV.

---

### Post by qmax on 2011-04-05
> **MikeUK said:**
> The 10.04 is the LTS version I have running LTSP at home, works fine, no issues, no probelms.
The only issues I had was I looked in the 'old' places to update my files, the DHCPD should be updated/edited in LTSP not DHCP, and the right tftp setup is under SRV.

Have you installed ltsp with apt-get, or from CD-installer (of server, desktop or alternate)?
In my 10.4.02 i have tftp in /var/lib/tftpboot

However my issues are not in client booting, but at client startup scripts.
And i have no idea how to track the issues.

---

### Post by priithansen on 2011-04-10
I had some serious mind melting problems when trying to test LTSP at first but after two days of messing about it all of a sudden just worked. Here is how I got it to work for me. [Link]("http://blog.onebit.ee/2011/04/07/how-to-get-ubuntu-10-10-and-ltsp-work-with-virtualbox/")

---

