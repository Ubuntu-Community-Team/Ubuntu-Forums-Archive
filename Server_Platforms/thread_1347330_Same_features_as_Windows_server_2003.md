---
title: "Same features as Windows server 2003?"
date: 2009-12-06
forum: Server Platforms
---

### Post by cyberedsun on 2009-12-06
Hi,

On Windows server 2003, you can create several accounts. From several Ubuntu clients, you can use "Terminal Server Client" to access to these accounts on Windows server 2003 to use applications (office, adobe, messenger...).

Now that I want to setup an Ubuntu server that act the same as Windows server 2003 in terms of handling accounts and applications.

I have tried "Remote Desktop View", "Grdc", "Gnoem-RDP", but none of these features is what I want. 

Please anybody give me an advise how to setup one?
Thanks!

---

### Post by Vegan on 2009-12-06
```
sudo adduser
```

use the man page for details

---

### Post by Bachstelze on 2009-12-06
If you want a Windows server, install a Windows server. Linux is not a free Windows.

---

### Post by munky99999 on 2009-12-06
sudo adduser. If you want a more centralized authentication method... there are options.

As for terminal services.

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

First one will tell you how to quickly install it.

---

### Post by koenn on 2009-12-06
> **Bachstelze said:**
> If you want a Windows server, install a Windows server. Linux is not a free Windows. this.

and if you're going to run a server, read the documentation. A default Ubuntu server doesn't even have a desktop, so what are you going to  rdp to ?

If you want a " Linux Terminal Server", munky99999's link is worth a look.

---

### Post by cyberedsun on 2009-12-07
Thanks guys for your comments to my concerns. After a few days playing around with Google, I have found exactly what I want.

- I install FreeNX server to the Ubuntu machine that I want to remote access to with graphical inteface.
- I use NXclient from Nomachine or QTNX as client to access to remote server.

Howto: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Now that I can give many people access to Ubuntu machine at the same time, with nice GUI. 

For your info, the "adduser" is good for text mode only. The LTSP is good for diskless solution.

Again, thanks to all for your comments and help.
Have a nice day!

---

