---
title: "winXP guest, networking issue"
date: 2010-06-20
forum: Virtualisation
---

### Post by larry.said on 2010-06-20
Hello everyone!  As this is my first post, I'll try not to make too much of a fool of myself. Here is my problem:  

   I have virtualbox installed running winXP guest in lucid host. Guest additions are installed and a host-only network was created in ubuntu. When I change settings in XP guest (via virtualbox) so that netowork adapter1 is enabled, I attached it to host network, but I don't see any networks in XP.  

 What I am trying to achieve is connecting my VM to the internet via my host wireless connection (by bridging the host-only network with my wireless network on my host).   

Any ideas?

---

### Post by xoomer.ap on 2010-06-21
Hi!
Why you not trying create a connection by NAT?

---

### Post by larry.said on 2010-06-21
I tried that, I attached the guest to NAT and still nothing

---

### Post by JustinR on 2010-06-23
Try changing it to bridged. This will change it to your current internet connection on your host, provided that you set the correct network hardware for VirtualBox to use.

---

