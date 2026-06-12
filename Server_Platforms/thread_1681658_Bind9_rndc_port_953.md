---
title: "Bind9 rndc port 953"
date: 2011-02-04
forum: Server Platforms
---

### Post by bonethepawn on 2011-02-04
Eh Okay so I've ran into this problem with trying to set up a DNS on my Ubuntu server.
I'm doing this so that I can have Kerberos on my systems but when I installed bind and configured all of the settings, I ran into a problem where it fails to start.

```
# /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                rndc: connect failed: 127.0.0.1#953: connection refused
                                                                 [ OK ]
 * Starting domain name service... bind9                         [fail] 

```Could anyone help me on fixing this problem. Spent about the last 4 hours searching for a solution on the Internet.

---

### Post by rudelgurke on 2011-02-05
Is your configuration correct ?

Running bind with /usr/sbin/named -dg will give some debug info on what might be wrong.

---

