---
title: "Has anyone successfully used KNetworkManager with connecting to a wireless router?"
date: 2007-04-27
forum: The Cafe
---

### Post by wersdaluv on 2007-04-27
I just installed Kubuntu Feisty in a new partition and I cannot connect with KNetworkManager. I researched about it and it seems that many people cannot connect to their wireless routers with Kubuntu because of KNetworkManager. 

In my old partition where I had Feisty which was upgraded from Edgy, I could connect to the internet but not through KNetworkManager, but through wlassistant.

I'm just curious, has anyone successfully connected to a wireless router with KNetworkManager without manual configuration or other apps like wlassistant?

Oh... I almost forgot. This case is also similar to Ubuntu (GNOME desktop) Feisty. It has a new wireless lan detecting feature, but I never actually managed to connect with it. I had to use the manual configuration in order to connect. Has anyone managed to connect with the new wireless lan feature in Feisty?

---

### Post by fuscia on 2007-04-27
you probably need to open up /etc/network/interfaces and comment out everything, except...

[i]auto lo
iface lo inet loopback[/i]

edit: that's worked for me in the past. it may not be the solution, but it's easily undone if not.

---

