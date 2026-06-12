---
title: "How to isolate one machine on the lan?"
date: 2010-09-10
forum: Security
---

### Post by locoHost on 2010-09-10
Forgive me if this is simple. I'm not really a network security guy or anything. I'm setting up an FTP server on my lan. I know how to install the software and how to setup my router but still have a couple question for an expert...

1. Which version of Ubuntu should I install? Server?
2. How can I isolate this machine from the others on the lan?

Thanks a lot for your advice :-)

---

### Post by bodhi.zazen on 2010-09-10
> **locoHost said:**
> Forgive me if this is simple. I'm not really a network security guy or anything. I'm setting up an FTP server on my lan. I know how to install the software and how to setup my router but still have a couple question for an expert...

1. Which version of Ubuntu should I install? Server?
2. How can I isolate this machine from the others on the lan?

Thanks a lot for your advice :-)

FTP is insecure, I advise vsftp or similar (proftp) or better ssh (scp / sshfs).

Server edition if this is a dedicated server.

Isolation how ? You can use your router (depending on your router) or iptables.

---

### Post by locoHost on 2010-09-10
Yes, I had planned to use vsftp :-)

Isolated in that, if someone would somehow gain access to the machine (not sure how but just in case) they could not access any other machine on my lan. Could I install gufw on the ftp box and block access to the other local ips? Or is there some simple way to do this?

---

### Post by bodhi.zazen on 2010-09-10
> **locoHost said:**
> Yes, I had planned to use vsftp :-)

Isolated in that, if someone would somehow gain access to the machine (not sure how but just in case) they could not access any other machine on my lan. Could I install gufw on the ftp box and block access to the other local ips? Or is there some simple way to do this?

You can do this with iptables or ufw.

iptables -A OUTPUT -d 192.168.0.1 -j ACCEPT
iptables -A OUTPUT -d 192.168.0.0/24 -j DROP

Assuming your router is 192,168.0.1 and your network is 192.168.0.0/24 , adjust accordingly.

If that works, use iptables-save and iptables-restore to save your rules.

---

### Post by Tylerjd on 2010-09-11
If you wanted added protection from people getting into your network, you could enable DMZ on your router, and point it at your machine. Basically, DMZ (standing from De-Militarized Zone) forwards all of the ports (of your router) you haven't already configured, to your server. So you will still want to have UFW, but it is just an added layer of security.

Further explanation: [http://en.wikipedia.org/wiki/DMZ_(computing)](http://en.wikipedia.org/wiki/DMZ_(computing))

---

### Post by HermanAB on 2010-09-12
ifconfig eth0 down

---

### Post by locoHost on 2010-09-12
> **HermanAB said:**
> ifconfig eth0 down

So funny :-/

---

