---
title: "clonezilla with no DHCP"
date: 2009-03-13
forum: Server Platforms
---

### Post by cazz on 2009-03-13
How can I create a ubuntu server with no DHCP
I already have a DHCP server on my network and I dont want to my ubuntu server have one. It just going to have clonezilla.

Have not find any information about it yet.

---

### Post by bluefrog on 2009-03-14
don't choose dhcp-server when installing and if installed then remove...

---

### Post by Cheesemill on 2009-03-15
If you are trying to set up a Clonezilla server that enables PXE network booting then you may or may not be able to use your current DHCP server depending on how complex it is. Basically to enable PXE your DHCP server has to have the capability of passing DHCP options 66 and 67 to your clients (PXE server address and boot image filename respectively).

This can be done with dhcp3-server on Linux or Win 2003 Server, but not with most home routers (sometimes running hacked firmware can give you this option).

Cheesemill

PS - I've never used Clonezilla myself but have set up a similar solution using [FOG]("http://www.fogproject.org"), so forgive me if I'm way off the mark here :)

---

### Post by cazz on 2009-03-15
ok, well thanks I did find information about the port at FOG place and I even have install FOG on same server so I can try both tomorrow.

---

