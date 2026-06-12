---
title: "The logic behind systemd's naming of devices"
date: 2016-02-29
forum: Ubuntu, Linux and OS Chat
---

### Post by grahammechanical on 2016-02-29
We might understand what eth0 or wlan0 represents but what about enp63s0?

Surprise, surprise, it is a systemd thing.

en = _e_ther_n_et. p = pci bus. 63 = anybody's guess. s = slot. 0 = first slot. It is obvious, really. Yes, really. :)

[https://github.com/systemd/systemd/blob/master/src/udev/udev-builtin-net_id.c#L20](https://github.com/systemd/systemd/blob/master/src/udev/udev-builtin-net_id.c#L20)

[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

> Starting with v197 systemd/udev will automatically assign predictable,  stable network interface names for all local Ethernet, WLAN and WWAN  interfaces. This is a departure from the traditional interface naming  scheme ("eth0", "eth1", "wlan0", ...), but should fix real problems.

Regards

---

### Post by SeijiSensei on 2016-02-29
Which "real problems" might those be?  in two decades of using Linux I never had any "problems" with names like eth0 and wlan0.  Now I'm going to need to run ifconfig all the time just to remember what the hell the adapter names are.

---

### Post by QDR06VV9 on 2016-02-29
> **grahammechanical said:**
> We might understand what eth0 or wlan0 represents but what about enp63s0?

Surprise, surprise, it is a systemd thing.

en = _e_ther_n_et. p = pci bus. 63 = anybody's guess. s = slot. 0 = first slot. It is obvious, really. Yes, really. :)

[https://github.com/systemd/systemd/blob/master/src/udev/udev-builtin-net_id.c#L20](https://github.com/systemd/systemd/blob/master/src/udev/udev-builtin-net_id.c#L20)

[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)



Regards
This was my hushed rants when it was in the development cycle..:D
And then ubuntu's systemd commands are slightly different than other distro's
It is a perpetual learning curve.. and i am **so not a fan** of the author of systemd.(Just my Opinion)
Regards

---

### Post by DuckHook on 2016-03-02
Odd... Mine just says:```
eno1
```...though I still don't know why that makes any more sense than *eth0*. Also, what's "predictable" or "stable" if there is already variance between graham's and mine?

---

### Post by mastablasta on 2016-03-02
the letters "th" caused mayhem with other programes. nothing worked as it should !!!!! :-)

now all is good. no more bugs in the OS.

---

### Post by DuckHook on 2016-03-02
> **mastablasta said:**
> the letters "th" caused mayhem with other programes. nothing worked as it should !!!!! :-)...but of course. Why didn't I think of that?> now all is good. no more bugs in the OS....for ever and ever. Amen.

---

