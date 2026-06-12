---
title: "Finding out IP details"
date: 2008-07-25
forum: Server Platforms
---

### Post by basicxman on 2008-07-25
I'm trying to find out all my IP details, including normal address, broadcast, network, netmask, and gateway

I know of ifconfig but I'm not sure which detail is which :D Yes, I'm a linux noob.

---

### Post by bab1 on 2008-07-25
Try```
sudo network-admin
```

From the terminal.

---

### Post by basicxman on 2008-07-25
is there a text based version of that or will i have to install the ubuntu-desktop GUI?

---

### Post by Uluen on 2008-07-25
```
# ifconfig
```
**Mac:** HWaddr 00:1b:21:1c:0e:7b
**IP:** inet addr:192.168.1.2
**Broadcast:** Bcast:192.168.1.255
**Netmask:** Mask:255.255.255.0

```
# route
```

---

### Post by basicxman on 2008-07-25
thanks to both of you!!  lol i also should've done man ifconfig to check it out :D

---

### Post by SeijiSensei on 2011-02-01
If you're behind a masquerading firewall router, like most everyone is these days, web sites can only tell you about your external IP address.  Your machine itself may have an entirely different address, often something in 10/8 or 192.168/16. The OP is (I believe) asking about the address on a machine behind the firewall where the commands ifconfig and route are the most useful tools.

---

### Post by Iowan on 2011-02-01
Closed.

Check the date... ;)
Hopefully OP has found the answer in the past 2.5 years.

---

