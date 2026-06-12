---
title: "squid installation"
date: 2010-03-06
forum: Server Platforms
---

### Post by vksingh on 2010-03-06
Hi,

I have installed squid proxy in my ubuntu 9.04. I edited /etc/squid/squid.conf file and set the following port:

http_port 7010

But when I put the proxy in my browser, It is giving me the page from my localhost apache server when I try to open [www.google.com](www.google.com).

Please somebody send me the configuration of squid proxy server.

Thanks,

Vivek

---

### Post by labinnsw on 2010-03-13
Not claiming to be an expert, but here is what the experts have to say.

[https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)

---

### Post by toosneaky on 2010-03-16
why are you using 7010?

try

http_port 7010 transparent

let me know if this works

---

### Post by toosneaky on 2010-03-16
also - which version of squid are you using?

---

### Post by ibuclaw on 2010-03-16
Moved thread to Server Platforms.

---

