---
title: "freeradius not working with sqlippool"
date: 2011-07-26
forum: Server Platforms
---

### Post by kagisos on 2011-07-26
Hi,

I keep getting the following when i include the sqlippool module on freeradius:

> freeradius: symbol lookup error: /usr/lib/freeradius/rlm_sqlippool.so: undefined symbol: sql_get_socket
The funny thing is that the sql module works fine.. 
if i include that and exclude sqlippool, it's ok.
I'm running FreeRADIUS Version 2.1.0 on Ubuntu, 
installed from package: apt-get install freeradius and
apt-get install freeradius-mysql

Please help..

---

