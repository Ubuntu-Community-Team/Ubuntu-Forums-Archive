---
title: "setting up ftp in UCE server edition?"
date: 2009-08-17
forum: Ubuntu Christian Edition
---

### Post by stlsaint on 2009-08-17
so with dansG and all the different settings are there special instructions for making server edition a ftp for a website? and if not whats the best way to set one up?

---

### Post by david_kt on 2009-08-17
> **stlsaint said:**
> so with dansG and all the different settings are there special instructions for making server edition a ftp for a website? and if not whats the best way to set one up?

What you have to do is open the ports used by your ftp software. What is the software you are using?

DK

---

### Post by stlsaint on 2009-08-17
i plan on using vsftp or upftp...i have to double check with in repos i think...maybe spelled them wrong but its software alread in ubuntu...

---

### Post by david_kt on 2009-08-18
> **stlsaint said:**
> i plan on using vsftp or upftp...i have to double check with in repos i think...maybe spelled them wrong but its software alread in ubuntu...

You should insert below to /etc/init.d/ubuntu_ce_firewall
```
modprobe ip_conntrack
modprobe ip_conntrack_ftp 
iptables -A INPUT -p tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -p tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT
```

May be I would open those ports by default to make it easy.

DK

---

