---
title: "FIrestarter firewall"
date: 2010-09-05
forum: Security
---

### Post by Vigh on 2010-09-05
Hi I added firestarter into the autostart list, but upon start-up it says root privelidges are required to initialize firestarter, do i need to do this? Or is it automatically loaded on start-up. I just thought it would be handy to have the firestarter icon in the top menu bar on start-up. I don't wish to use a root login due to security problems involved. If it is not necessary to have firestarter automatically start up and the firewall is always going in the background I will just remove it from the autostart up list. Any help appreciated.

Ant

---

### Post by bowens44 on 2010-09-05
firestarter is just a GUI for iptables(the actual firewall). iptables is running in the background whether or not firestarter is active.

---

### Post by dino99 on 2010-09-05
[http://1000umbrellas.com/2010/04/29/how-to-set-up-the-firewall-using-ufw-on-ubuntu-lucid-lynx-server](http://1000umbrellas.com/2010/04/29/how-to-set-up-the-firewall-using-ufw-on-ubuntu-lucid-lynx-server)

something outdated, but:

[http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html](http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html)

---

### Post by CharlesA on 2010-09-05
Please don't use firestarter, it's no longer in development and UFW/GUFW are better replacements.

---

### Post by Vigh on 2010-09-06
Thanx I will use UFW from now on. Just want to block some specific ports thats all. Cheers.

---

