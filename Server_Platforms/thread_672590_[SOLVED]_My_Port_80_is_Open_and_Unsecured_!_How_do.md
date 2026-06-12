---
title: "[SOLVED] My Port 80 is Open and Unsecured ! How do i Make it Secure ?"
date: 2008-01-19
forum: Server Platforms
---

### Post by pat_pat on 2008-01-19
I run a Firewall Test at [http://probe.hackerwatch.org/probe/probe.asp](http://probe.hackerwatch.org/probe/probe.asp) and It show me that Port 80 (HTTP) is Open and Unsecure . How do I secure it ? :(

---

### Post by Joeb454 on 2008-01-19
I believe that if you close port 80, you'll lose your internet connection

---

### Post by smartboyathome on 2008-01-19
Are you running a server? That port is the one you want open, otherwise people won't be able to access your server.

---

### Post by pat_pat on 2008-01-19
I don't run a server

---

### Post by GavinZac on 2008-01-19
> **pat_pat said:**
> I don't run a server

what applications do you use which may interact with the outside world?

---

### Post by Steveway on 2008-01-19
What happens if you follow this link?
[https://localhost:80/](https://localhost:80/)

---

### Post by bwhite82 on 2008-01-19
It is only open when you are actively surfing (or scanning your computer from the internet as it were). If you use nmap on yourself, and are not surfing, then the port should be closed.

---

### Post by pat_pat on 2008-01-19
Before, Port 80 is Secure , When I install Firestarter the port becomes Open

---

### Post by bwhite82 on 2008-01-19
If by 'secure' you mean filtered, then yes. That was probably the case. However, it was still open. Ubuntu is shipped pretty secure by default and filters all ports.

---

### Post by chrisccoulson on 2008-01-19
By default, Ubuntu is wide open, but there are no services running on port 80. The 'open' result suggests that the you're running a service which is listening for connections on that port (web server?). On a default installation, your result for port 80 should be closed (the port will be open, but nothing is listening for a connection). With Firestarter installed, I'd probably expect you to get a secure result, unless you've opened up the port in the settings.

Are you defaintely sure you're not running a web server?

If you do ```
nmap localhost
``` ...does it list port 80 as being open? If it does, then there is a good chance you are running a web server. What is the output of ```
sudo iptables -L
```

---

### Post by PriceChild on 2008-01-19
Your router's webconfig is probably what's being shown as open.

This "shouldn't" be a problem as ACLs will prevent anyone not on the LAN from viewing it.

---

### Post by warrior24 on 2008-01-20
Pretty cool link I am all secure.

---

