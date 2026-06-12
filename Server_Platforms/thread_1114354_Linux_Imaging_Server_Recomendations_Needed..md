---
title: "Linux Imaging Server Recomendations Needed."
date: 2009-04-02
forum: Server Platforms
---

### Post by Mortus Pryde on 2009-04-02
My tech department has a Windows based imaging server that is in bad need of replacing and at minimal cost so I am revisiting Linux as an inexpensive alternative. I do not have much experiance with Linux, what little experiance I had was at least a decade ago. For our current server we are using Symantec Ghostcast on Windows 2000 server and loading the GhostCast Client via PXE to make images of our product with all drivers and essential software installed which are then Sysprepped removing the product key and SIDs from Windows as each machine has its own COA with product key. It also acts as our DHCP server and internet gateway which I may change and impliment it as a dedicated PXE and Image server with a dedicated gateway and DHCP Machine.

Those details done, I would like some recomendations on which Imaging Application to impliment. Ideally I am looking for something that can handle unicast and multicast, multiple individual sessions, and most importantly is able to use our existing library of Ghost Images. Our refubishing department is using Ghost as well so it would also be ideal if the application in question could make Ghost capable images as well to facilitate continued exhange of images the other department may not have archived.

Thanks in advance.

---

### Post by HermanAB on 2009-04-02
If you wish to use your existing ghost images, then you got to keep using Ghost.

If you wish to have Freedom, then you can look at dd and nc:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

and G4L:
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

---

### Post by Cheesemill on 2009-04-03
Check out [FOG]("http://www.fogproject.org/").

I think it does everything you need, I've been using it at work for 6 months now without any problems and must have imaged over 1000 machines so far.

Cheesemill

---

