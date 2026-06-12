---
title: "Firewall on a latop with multiple interfaces"
date: 2009-04-25
forum: Security
---

### Post by avion on 2009-04-25
What is the best way to set up a firewall on my laptop which changes as the interface changes.  In other words sometimes I use the wireless connection and sometimes I use the wired connection.  I would like for the firewall to change dynamically as I switch my network interface.

Avi

---

### Post by celthunder on 2009-04-25
I believe iptables isn't interface specific...could be wrong though.

---

### Post by bodhi.zazen on 2009-04-25
> **celthunder said:**
> I believe iptables isn't interface specific...could be wrong though.

iptables is interface specific , lol

-i = input interface -o = output interface.

this is made use of by the gui and command line config tools as well.

See: [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by celthunder on 2009-04-25
Good to know for future reference, thanks.

---

### Post by avion on 2009-04-25
In the past I used firestarter and created a simple script in /etc/network/if-down.d and /etc/network/if-up.d directories to restart firestarter as the network interfaces are brought up and down.  It is a bit of a pain to remember to copy the scripts everytime I upgrade or install on a new computer and was hoping that something like this will be built into Ubuntu by default.

---

### Post by bodhi.zazen on 2009-04-25
Ubuntu now comes with ufw . gufw is the gui front end.

---

