---
title: "USB modem"
date: 2009-01-12
forum: Server Platforms
---

### Post by Stunts on 2009-01-12
Hello everyone!

I've just put together a mini ITX machine to use as a server for backups, samba shares, and home network routing (since my router is a good access point, but lousy as a router).
I installed ubuntu server 8.10 and setup eBox without any major issues.
When I did this I was connected to the internet via wireless router using my Ethernet card (eth0).
Since now I'm trying to setup routing trough the server box, I'm trying a direct connection to the modem using a USB port (the modem supports both Ethernet and USB connections), but I'm getting no joy there.

Why, you ask? 
Because when I connect the USB modem, no new network interfaces appear. Using the ubuntu desktop edition, all I had to do was plug it in and I had instant Internet.
My goal setup is:
Modem ---> Server ----> Wireless Router (as access point only) ----> Client computers on home network.
This seems to be quite simple to setup using eBox, but getting the modem to work from USB ports doesn't seem so easy.

Any sugestions on what to do?

I'm already somewhat profficient with the CLI (I setup samba using only nano, before I knew about eBox), so I can perform some more advanced tasks if required.

Thanks in advance.

Stunts

---

### Post by Stunts on 2009-01-14
Hi!
I have found a solution to my problem.
After hours of googling, nobody seemed to have the same problem, so I tought: "Maybe it's not a problem...".
Turns out all I had to do was```
sudo ifconfig eth1 up
```Simple hu?
Expect more help requests as I start discovering the world of ubuntu server! =-)

Edit: Can't mark this solved?

---

