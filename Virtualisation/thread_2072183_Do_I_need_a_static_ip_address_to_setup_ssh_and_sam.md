---
title: "Do I need a static ip address to setup ssh and samba in virtualbox"
date: 2012-10-17
forum: Virtualisation
---

### Post by thunderpenguin on 2012-10-17
My computer gets dynamic ip address from a router.

I want to setup servers in Virtualbox and connect to them from the host using ssh and share files between them with samba.

Is it possible to do this with dynamic ip address or would I need a static ip address.

---

### Post by BelJoost on 2012-10-19
I guess ssh and samba don't mind it being a dhcp issued ip. How would they know anyway. But it will probably matter to you. You'll have to check each time if the ip address has not changed. Far more easier to use a static ip.

---

### Post by CharlesA on 2012-10-20
If you have DNS setup correctly on your network and know the hostname, you don't have to worry about remembering what IP it is getting from DHCP. ;)

---

