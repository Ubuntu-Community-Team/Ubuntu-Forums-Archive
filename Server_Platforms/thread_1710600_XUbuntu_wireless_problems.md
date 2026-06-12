---
title: "XUbuntu wireless problems"
date: 2011-03-20
forum: Server Platforms
---

### Post by amcnerney13 on 2011-03-20
Hey everyone!

I have recently converted my old desktop computer into a server (using the ubuntu server 10.10 install disk), installed xubuntu, and have installed the driver for my WPN111 usb antenna using ndiswrapper. I then installed wicd to connect to my home network (with a WPA2 passkey). Anyways, it works great... with one major annoyance – whenever I reboot (with "sudo reboot") the computer, the wireless configuration isn't detected at all. 
```
$ iwconfig
lo     no wireless extensions
eth0   no wireless extensions
```
The only time it works is when I turn my computer off and manually turn back it on... and then "iwconfig" gives me a third entry: wlan0. The wireless then (and only then) works like a charm. The problem is, I want to be able to access this server away from home, and of course in that situation I cannot manually reboot it. Please help!

---

### Post by amcnerney13 on 2011-03-20
Alright, I sort of figured out the problem – this is happening because the power to the antenna isn't being cut when the system is rebooted. Is there any way to cut the power from the command line? Or somehow fix this so that it will not need to have the power shut completely off?

---

