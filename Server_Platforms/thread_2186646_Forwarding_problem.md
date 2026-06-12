---
title: "Forwarding problem?"
date: 2013-11-08
forum: Server Platforms
---

### Post by oscar.vadillog on 2013-11-08
Hi all,

First of all sorry for my bad english. I will try to write my best.

My scenario is the next:

USB IPv6 device -------- (tun0) Computer 1 (eth0) --------- (eth0) Computer 2

I can ping6 from computer 1 to USB device and to Computer 2.

I can ping6 from Computer 2 to Computer 1.

But I can't ping6 from Computer 2 to USB device.

Some idea?

Best regards
Oscar

---

### Post by oscar.vadillog on 2013-11-08
I think that I need to forwarding eth0 to tun0 in Computer 1, but I am not sure, and I don't know how.

---

### Post by Roswebnet on 2013-11-08
Hi

did you reed this one:

[https://wiki.ubuntu.com/IPv6](https://wiki.ubuntu.com/IPv6)

---

### Post by SeijiSensei on 2013-11-08
Enable IPv6 packet forwarding in /etc/sysctl.conf, then reboot.

```
# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1

```

---

### Post by oscar.vadillog on 2013-11-08
I enable [COLOR=#000000][FONT=Ubuntu Mono]net.ipv6.conf.all.forwarding=1

[/FONT][/COLOR]But problems continue :(. I can't ping6 2001::3 since computer 2

[IMG]http://oscarvadillo.com/pfc/Captura.JPG[/IMG]

Any idea? Please

Best regards
Oscar

---

### Post by oscar.vadillog on 2013-11-09
I think that I can solve it with radvd, but I am not sure about them.

---

