---
title: "Vbox: Getting wireless to work, Ubuntu host, XP guest"
date: 2009-09-05
forum: Virtualisation
---

### Post by humphreybc on 2009-09-05
Hi there,

How do I get Windows XP to see my wireless connection from Ubuntu when I have XP set up as a guest on my Ubuntu 9.04 system?

The ethernet port works fine but I have tried a few settings for wireless and can't seem to make it work.

Cheers,
Benjamin

---

### Post by Perryg on 2009-09-05
Assuming that your Ubuntu can see and use the wireless connection it should be available as a selection in the guest setting under network.  If you plan to use both I would set it up as a second adapter and then you can select which one you want to use.

---

### Post by humphreybc on 2009-09-05
Yup thanks I got it working by using bridged with wlan0.

Cheers

---

