---
title: "DNS Error"
date: 2005-09-02
forum: Server Platforms
---

### Post by soon82 on 2005-09-02
Once I type the nslookup at root terminal. it give me the result.

root@ubuntu:~ # nslookup
> server
Default server: 202.188.0.133
Address: 202.188.0.133#53
Default server: 202.188.1.5
Address: 202.188.1.5#53
> /
Server:         202.188.0.133
Address:        202.188.0.133#53

** server can't find /: NXDOMAIN
>

---

### Post by robert_pectol on 2005-09-05
> 
> /
Server:         202.188.0.133
Address:        202.188.0.133#53

** server can't find /: NXDOMAIN
>
And what exactly were you expecting to get back from the server, when looking up, "/", that you didn't?  Just curious.

---

