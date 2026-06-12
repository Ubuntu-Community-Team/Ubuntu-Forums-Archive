---
title: "Nagios Remote plugins issues"
date: 2007-08-08
forum: Server Platforms
---

### Post by holocaust on 2007-08-08
Hi all, i'm currently installing a NRPE module in my ubuntu Feisty Server Box, but i keep getting this message whenever i try to configure the service:

root@l-caracas:~/downloads/nrpe-2.8.1# ./configure
.
.
.
checking for closesocket... no
checking for socklen_t... yes
checking for type of socket size... size_t
checking for SSL... configure: error: Cannot find ssl libraries

Has anyone done this before?
Could give me a hand?

Thnaks on advance

---

### Post by aladd on 2007-08-16
I had the same problem on another flavor of Linux.  The fix was to install oppenssl and the development package.  NRPE need them to build.:)

---

