---
title: "Virtualisation of network interfaces with same IP"
date: 2018-05-23
forum: Virtualisation
---

### Post by iwetzel on 2018-05-23
Hi,  I do have a server for some test actions which has 32 physical interfaces. I really need them physically.  But for my test actions I need a application set started for each interface with same IP and routing infos.  Usually I would use kvm but isnt that to much for just separating the interfaces from each other... Docker seems not to be an option because its  L7  optimzed virtualisation. Or not ?  What would you suggest to be a ressource gently virtualisation for such things.  BTW one example of the app would be a webbrowsing app started on each interface to connect to a  DSL Modem with default ip (192.168.1.1) and check the webinterface

---

### Post by TheFu on 2018-05-23
Welcome to the forums.

Assuming you have a switch that is capable of bonding that many interfaces under a single IP, then just follow the Linux bonding guide.  [https://wiki.linuxfoundation.org/networking/bonding](https://wiki.linuxfoundation.org/networking/bonding)  If the switch doesn't support the correct protocols, trying to put 2 interfaces on the same IP will be bad, very bad.

---

