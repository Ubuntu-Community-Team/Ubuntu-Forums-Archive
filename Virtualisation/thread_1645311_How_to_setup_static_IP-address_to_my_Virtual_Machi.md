---
title: "How to setup static IP-address to my Virtual Machine?"
date: 2010-12-14
forum: Virtualisation
---

### Post by rule-of-three on 2010-12-14
How to setup static IP-address to my Virtual Machine in VirtualBox?

---

### Post by bodhi.zazen on 2010-12-16
You set a static ip address in the guest the same way you would on a physical machine.

So it depends on what OS you are running as a guest.

Debian / Ubuntu :

[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

Other guests vary.

---

### Post by leuribe2 on 2010-12-17
Don't forget to change your VM network connection to bridge if you want it to be in your network...

---

### Post by HermanAB on 2010-12-19
In the host, set the network to Bridge mode.
In the Client, set the network IP address, netmask and default route to whatever you want.

---

### Post by rule-of-three on 2010-12-19
I tried that but it not works?

What do mean by client?

I can only took connect to my Red Hat Enterprise Linux 6 Virtual Machine over VNC/SSH.

When I set a IP-address to network configuration then internet connection is lost.

---

