---
title: "Xen Network Configuration"
date: 2013-10-08
forum: Virtualisation
---

### Post by sideaway on 2013-10-08
I'm followng the Ubuntu Xen documentation here:

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

And am up to this point;

```
Edit /etc/network/interfaces, and make it look like this:

[CODE]auto lo
iface lo inet loopback

auto xenbr0
iface xenbr0 inet dhcp
    bridge_ports eth0

auto eth0
iface eth0 inet manual
```[/CODE]

However once I do this, my networking completely fails to load and cannot start the daemon. I rebooted the machine and it hung until the daemon timed out and it booted without networking support. I managed to use another session to edit the interfaces file to return it to my previous configuration of;

> auto lo
iface lo inet loopback

It also killed Unity temporarily for some reason... Not sure what happened there. Anyone have any ideas? I'm guessing I have to specifiy wlan perhaps?

My machine is a laptop; HP Elitebook 8460p, 6gb RAM, i5-2410M, HD 4000.

Cheers,

---

