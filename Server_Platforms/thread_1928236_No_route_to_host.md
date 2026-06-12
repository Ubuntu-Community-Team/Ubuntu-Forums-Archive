---
title: "No route to host"
date: 2012-02-19
forum: Server Platforms
---

### Post by perfecti0n on 2012-02-19
Hello!

I'm trying to learn about web servers and I am at the moment trying to serve multiple domains using virtual hosts on Apache2. I am getting a **no route to host** error.

Googling didn't really turn up a solution to my problem but it would seem it is a problem with the network or if I understood correctly, with the firewall.

I am using iptables and you can see my rules here:
[http://cl.ly/0p1W0h3i252o1O2t2A0P](http://cl.ly/0p1W0h3i252o1O2t2A0P)

Any idea what could be wrong? Ask if you need more information.

---

### Post by Iowan on 2012-02-19
Dunno i you're using IP- or name-based virtual hosts. I haven't managed to get multiple hosts going, but I think my problem is in the DNS. [Here]("http://httpd.apache.org/docs/2.0/vhosts/examples.html") is one article  I've been using, and [another]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html").

---

### Post by perfecti0n on 2012-02-19
I am using name-based virtual hosts. Thanks for the links, I'll go through them and report back.

Are you also having the same error (113)?

---

### Post by Iowan on 2012-02-19
> **perfecti0n said:**
> IAre you also having the same error (113)?Machine is at work - I'll try to check tomorrow.  I haven't tried adding "alias" in the client **hosts** file.

---

### Post by perfecti0n on 2012-02-20
It's really weird because I can browse the directories.
But when I try to open the /var/www/site/htdocs it show the no route to host error.

I can't seem to find anything wrong with the configuration.

---

### Post by volkswagner on 2012-02-20
Some commands to run for each of your domains.

```
host yourdomain.com
```

```
dig yourdomain.com
```

```
ping yourdomain.com
```

If the server is inside your lan check using open port tool

From LAN connected machine, navigate to canyouseeme.org and check port 80.

Also can you navigate to the any site using server's internal ip and external(public) ip?

---

