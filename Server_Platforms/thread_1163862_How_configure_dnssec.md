---
title: "How configure dnssec"
date: 2009-05-19
forum: Server Platforms
---

### Post by erdee on 2009-05-19
Hi sorry for my english level :D
How configure DNSSEC on bind9. i'm configured bind9 DNS & working. It is my bachelor diplom's topic. i'm reading & can't understand because my enlglish is bad. Experts! answer my posts. E.g step by step tutorial & ....

---

### Post by erdee on 2009-05-19
Hi sorry for my english level :D
How configure DNSSEC on bind9. i'm configured bind9 DNS & working. It is my bachelor diplom's topic. i'm reading & can't understand because my enlglish is bad. Experts! answer my posts. E.g step by step tutorial & shell script....

---

### Post by erdee on 2009-05-19
Hi sorry for my english level :grin:
How configure DNSSEC on bind9. i'm configured bind9 DNS & working. It is my bachelor diplom's topic. i'm reading & can't understand because my enlglish is bad. Experts! answer my posts. E.g step by step tutorial & shell script....

---

### Post by erdee on 2009-05-19
Hi sorry for my english level :grin:
How configure DNSSEC on bind9. i'm configured bind9 DNS & working. It is my bachelor diplom's topic. i'm reading & can't understand because my enlglish is bad. Experts! answer my posts. E.g step by step tutorial & shell script....

---

### Post by MechaMechanism on 2009-05-21
Go here:

[https://www.isc.org/solutions/dlv](https://www.isc.org/solutions/dlv)

[https://www.isc.org/software/bind](https://www.isc.org/software/bind)

[http://linux.thomason.homeip.net/CIS2556/DNS/Bv9ARM.html](http://linux.thomason.homeip.net/CIS2556/DNS/Bv9ARM.html)

[http://www.bind9.net/](http://www.bind9.net/)

All I can say is read the documentation, man pages and do tons of google searches.  You will need to initially set up verbose DNSSEC logging to verify that it works.  Also make sure to use a DLV registry.  Also you may need to build bind9 from source if the bind9 included with 9.04 does not have the appropriate cipher that was recently implemented, see here:


[https://lists.isc.org/pipermail/dlv-announce/2009-April/000003.html](https://lists.isc.org/pipermail/dlv-announce/2009-April/000003.html)


Good luck.

---

### Post by bapoumba on 2009-05-21
Threads merged.
We will not provide support regarding school work, sorry. Closing the thread.

---

