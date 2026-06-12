---
title: "site blocking in ubuntu server ?"
date: 2010-11-21
forum: Server Platforms
---

### Post by talaljavaid on 2010-11-21
Hi evey one, ihave a windows server and i am thinking to put a ubuntu server also on the network, for data storage only, but i was thinking if i could also use it as a internet fire wall , like i might need to block some sites for some users, is it possible ?

---

### Post by headvampyre@hotmail.co.uk on 2010-11-21
yeah. this should be possible with samba, dansguardian and squid/tinyproxy.are you using a domain  or a worksgroup? samba can work in both of these for filesharing, it cant act as an AD DC yet, but it can join as part of a domain. basically to use dansguardian (for content filtering) you need to use a proxy server, the best ive used on a linux based os would be squid, but for a low end machine id recommend tinyproxy.

---

### Post by bmathis on 2010-11-21
Check out [Zentyal]("http://www.zentyal.org/") (formally called ebox-platform). It can act as a DC, firewall, and filter (plus a lot more); and is run ontop of Ubuntu.

---

