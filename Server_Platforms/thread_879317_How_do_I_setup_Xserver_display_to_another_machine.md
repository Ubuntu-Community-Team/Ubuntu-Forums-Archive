---
title: "How do I setup Xserver display to another machine?"
date: 2008-08-03
forum: Server Platforms
---

### Post by JBull on 2008-08-03
I have a headless server that is kept in a closet.  Currently I use ssh to administer that machine.  How can I configure Xserver to send the display to another machine?

I have another machine that runs Kubuntu.  I'd like to use this machine to view the X display from my headless server.   What approach should I take?

Thanks

---

### Post by JBull on 2008-08-04
OK, I got it.  Onmy server machine I installed gdm.  Then in GDM settings enabled XDMCP.

Then from my client machine in kdm I select remote connection (enter ip address and username/password) and it connects right up!  Now I can have my graphical display from my server on any of my other machines, fully functional.  It works great just like I'm sitting in front of my server except without having to get up and connect a monitor.

---

