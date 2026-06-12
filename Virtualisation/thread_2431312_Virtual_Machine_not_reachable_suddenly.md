---
title: "Virtual Machine not reachable suddenly?"
date: 2019-11-14
forum: Virtualisation
---

### Post by adamknite22 on 2019-11-14
I am running Debian as a virtual machine on my Ubuntu install. It's our Concerto server if that helps any... but sometime between last night and this morning the virtual  machine is completely unreachable to anything. It can't be pinged or anything. However, the actual VM itself can ping out to the internet and local machines... just nothing can reach it. Like I said it was working yesterday perfectly and has been for the past year since it was setup.

Is there anything obvious I might be missing here? Nothing's changed since it was first setup  so I'm lost as to why it just stopped. I'm running it on Ubuntu 19.04 if that means anything..

---

### Post by ank2 on 2019-11-14
Do you run an adaptive firewall? If, first disable the firewall and see if you can reach the other machine.

---

### Post by adamknite22 on 2019-11-14
No. I don't run any firewalls on here.

---

### Post by SeijiSensei on 2019-11-15
Are you using bridged neteorking? A virtual machine using NAT is invisible to other hosts on the network.

---

