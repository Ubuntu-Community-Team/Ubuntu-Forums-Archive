---
title: "Virtualization with KVM server and thin clients that connect by network"
date: 2009-11-11
forum: Virtualisation
---

### Post by erlguta on 2009-11-11
Hello.
I am looking for information about kvm server hosting diferent guests (ubuntu-desktp, win-xp, etc), and users connect to these virtual desktops using either inexpensive thin clients or PCs, with a minimal booting OS.

Is there something about this?. 
Where can I find information about this?

Thank you.

---

### Post by erlguta on 2009-11-11
Or maybe booting by PXE from a thin client, that loads one kvm guest...
I'm wandering... is this possible?

I want something like this in Ubuntu:

[http://www.redhat.com/virtualization/rhev/desktop/](http://www.redhat.com/virtualization/rhev/desktop/)

"With Red Hat Enterprise Virtualization for Desktops, complete desktop environments are hosted as virtual desktops on servers located in a centralized datacenter. Users connect to these virtual desktops using either inexpensive thin clients or repurposed PCs."

I think the idea is clear...

---

### Post by gonzakloperu on 2010-09-04
I'm also interested in this idea! Any information on doing this with Ubuntu?

---

### Post by TheFu on 2010-09-06
KVM requires a VT-x capable CPU (or whatever AMD calls it), so running a KVM VM on a netbook probably is not possible.  On the client side, you can run any remote access protocol like RDP, VNC, NX, or straight X11/Windows to access server computing power.  In this way, you just need a minimal Linux running on the netbook with networking enabled to connect to the server.  If the server is also Linux, then you already have a multi-user system that can run tons of apps. If the systems are on the same LAN, even wifi "g" connections are fast enough for straight X11.

There are specific solutions for performing this sort of setup if you really want to deploy less powerful desktops. Most that I am aware of are commercial - Xen, VMware, and Oracle are the non-MS solutions.  

If you want something free with a central server, check out the Linux Terminal Server Project [http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project).  The "See Also" section will provide some more ideas for you [http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project#See_also](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project#See_also)

I hope these leads help someone. It would be great if someone who actually deployed LTS can respond.

---

### Post by kemra on 2010-09-08
To run thin-clients from a central server you can LTSP. The official documentation can be found here:

[http://kent.dl.sourceforge.net/project/ltsp/Docs-Admin-Guide/LTSPManual.pdf]("http://kent.dl.sourceforge.net/project/ltsp/Docs-Admin-Guide/LTSPManual.pdf")

And the Ubuntu Help Page (including installation instructions) can be found here:

[https://help.ubuntu.com/community/UbuntuLTSP]("https://help.ubuntu.com/community/UbuntuLTSP")

---

### Post by LightningCrash on 2010-09-08
You might look at the Sun Ray Server and Sun Rays (all on Linux, of course)

The Sun Ray 1s are $10-20 each on eBay and they still work pretty well.

---

