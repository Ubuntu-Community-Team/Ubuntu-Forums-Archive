---
title: "ip tables"
date: 2009-04-02
forum: Security
---

### Post by num on 2009-04-02
hello,

how can i open a port in ip tables?

---

### Post by cdenley on 2009-04-02
How have you configured iptables to "close" the port? There are various ways to configure iptables.

---

### Post by bodhi.zazen on 2009-04-02
sudo iptables -A INPUT -p tcp --dport xx -j ACCEPT

xx = port number (ie 22 , 80, 443 , etc)

You can also use multiport.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by hyper_ch on 2009-04-02
if you did not mess with iptables you'd just need to start a server that listens on a given port.

---

### Post by The Cog on 2009-04-03
In a default installation, iptables is not blocking any ports. If you have configured iptables to block ports after installation, then you need to reverse or adapt your iptables/firewalls rules that you appplied.

If the client you are trying to use is telling you connection refused, then iptables is probably not blocking the port, and your problem is probably that there is no application listening for connections on that port.

---

