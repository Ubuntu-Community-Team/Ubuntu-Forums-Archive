---
title: "Random MAC address?"
date: 2012-02-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by callen41 on 2012-02-28
For whatever reason every time I reboot Precise I create a new wired connection with a new hardware address.  I'm up to fourteen of them at the moment.  To my knowledge nothing was modified between 11.10 and 12.04 alpha 2.

I realize its an alpha and beta is on its way but I'm just curious as to what could be causing this to happen.

---

### Post by dino99 on 2012-02-29
how do you check them ? how is your config ?

---

### Post by enjoijesus94 on 2012-02-29
can you give us more details
ill be glad to help

---

### Post by callen41 on 2012-03-01
What information should I provide?

---

### Post by effenberg0x0 on 2012-03-01
> **callen41 said:**
> For whatever reason every time I reboot Precise I create a new wired connection with a new hardware address.  I'm up to fourteen of them at the moment.  To my knowledge nothing was modified between 11.10 and 12.04 alpha 2.

I realize its an alpha and beta is on its way but I'm just curious as to what could be causing this to happen.

As far as I know, the only possible ways to do it are:
- Install macchanger, associate it with if-pre-up (change MAC at each connection) or init (change MAC at each boot).
- Have the IFACE off Network-Manager and directly set at /etc/network/interfaces, and script something to randomly write a hwaddress there.

In any case, unless you're wardriving, it's useless :)
I'm gonna guess you went for option 1. In that case, try:
```
sudo apt-get remove macchanger 
if [[ -e /etc/init.d/macchanger* ]]; then sudo rm -rf /etc/init.d/macchanger*; fi
if [[ -e /etc/init/macchanger* ]]; then sudo rm -rf /etc/init.d/macchanger*; fi
if [[ -e /etc/network/if-pre-up.d/macchanger* ]]; then sudo rm -rf /etc/network/if-pre-up.d/macchanger*; fi
sudo sed -i 's/hwaddress/#hwaddress/g' /etc/network/interfaces

```

Remove all your wired connections from Network-Manager. See if it can use only one from now on.

Regards,
Effenberg

---

