---
title: "Bind9 Won't Start (key issue?)"
date: 2009-02-11
forum: Server Platforms
---

### Post by etali on 2009-02-11
I was following some guides to set up wildcard CNAME records under bind9, but it wasn't working.  Somewhere along the line I've managed to totally break bind9.  I think it was when I created a new rndc key.

This is what happens:

/etc/init.d/bind9 restart
 * Stopping domain name service... bind                                         rndc: connection to remote host closed
This may indicate that
* the remote server is using an older version of the command protocol,
* this host is not authorized to connect,
* the clocks are not syncronized, or
* the key is invalid.
                                                                         [fail]
 * Starting domain name service... bind                                  [fail]


I tried purging then re-installing bind9 - it starts fine the first time after the install, but if I restart it manually, it errors.  

Any suggestions much appreciated!

---

### Post by etali on 2009-02-12
OK, now I feel like an idiot - rebooting fixed it.

Now to figure out why the wildcard subdomains aren't working.

---

