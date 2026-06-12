---
title: "User-Mode Linux Networking"
date: 2012-04-16
forum: Virtualisation
---

### Post by gardnan on 2012-04-16
I have been trying to set up a network connection to a Debian User Mode Linux system running on my machine. Essentially I have followed the steps in this guide: [http://user-mode-linux.sourceforge.net/network.html](http://user-mode-linux.sourceforge.net/network.html)

I have ensured that TUN/TAP capability is enabled of both the kernels of the host machine and the guest kernel. However, the command mentioned in the tutorial 'ifconfig tap0 192.168.0.253 netmask 255.255.255.255 up' is giving me the error 
```
SIOCSIFADDR: No such device
```I thought then that maybe I would have to create a tun device guest side, but after trying that, the network connection does not seem to work.

If anyone here had any experience with User Mode Linux Networking ans is willing to help, I would appreciate knowing exactly what the problem is.

---

### Post by gardnan on 2012-04-16
Alright, I feel like an idiot.

Some of the commands that I was following in the guide were actually host commands, not guest commands. It wasn't very clear. Sorry for not reading it thoroughly enough before posting.

---

