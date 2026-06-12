---
title: "Serval Dial Up Internet Access?"
date: 2007-03-12
forum: System76 Support
---

### Post by steveneddy on 2007-03-12
Carl - I'm going to an area where the only internet connection will be through dial up connection. I gathered the old phone cable and plugged it into the modem jack, installed gnome-ppp and got absolutely nothing. 

It said that there wasn't a modem installed. But why the plug in the back of the pc case?

Please help. My only other option is to take an older desktop with a dial up modem with a known good configuration and make it a connection sharing modem and router for the internet. 

I hate doing that. 

-SE

---

### Post by MarkID on 2007-03-12
The problem with the built-in modems under Linux is not that there's a phone jack in the case, it's that most laptop modems are not hardware modems, and getting the wrappers and drivers to work on a software modem under Linux is a real pain.

Your best bet, and what has worked for me in the past, is to get a PCMCIA modem card (in other words, a hardware modem) for your Serval laptop.  That should work without a problem.

---

### Post by crichell on 2007-03-13
Mark is right - PCMCIA modems work great.  Internal softmodems are lightly supported (probably because not many people use modems these days - not the most fun project for a developer.)  We are working on softmodem support however.

---

### Post by steveneddy on 2007-03-14
Sigh - more hardware to buy.

---

