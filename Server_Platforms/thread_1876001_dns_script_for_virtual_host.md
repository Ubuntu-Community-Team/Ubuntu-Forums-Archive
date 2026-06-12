---
title: "dns script for virtual host"
date: 2011-11-05
forum: Server Platforms
---

### Post by 1885 on 2011-11-05
I'm setting up a test web server on a closed  network. 192.168.1.15
I want to set up virtual host using the same ip ( 192.168.1.15).
I'm using .com as a test zone.
Do I need to add an entry to db.root?
This in my script?  I can not get company0.com to work.
or [www.e.com]("http://www.e.com")
Any ideas?

$TTL    86400
com.               IN SOA  ns.e.com.    root.e.com. (
                                      2 ; serial ()
                                        3H              ; refresh
                                        15M             ; retry
                                        1W              ; expiry
                                        1D )            ; minimum
com.    IN      NS      ns.e.com.
e.com. IN A 192.168.1.15
[www.e.com]("http://www.e.com"). IN A 192.168.1.15
[www.ez.com]("http://www.ez.com"). IN A 192.168.1.8
ez.com. IN A 192.168.1.8
[www.ghost.com]("http://www.ghost.com"). IN A 192.168.1.11
ghost.com. IN A 192.168.1.11
company0.com.    IN A 192.168.1.15
[www.company0.com]("http://www.company0.com").    IN A 192.168.1.15

---

### Post by elico on 2011-11-05
i would recommend to opne new zone only for the [www.ez.com](www.ez.com) and to not touch the com. zone at all.

---

### Post by 1885 on 2011-11-05
> **elico said:**
> i would recommend to opne new zone only for the [www.ez.com](www.ez.com) and to not touch the com. zone at all.

thanks I'll give it a try.

I did get this script to work on a RedHat dns server.
I'm doing something wrong using Ubuntu :(

---

