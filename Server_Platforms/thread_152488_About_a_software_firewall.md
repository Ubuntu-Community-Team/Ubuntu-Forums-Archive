---
title: "About a software firewall"
date: 2006-03-30
forum: Server Platforms
---

### Post by Ob1 on 2006-03-30
I have a quite good firewall in my router, is that enough? or should i also get a software one like firestarter?

---

### Post by Darkriser on 2006-03-30
firestarter is basically just a graphical tool for iptables maintenance, which is the best firewall implemented already in your kernel. so you already HAVE firewall - type `man iptables` in console for more info.
ok, firestarter is not only a frontend tool for iptables - it adds some more features like dynamic firewalling, so i recommend installing it. (i also have hardware router with firewall + firestarter)

---

