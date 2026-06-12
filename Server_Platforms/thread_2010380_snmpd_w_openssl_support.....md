---
title: "snmpd w/ openssl support....?"
date: 2012-06-25
forum: Server Platforms
---

### Post by andygauvin.ee on 2012-06-25
Hi all,

Setting up a SNMP-enabled tier for work and trying to get SNMPv3 working with some proper authentication/encryption so that digital passer-bys aren't scraping our vital signs and probing our networks...

I've followed the guide over yonder: [http://wmunguiam.blogspot.com/2009/07/howto-use-snmpv3-ubuntu.html](http://wmunguiam.blogspot.com/2009/07/howto-use-snmpv3-ubuntu.html)  - Great guide on the subject of SNMPv3 and correctly setting up users!

HOWEVER! My real problem lies in the Ubuntu repo-provided snmpd. I want DES/AES encryption in addition to the standard SHA/MD5 authentication, but for that to work, snmpd needs to be compiled with openssl support; apparently the Ubuntu version isn't!

I'd have no problem recompiling from source on my own machines, but in a server environment I'd really prefer to use a repo so that upgrades are seamless and painless when things like libc6 or openssl sees upgrades...

Anybody have any input without going as far as managing my own repo...? ;)


Just to data, you can see that there is no openssl support in my snmpd *server*, but my snmp *client* at least depends on it:
```

$ lsb_release -a 2> /dev/null | grep Release
Release:    12.04

$ dpkg -s snmpd | grep '^Original\|Maintainer\|Version\|Depends'
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Version: 5.4.3~dfsg-2.4ubuntu1.1
Depends: libc6 (>= 2.15), libsnmp15 (>= 5.4.3~dfsg), libwrap0 (>= 7.6-4~), debconf (>= 0.5) | debconf-2.0, adduser, debconf, lsb-base (>= 3.2-13)
Original-Maintainer: Net-SNMP Packaging Team <pkg-net-snmp-devel@lists.alioth.debian.org>

$ dpkg -s snmp | grep '^Original\|Maintainer\|Version\|Depends'
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Version: 5.4.3~dfsg-2.4ubuntu1.1
Depends: libc6 (>= 2.14), libsnmp15 (>= 5.4.3~dfsg), libssl1.0.0 (>= 1.0.0)
Original-Maintainer: Net-SNMP Packaging Team <pkg-net-snmp-devel@lists.alioth.debian.org>

```

---

### Post by andygauvin.ee on 2012-06-27
ala *bump*;

Anybody..?

---

### Post by ptn107 on 2012-06-27
Set up a PPA on launchpad.  It works like your own Ubuntu repository!

[https://login.launchpad.net/+new_account](https://login.launchpad.net/+new_account)

---

### Post by ptn107 on 2012-06-27
Openssl should be supported from the get-go.  I see that '--with-openssl' is passed to .configure by debian/rules during the compilation of snmpd.

---

