---
title: "Firestarter question on wired and wireless..."
date: 2008-12-12
forum: Security
---

### Post by ooobooontooo on 2008-12-12
Hi,

I'm using firestarter to configure my iptables on my laptop. I switch often between using wireless and my wired network. I notice that when I do switch, firestarter doesn't "start the firewall" because the device it's looking for (eth0 for wired connection and wlan0 for wireless) is not found. This is because I had previously been using a different type of connection and it fails to recognize it. Is there way for firestarter to automatically notice which sort of connection it's using? Thanks in advance.

---

### Post by bodhi.zazen on 2008-12-12
No, this is an issue with firestarter, it really can not handle complex network configurations.

Firestarter is no longer maintained and I suggest you change over to UFW

If you want a gui, use gufw

You will have to remove (purge) firestarter.

---

### Post by ooobooontooo on 2008-12-12
Thanks.

---

