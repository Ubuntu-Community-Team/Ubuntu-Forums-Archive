---
title: "UFW - My ports are filtered?"
date: 2009-10-15
forum: Security
---

### Post by kreggz on 2009-10-15
Hi,

Is it possible to change the behaviour of UFW to hide my PC from NMAP scans? I am using gufw to modify UFW.

At the moment if I can my pc from another pc I get:
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2009-10-16 12:36 CST
All 1697 scanned ports on xxx.xxx.xxx.xxx are filtered

Cheers,

---

### Post by cariboo on 2009-10-15
What's the problem? Everywhere you go can see your ip address.

---

### Post by Bucky Ball on 2009-10-15
... and if you are using a router the router is probably sending a 'fake' one for the whole network, not individual machines. Maybe cariboo can verify my thinking there ...

---

### Post by prshah on 2009-10-16
> **kreggz said:**
> 
At the moment if I can my pc from another pc I get:
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2009-10-16 12:36 CST
All 1697 scanned ports on xxx.xxx.xxx.xxx are filtered


You can set the default UFW rule to deny. Open a terminal (Applications-Accessories-Terminal) and give the command```
sudo ufw default deny
``` (If "deny" does not work, try "reject"; I forget which one is for stealth).

In GUFW you can enable this with the "Deny incoming traffic" option near the top of the window.

---

### Post by kreggz on 2009-10-16
Ok, thanks prshah I am a little closer however gufw isn't blocking ICMP, that is how nmap is finding me.

I guess I will have to do the rest at the CLI. Is there an easy way to do this?

---

### Post by rookcifer on 2009-10-16
DROP is the command for "stealth."  REJECT will send a RST packet.

Try something like:

```
iptables -P INPUT DROP
```

---

### Post by __p1n__ on 2009-10-16
As long as your machine is running then it's going to be visible.  Host status (up/down) is easily done with ARP even if ICMP, UDP, TCP packets are dropped.  If the host is detected to be up then the filtered status (on a port by port basis) is directly inferrable in the event of a non-response to a SYN, FIN, ACK, etc. packet (or RST or other active response.)

---

### Post by kreggz on 2009-10-17
thanks

---

