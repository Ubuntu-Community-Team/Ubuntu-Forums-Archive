---
title: "[SOLVED] Jabber and DNS"
date: 2008-08-17
forum: Server Platforms
---

### Post by shingalated on 2008-08-17
I have a Jabber server running on my network at home, open to the world.  It works from one person to another on the same server, but it can not talk to other Jabber servers.  I believe this is a DNS problem, something about adding SRV records.  The people that do my domain's DNS (zoneedit)  do not allow adding SRV records.  If I set up an internal DNS server and add a SRV record to that would that work?

---

### Post by shingalated on 2008-08-18
The jabber server I am using is openfire...

---

### Post by shingalated on 2008-08-21
Bump!

---

### Post by windependence on 2008-08-21
You don't need an internal DNS server. What is in your /etc/resolv.conf?

-Tim

---

### Post by shingalated on 2008-08-21
In my etc/resolv.conf is just

nameserver 192.168.0.1

Do I need to add something?

---

### Post by windependence on 2008-08-21
Try adding these nameservers:

```
namsserver 208.67.222.222
nameserver 208.67.220.220
```

Then restart your network and try again.

---

### Post by shingalated on 2008-08-21
I added those 2 DNS servers, but still my jabber server cannot send or receive messages with users on other servers such as jabber.org
It fails with a 404 code

---

### Post by shingalated on 2008-08-21
Solved!  Port 5269 was not forwarded to the jabber server (which is the port for server to server connections)

---

