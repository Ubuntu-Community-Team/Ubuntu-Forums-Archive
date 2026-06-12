---
title: "Ubuntu server+squid modify swapiness?"
date: 2015-09-30
forum: Server Platforms
---

### Post by sergio46 on 2015-09-30
I use Ubuntu server 14.04 LTS with 50 clients in SQUID 3.3.8
The server has 8GB of RAM.
I want to know if it convenient to modify the swapiness value to, for example, 10 or 20...
many thanks

---

### Post by SeijiSensei on 2015-09-30
I maintain a gateway that runs Squid, MailScanner, c-icap, Postgres, ntop and BIND in 8GB and has about 250 clients behind it.  I've never had to futz with swappiness.  Even with all that the server is using just under 1 GB of swap and reports a disk cache of over 3 GB.  Top reports a long-term load average of about 0.6; this is a dual-Xeon machine though.

---

