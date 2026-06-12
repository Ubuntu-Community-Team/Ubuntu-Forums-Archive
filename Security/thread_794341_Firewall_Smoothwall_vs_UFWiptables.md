---
title: "Firewall: Smoothwall vs UFW/iptables"
date: 2008-05-14
forum: Security
---

### Post by snuza on 2008-05-14
I would like to know if i am opening up security holes if i replace my Smoothwall machine + windoze server (2 separate machines) with a single Ubuntu server machine? I mainly use my Smoothwall (besides minimising chances of attacks) to monitor bandwith usage on individual PCs on the LAN. Also to (try to) prevent PC's on the LAN accessing undesireable sites (porn, etc). And i use port forwarding too. That's about it - nothing complicated!! So... will i be able to sleep peacefully at night knowing my files are as safe as they are with Smoothwall?? 

Greg

P.S. I'm relatively new to Linux.

---

### Post by mkoyle on 2008-06-22
iptables is quite capable, but when it comes clear down to it, you can remove UFW and iptables from Ubuntu and use Smoothwall in Ubuntu.  You could probably even copy most of your old config.

---

### Post by Trevor Ostrander on 2010-02-14
> **mkoyle said:**
> iptables is quite capable, but when it comes clear down to it, you can remove UFW and iptables from Ubuntu and use Smoothwall in Ubuntu. You could probably even copy most of your old config.
 
How do you install Smoothwall in Ubuntu?

---

### Post by cariboo on 2010-02-14
You run it in a vm, as it is a Linux distribution on it's own.

---

