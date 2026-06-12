---
title: "New User Help..."
date: 2009-09-04
forum: Server Platforms
---

### Post by danserver on 2009-09-04
Hi.. Another neewbie here!!
 
Basically my problem is that when I install Ubuntu server it will not pickup my internet network connection. I have the computer's netwrok card plugged into the router with a grey crossover cable.   It is an oldish computer running a usb wireless internet connection before.
 
If anyone has any advice that would be great... Obviously i can't do alot without have an internet connection to update etc.
 
Thanks for your help :)

---

### Post by scragar on 2009-09-04
OK, first thing is to find out if the network card is picked up as hardware:
```
lspci | grep Eth
```
If it is then check if ifconfig can see it:
```
ifconfig eth0 up
```
If ifconfig doesn't complain attempt to connect using it:
```
dhcpcd eth0
```
If that doesn't complain your internet should be up, and I don't understand why it didn't work right away.

---

