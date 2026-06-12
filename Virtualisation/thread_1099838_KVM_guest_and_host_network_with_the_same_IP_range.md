---
title: "KVM guest and host network with the same IP range?"
date: 2009-03-18
forum: Virtualisation
---

### Post by MirkoHuf on 2009-03-18
Hello users,

i have a problem with kvm network settings and a Windows 2003 guest system. I want that the windows guest are in the same IP range that all other physical systems - for example the host with eth0 has 10.4.9.33. What I want is that the guest became 10.4.9.107.

I try it with "bridging" but that is not what I need - i can ping the 10.4.9.XX from the guest without any problem - but that is not exactly what I want because the guest has a 192.168.122.1.

Have anybody an idear how can I solve this problem?

Thanks
Mirko

---

### Post by bodhi.zazen on 2009-03-18
The only way I know to do this is to bridge your network card and use a tap.

I am curious as to why you say bridging is not what you need, bridging is exactly what you need ;)

---

### Post by MirkoHuf on 2009-03-19
Ohh - mm I play again with the bridging options and now it works. I think I forget to remove the bonding param from the interfaces configuration file.

Thanks for your reminder :-)

---

### Post by Schorschi on 2009-04-05
In fact, I am working on bridging mutliple NICs, to try to get what VMware does with bonds on vSwitches.  We need redundent networking, so we need bridging on top of teaming (a.k.a active/active bond).

---

