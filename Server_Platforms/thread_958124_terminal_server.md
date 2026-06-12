---
title: "terminal server"
date: 2008-10-25
forum: Server Platforms
---

### Post by mitchroberts on 2008-10-25
need help

what would i need on a windows xp computer to be able to connect to ubuntu terminal server and and run programs with the GUI on a windows desktop.

Mitch

---

### Post by sethvath on 2008-10-25
Do you mean remote assistance from a ubuntu system to a windows xp computer?

---

### Post by bunnynuts on 2008-10-25
Are you looking to see your unix desktop from windows (do you use a gui for the server)? Or, are you looking to manage from command line? If you are looking to connect using ssh, then the putty ssh client is what you need. If you are looking to do something of a remote desktop from windows to view a unix desktop I can not help you there. Possibly something related to the cygwin project?

---

### Post by lykwydchykyn on 2008-10-25
VNC is another option.

---

### Post by ezacon on 2008-10-26
Use NX from [http://www.nomachine.com/](http://www.nomachine.com/)
There is a free linux server and a free windows client.
Once installed you can login to GDM as if you where in your console.
Much simpler than X redirection etc...

---

### Post by mitchroberts on 2008-10-26
i would like to install the gnome desktop with terminal service be able to access the gnome desktop from 2 or 3 windows pc's and be able to run a few programs.
thanks

---

### Post by mitchroberts on 2008-10-26
> **bunnynuts said:**
> Are you looking to see your unix desktop from windows (do you use a gui for the server)? Or, are you looking to manage from command line? If you are looking to connect using ssh, then the putty ssh client is what you need. If you are looking to do something of a remote desktop from windows to view a unix desktop I can not help you there. Possibly something related to the cygwin project?

yes i am using gui on the server also i have terminal service installed and i am looking to see the gnome desktop so 2 or 3 people can run some programs these 2 or 3 people no less then i do about linux so having the desktop is a have to.

---

### Post by mitchroberts on 2008-10-26
so what would be the best one to use and what other programs would i need for this to work

---

### Post by lewtwo on 2008-10-27
[http://blog.gwright.org.uk/articles/2008/07/12/freenx-package](http://blog.gwright.org.uk/articles/2008/07/12/freenx-package)

Unlimited compile of NoMachine NX 3.2.0 server open source for Ubuntu Hardy (32-bit). You will still need a NX CLinet (NoMachine free client).

Another FreeNX link:
[http://en.kioskea.net/faq/sujet-722-install-freenx-server](http://en.kioskea.net/faq/sujet-722-install-freenx-server)

---

### Post by alienprdkt on 2008-10-27
> **lykwydchykyn said:**
> VNC is another option.

I have VNC on my amd 64x2 6400 (3.0GHz x2) with 2gb ram on a local LAN and it runs very sloooow and choppy for some reason. This was the first time I have used VNC on Ubuntu. I have used it on gentoo and had really good results. I have used NOMACHINE on Ubuntu before and works great.

---

### Post by lykwydchykyn on 2008-10-28
agreed, the NX option performs much better than VNC.  For 2-3 people you need FreeNX, though, as the (proprietary) NXserver from NoMachine only allows 2 concurrent connections.  I've had some problems with it myself, though when it works it performs well.

You need to add these repos to install though:
```

deb http://ppa.launchpad.net/freenx-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/freenx-team/ubuntu hardy main

```
It's not in the main repos.

---

