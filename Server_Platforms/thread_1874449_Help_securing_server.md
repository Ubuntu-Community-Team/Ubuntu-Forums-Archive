---
title: "Help securing server"
date: 2011-11-03
forum: Server Platforms
---

### Post by ScottG89 on 2011-11-03
Hey guys, I have a couple questions about securing a server.

I just installed Ubuntu server on my old computer so I can setup a webserver and have ssh on it as well. I was wondering if you have any tips/suggestions or web sites that will help me get it nice and secure. I will have it open to public so I can ssh from wherever and of course have the website open to public but before I do that, I was wondering about general setup of ipTables and anything else you can suggest for the web part of ssh part.

Also, I have my personal computer and web server hooked up on the same router (same outside ip), so I need to take that into consideration when securing the network/server.

the ssh is openssh by the way. Thanks in advance.

-Scott

---

### Post by HermanAB on 2011-11-03
My tuppence worth:
1. Ensure that ALL passwords are longer than 9 characters.
2. Add a rate limit rule to iptables to prevent DOS or brute force attacks.
3. Disable services that are not required.

That is really all I do on my servers.

> # General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

---

### Post by ScottG89 on 2011-11-03
Ok, thank you guys. Are iptables the only thing I should worry about. Or are there other security measures I should take.

-Scott

---

### Post by xpam on 2011-11-03
Hi

For the webserver in the case of the Apache you can found information about security here

[https://httpd.apache.org/docs/2.0/misc/security_tips.html](https://httpd.apache.org/docs/2.0/misc/security_tips.html)

Or in the page of the webserver that you use will find security tips

---

### Post by SeijiSensei on 2011-11-03
Scan your system from an external location using **nmap**.  If it finds open ports that you didn't open intentionally, figure out why.

---

### Post by linuxwin2 on 2011-11-04
> **SeijiSensei said:**
> Scan your system from an external location using **nmap**.  If it finds open ports that you didn't open intentionally, figure out why.

nmap -sS ipaddress
Or 
nmapfe - GUI
```
$ sudo apt-get install nmapfe

```

---

