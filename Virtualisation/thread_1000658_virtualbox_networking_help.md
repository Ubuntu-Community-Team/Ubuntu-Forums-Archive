---
title: "virtualbox networking help"
date: 2008-12-03
forum: Virtualisation
---

### Post by RavUn on 2008-12-03
I'm on a wireless laptop and I've been able to connect my guest machines after installing the guest additions but is it possible to "share" my laptop's connection with the guest machine without the guest additions?

I've installed knoppix-std and I cannot figure out how to install the guest additions on it and I cannot connect to the internet, either.  I always enable the networking in the virtualbox settings but the guest machine never connects until I install the guest additions... is that how it's supposed to be?

---

### Post by bodhi.zazen on 2008-12-03
the problem will be with wireless. NAT should work "out of the box" but if you want to bridge your wireless card you may have problems. 

I am not sure you can bridge with virtualbox, but you can bridge your wireless card with VMWare.

---

