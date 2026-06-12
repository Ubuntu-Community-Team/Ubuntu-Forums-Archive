---
title: "TLS Master / Slave replication - Ubuntu 20.04 Mariadb 13.1?"
date: 2020-08-25
forum: Server Platforms
---

### Post by 2td-8ndrecy-y5m on 2020-08-25
Hi,

I have messed around with a lab environment that should be the backend for our powerdns servers.

But I can not wrap my head around SSL/TLS replication in mariadb.

I have tried to make notes when installing and iterate to this: » [https://gist.github.com/falkowich/690e36b988a7c4c23802d7aba6b3f347](https://gist.github.com/falkowich/690e36b988a7c4c23802d7aba6b3f347)

I get the replication going, but I can't really verify that the data in motion is encrypted with SSL/TLS.

Any takers on this?

--
Regards Falk

---

### Post by LHammonds on 2020-08-25
Use Wireshark to look at the data from the source IP and target IP.

---

