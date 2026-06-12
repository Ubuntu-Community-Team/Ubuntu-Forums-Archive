---
title: "Bridged Networking with KVM"
date: 2008-04-16
forum: Virtualisation
---

### Post by SniperSlap on 2008-04-16
Is there any way to do something similar to bridged networking in VMWare using the handy config tools for KVM?

I run development servers on a development network and so it's preferred to not use NAT as that blocks machines from seeing them and is just a hassle if I actually tried to set up port forwarding.

My laptop supports promiscuous mode on both the wifi and the wired networks so I generally bridge to both and let whichever is connected work...

---

### Post by rajeshja on 2008-04-28
This interests me too. Did you figure out how to get bridged networking to work?

---

### Post by m.brinkers on 2008-05-11
See:

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

Martijn

---

