---
title: "VMWare Server using only CLI?"
date: 2006-07-17
forum: Server Platforms
---

### Post by tgoose on 2006-07-17
Is it possible to run a virtual machine without having installed X11 etc. on the host system (i.e. Ubuntu Server 6.06)? I can't seem to find any guides as to how to do this; I have run vmware-server-config.pl and it all seems satisfactory, but beyond that I'm pretty much lost.

Failing that, is there an easy way to install X11 and a lightweight window manager in order to run it graphically? I'd much rather have the first option, but if that's impossible I could probably do this.

Thanks.

---

### Post by Thenotsowyzewun on 2006-07-20
Hi,

You might get more responses over @ VMWare's support site, [here]("http://www.vmware.com/community/index.jspa").
Lightweight Window Managers? Well there's WindowMaker, FVWM, Blackbox, XFCE, Fluxbox, Openbox...

---

### Post by A1ex on 2006-07-20
Download and install the VMware server clients onto whatever box you want to manage the server from.

You can then use that to connect remotely to VMWare without having X11 installed on the server.

---

