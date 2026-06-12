---
title: "colord: Cannot adopt OID ...."
date: 2018-09-03
forum: Ubuntu Development Version
---

### Post by dino99 on 2018-09-03
Journalctl has plenty of colord entries garbage:  [https://paste.ubuntu.com/p/5nQgcYTxm7/](https://paste.ubuntu.com/p/5nQgcYTxm7/)


Some old similar errors found on google suggest either installing snmp or snmp-mibs-downloader (which i does not really need).

Wonder if its due to that oldish colord version: cosmic still use 1.3.3-2 version. 
Upstream stable version is at 1.3.5 and latest dev is at 1.4.3 [https://www.freedesktop.org/software/colord/download.html](https://www.freedesktop.org/software/colord/download.html)   Why such a delta ?

---

### Post by amano on 2018-09-09
I think that I remember from the ubuntu-desktop irc channel that Timo Aaltonen was going to update colord to 1.4.3 soon.

I don't know if that will fix your problem though. Disabling color profiles by default was discussed as well at some point.

Another component with a big delta would be librsvg. Ubuntu ships 2.40.20, (stable) upstream is at 2.44.3

---

### Post by amano on 2018-09-13
[https://bugs.launchpad.net/ubuntu/+source/colord/+bug/1792356](https://bugs.launchpad.net/ubuntu/+source/colord/+bug/1792356)

A FFE ist filed for colord

---

### Post by dino99 on 2018-09-13
> **amano said:**
> [https://bugs.launchpad.net/ubuntu/+source/colord/+bug/1792356](https://bugs.launchpad.net/ubuntu/+source/colord/+bug/1792356)

A FFE ist filed for colord

Thanks for the head up ):P
The new garbage is recent, so it might have been pushed by an other upgraded package; but have not identified it. (possible extra new dependecies)

---

### Post by amano on 2018-10-01
In the repo now ;)

---

