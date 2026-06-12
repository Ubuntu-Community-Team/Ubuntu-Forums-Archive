---
title: "Setting fix IPAddress and Subnet for server"
date: 2009-12-02
forum: Server Platforms
---

### Post by ishfady on 2009-12-02
Hi

I have just installed Ubuntu 9.10. Currently it has dynamic IPAdrress and Subnet. It get IPAddress from DHCP. I would like to set Static IPAddress and Subnet for my server.

Please could someone help me, how to set static IPAddress and Subnet Ubuntu server.

Many thank

---

### Post by Vegan on 2009-12-02
```
sudo nano /etc/network/interfaces
```

And assign the needed stuff for static addresses.

---

### Post by Iowan on 2009-12-02
Another option, depending on your DHCP server, is to configure it to issue a static lease to your server - based on MAC address.

Forgot to mention - the static lease should be outside the lease range of the DHCP server - but still inside the subnet.

---

### Post by BkkBonanza on 2009-12-02
You should use the static lease method on your DHCP server. If you have more then one machine than manually entering it in /etc/network/interfaces doesn't allow for other machines on the LAN that could result in IP address conflict. If every other machine uses DHCP then simply telling the DHCP server to assign a static lease to a certain MAC address ensures you always get that IP for that machine. Most routers have a way to add this assignment by MAC address.

---

