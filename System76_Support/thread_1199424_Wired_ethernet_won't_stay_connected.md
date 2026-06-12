---
title: "Wired ethernet won't stay connected"
date: 2009-06-28
forum: System76 Support
---

### Post by John Marter on 2009-06-28
I am one week into using my new System 76 Ratel with Jaunty installed.  The one thing I have been struggling with is that the network is constantly going down.  I am using the same network cord into the same jack on the router as my old computer, so I suspect the problem is with the new box.

Here is a section of the dmesg output which gives a sense of the problem.
```
[28482.715458] r8169: eth0: link down
[28484.443701] r8169: eth0: link up
[28707.761924] r8169: eth0: link down
[28709.716493] r8169: eth0: link up
[28942.810869] r8169: eth0: link down
[28944.931901] r8169: eth0: link up
[29482.912367] r8169: eth0: link down
[29484.698935] r8169: eth0: link up
[29697.930395] r8169: eth0: link down
[29699.738988] r8169: eth0: link up
```Any ideas how I should tackle this problem?  It would not be unreasonable for me to install a network card rather than use the on-board port.

---

### Post by thomasaaron on 2009-06-29
I doubt a network card is necessary. Networking is tested pretty thoroughly in QC.

Try bypassing the router and plug straight into the wall/modem. Does it still drop the connection?

---

### Post by John Marter on 2009-06-29
Yes, that was it.  I have switched to my old (no wireless) router and I have not had any problems all afternoon.

It is curious that I did not have the same level of problems on my old Debian box.  With the new box, Pidgin refused to connect to one of the servers because of too many disconnects.  I did not have NetworkManager installed on my old system.  [Wild speculation follows] Maybe Pidgin is more tolerant of the network problems in the absence of NetworkManager.  

Anyway, the router in question is an AT&T Plug&Share 6800G.  I was planning on replacing the device anyway, so that solves the problem for me.  Thanks for your help.

-John

---

