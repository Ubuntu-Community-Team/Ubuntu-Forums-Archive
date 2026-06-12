---
title: "Best solution for Linux application server (X vs. RDP vs. VNC, etc.)"
date: 2011-02-24
forum: Server Platforms
---

### Post by teprovoco on 2011-02-24
I'd like to set up my Linux box so that I can access its GUI applications from an older Mac laptop running OS X 10.5 on the local LAN and away from home (over the internet).

I know the traditional way to do this is with an X session (& Mac OS X has an X window client included), but does this offer the best performance, especially over the internet?  Would I be better to install some sort of RDP server?  I've used VNC in the past, but performance has been pretty slow and ideally I'd like the remote apps to show up seamlessly (more efficient use of screen real estate).

What are my options?  Have you set up something like that?  Experiences?

Thanks for your advice!!

---

### Post by cviorel on 2011-02-24
Have you tried NoMachine NX?
I posted a guide [here]("http://cviorel.easyblog.ro/2008/01/15/installing-nomachine-nx-on-ubuntu-710/").

---

### Post by elico on 2011-02-25
or VNC \XRDP.
XRDP uses a RDP frontend as connection and then using a loopback and VNC.

i have used XRDP, just apt-get install XRDP and works.
VNC for mac is more native cause it's a unix based system with VNC server built in.

---

