---
title: "Beta 19.10 can't set maual IPv4"
date: 2019-09-29
forum: Ubuntu Development Version
---

### Post by ubname on 2019-09-29
Hi I use ipv4 and have a couple of pc with static ip ( i refer static ip ) in ubuntu 19.10 I cannot set the static IP (via standard graphical gnome settings);
I can set all the values but cannot apply ( the apply button is not highlighted/active, I can only hit "cancel" ) al settings are ok, triple checked, is this a known bug?

thanks!

---

### Post by webaake on 2019-09-30
If you did a clean install maybe you're not in the group netdev anymore? Check with the command groups in terminal. If not check this link: [https://askubuntu.com/questions/341810/add-user-to-group-which-can-access-network-interfaces](https://askubuntu.com/questions/341810/add-user-to-group-which-can-access-network-interfaces)

But if you're really into static IP's why not manually edit the /etc/network/interfaces files? It looks something like this: > # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.xxx
gateway 192.168.1.1
dns-nameservers 66.212.63.228 66.212.48.10 //*EXAMPLES

---

### Post by ubname on 2019-09-30
I did a bit of "research", turns out it's actually a Gnome bug so hopefully it will be fixed soon thanks!

[https://gitlab.gnome.org/GNOME/gnome-control-center/issues/677](https://gitlab.gnome.org/GNOME/gnome-control-center/issues/677)

---

### Post by ubname on 2019-09-30
Hi it's a gnome bug, hopefully it will be fixed soon

---

