---
title: "VMware, Network Interface Broken"
date: 2010-03-07
forum: Virtualisation
---

### Post by benomg on 2010-03-07
The NAT connection was working fine for a long time and now it, and any other connection type, doesn't work for some reason. I  don't recall doing anything related to the networking of the vm. There  is probably some very basic trouble shooting that I'm not doing.

I would copy and paste the ifconfig but I'm at loss as to how. I cannot ssh to it  and the player does not allow highlighting. But what I can tell you is that  ifconfig -a only shows "eth1" and "lo". Should it also be showing a  "VMnet" interface like the one I can see in my XP network connections that  has a row like...

inet addr:192.168.xxx.xxx Bcast:192.168.xxx.xxx Mask:255.255.255.0 ?

---
Ubuntu 8.04, VMware Player 2.05

---

### Post by dcstar on 2010-03-08
> **benomg said:**
> The NAT connection was working fine for a long time and now it, and any other connection type, doesn't work for some reason. I  don't recall doing anything related to the networking of the vm. There  is probably some very basic trouble shooting that I'm not doing.

I would copy and paste the ifconfig but I'm at loss as to how. I cannot ssh to it  and the player does not allow highlighting. But what I can tell you is that  ifconfig -a only shows "eth1" and "lo". Should it also be showing a  "VMnet" interface like the one I can see in my XP network connections that  has a row like...

inet addr:192.168.xxx.xxx Bcast:192.168.xxx.xxx Mask:255.255.255.0 ?

---
Ubuntu 8.04, VMware Player 2.05

Do you want to tell us **exactly** what the Host OS is and what the VM client is?

---

### Post by benomg on 2010-03-08
> **dcstar said:**
> Do you want to tell us **exactly** what the Host OS is and what the VM client is?

Sure. Windows XP Pro SP3 and VMware Player 2.0.5 build-109488.

---

### Post by dcstar on 2010-03-08
> **benomg said:**
> Sure. Windows XP Pro SP3 and VMware Player 2.0.5 build-109488.

So you have a VMware networking problem with your **Windows **system and you are asking about it in a Linux forum?

---

### Post by benomg on 2010-03-08
Yes i was.

---

