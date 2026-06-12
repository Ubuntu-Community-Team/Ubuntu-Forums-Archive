---
title: "How to create network interface virbr0?"
date: 2018-03-27
forum: Virtualisation
---

### Post by eezacque on 2018-03-27
I have happily run a virtual machine with functional networking for years, and I just found out the upgrade to Ubuntu 17.10 broke networking, due to network interface virbr0 missing. I cannot remember I ever created this interface, but I need to get it back. Any clue?

---

### Post by TheFu on 2018-03-27
I don't have any 17.10 stuff here. Only use LTS myself, but I do manually create bridges for each physical NIC in my VM hosts using normal Linux bridge methods.  With 17.10, I understand they deprecated the "interfaces" file and use something called NetPlan.  I'd begin my research there.

Sorry, but that's all I got.

---

