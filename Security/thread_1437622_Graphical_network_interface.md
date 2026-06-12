---
title: "Graphical network interface"
date: 2010-03-24
forum: Security
---

### Post by fra1986 on 2010-03-24
Hello everybody,

I'm a Belgian student in internship that must enable 802.1X _wired_ security on HP switches.

I am running some tests with an 9.04 version and I have got serious problems with the Graphical network interface concerning 802.1X TLS parameters.

It seems that Ubuntu doesn't care about the parameters that I set with the graphical mod.

Do you know how to configure 802.1X into the network/interfaces file for TLS authentication? 

It's maybe an other configuration file?

Thanks for help an sorry about my poor knowledge in English.

---

### Post by cdenley on 2010-03-24
I think if I remember correctly, there was a bug in the NetworkManager applet where you needed to delete an automatically configured interface then re-add it in order to reconfigure it. I don't remember if that was on 9.04 (which isn't the latest release). Also, if the interface is configured in /etc/network/interfaces, then it cannot be configured from the NetworkManager applet.

---

### Post by fra1986 on 2010-03-24
Thanks for your help, i will explore this idea :D

---

