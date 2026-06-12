---
title: "Migrating a webserver to Ubuntu"
date: 2008-11-30
forum: Server Platforms
---

### Post by comandrei on 2008-11-30
I have a gateway machine that splits net to about 100 clients. 
The gateway was also a webserver (serving both clients behing the gateway and those from the internet). 
I now want to move the webserver to a dedicated machine, but can't figure out how to forward port 80 right to the new webserver.
It's important that both "inner" and "outer" clients can acces the webserver using the domain.tld hostname.
The gateway is running Debian Etch and the new webserver Ubuntu 8.04 Server

---

### Post by Philio on 2008-11-30
Which software are you using for the gateway?

---

### Post by comandrei on 2008-11-30
> **Philio said:**
> Which software are you using for the gateway?
[quote=comandrei]The gateway is running Debian Etch[/quote]
I already said

---

### Post by iler on 2008-11-30
If using iptables you could use something like this:
iptables -A PREROUTING -t nat -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.1.50:80
iptables -A INPUT -p tcp -m state --state NEW --dport 80 -i eth1 -j ACCEPT

Briefly explained here [http://www.debian-administration.org/articles/73]("http://www.debian-administration.org/articles/73")

---

### Post by comandrei on 2008-11-30
> **iler said:**
> If using iptables you could use something like this:
iptables -A PREROUTING -t nat -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.1.50:80
iptables -A INPUT -p tcp -m state --state NEW --dport 80 -i eth1 -j ACCEPT

Briefly explained here [http://www.debian-administration.org/articles/73]("http://www.debian-administration.org/articles/73")
Already tried. With these rules, clients outside can access the server but clients inside can't. For clients inside other websites work.

---

### Post by iler on 2008-11-30
I suppose that you are using private network based addressing for clients inside your network? What if you add this forward rule also for connections to your LAN network iface? Just a guess...

---

### Post by comandrei on 2008-11-30
```
iptables -A PREROUTING --dport 80 -s 192.168.0.0/255.255.0.0 -d public_ip_of_gatway -p tcp --to-destination 192.168.1.5:80 
```
Same thing

---

