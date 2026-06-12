---
title: "Change server ports"
date: 2008-04-20
forum: Server Platforms
---

### Post by quikone8 on 2008-04-20
I have installed Citadel mail server along with webcit and I am close to getting it running correctly.  One problem is I confiqured webcit to run on port 8080, how do I change it back to port 80?

---

### Post by ikonia on 2008-04-21
edit the config file ? change the port varible back to 80 ?

---

### Post by Wizard of Aahz on 2008-04-21
Might this help?

[http://www.citadel.org/doku.php/documentation:cmdman:webserver?s=webcit%20server%20port](http://www.citadel.org/doku.php/documentation:cmdman:webserver?s=webcit%20server%20port)

Enjoy using citadel.
-Aahz

---

### Post by HermanAB on 2008-04-21
Here is one trick:
/sbin/iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080

Put that at the end of /etc/rc.d/rc.local

Cheers,

Herman

---

### Post by Oldsoldier2003 on 2008-04-21
> **HermanAB said:**
> Here is one trick:
/sbin/iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080

Put that at the end of /etc/rc.d/rc.local

Cheers,

Herman

slick ;) the idea never even crossed my mind.

---

### Post by HermanAB on 2008-04-21
Sometimes I wonder what I'll do without netfilter on Linux.  I use the same iptables redirect trick to provide an extra listener on port 2525 to allow mail clients to get past ISP blocks of port 25.  (Although it is better to enable SSL, which uses a different port, which is usually not blocked and then it is secure too).

---

