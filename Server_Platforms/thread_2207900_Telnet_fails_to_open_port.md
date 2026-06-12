---
title: "Telnet fails to open port"
date: 2014-02-25
forum: Server Platforms
---

### Post by Mr_H on 2014-02-25
I am setting up a server with a good old fashion MU on it.  The MU requires port 2511 to be open and accessible via telnet.  I have opened the ports, and can connect from the local host, but connecting from other computers fail.    Ubuntu 12.04, VPS but I've got full root access and have opened other ports (http, ftp, etc) without issues.

On the localhost
I have done: **ufw allow 2511**  (and ufw allow 2511/tcp).  
A ufw status verbose shows that the ports are open:  
```
2511                       ALLOW IN    Anywhere
2511/tcp                   ALLOW IN    Anywhere
```

**netstat -plntu** shows: ```
tcp        0      0 0.0.0.0:2511            0.0.0.0:*               LISTEN      16749/netmux
```
**nmap localhost -p2511** shows: ```
2511/tcp open  unknown
```
Telnetting to the port from the localhost works without problem.

However, from outside sources, I am unable to access the port, with IP or DNS.
**nmap serverIPAddress -p2511 -PN** returns: ```
PORT     STATE    SERVICE
2511/tcp filtered unknown
```


So my question is...what am I missing?  Could the port be blocked elsewhere that I'm not aware of?

Thanks muchly
Jon

---

### Post by Mr_H on 2014-02-25
Self 'solved'.  I dumped UFW and went with just doing everything via iptables.  Once I did that, it worked.  I'm guessing there was something UFW was doing that was 'wrong'....but hey, fixed it. Yaay.

---

