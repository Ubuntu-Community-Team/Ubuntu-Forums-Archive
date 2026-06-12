---
title: "So I was installing the newest server on a really old server..."
date: 2013-10-13
forum: Server Platforms
---

### Post by ModifyMe on 2013-10-13
As I wrote in the title I downloaded the latest ubuntu linux version but when I tried to install it on our old server it would write out: "This kernel requires an x86-64 CPU , but only detected an i686 cpu. Unable to boot - please use a kernel apporpriate to your CPU." I'd be really thankful if someone helped me, or linked me the appropriate version. And if I posted in the wront thread i'm sorry. I saw what looked like a simillar pot but posed in 2009 here. Thanks.

---

### Post by Iowan on 2013-10-13
Moved to Server Platforms.
Sounds like you downloaded the 64-bit version instead of the 32-bit. The 64-bit version is the default. I'll look for the link.

[This]("http://releases.ubuntu.com/raring/") page lets you choose which version you want.

---

### Post by volkswagner on 2013-10-13
Before downloading "Choose your flavor" download the 32 bit version not the 64bit.

[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

---

### Post by tgalati4 on 2013-10-13
If your processor does not support PAE--physical address extension, then you will have to fake it or go with an older distro that still supports non-PAE cpu's.

---

### Post by ModifyMe on 2013-10-13
Thanks guys its working now. 1 more question. Is it possible for me to install the "desktop" GUI on a server type? I'm really new to linux.

---

### Post by Amorphous Serendipity on 2013-10-13
> **ModifyMe said:**
> Is it possible for me to install the "desktop" GUI on a server type? I'm really new to linux.

ModifyMe,

To install the ubuntu-desktop run:
```
sudo apt-get install ubuntu-desktop
```

I highly recommend not doing this on a server install, especially if it  will be a production server. Ubuntu server installs headless (without  GUI) to reduce system load, limit attack surface, etc.

Additionally, not installing the ubuntu-desktop will force you to get use to the Linux CLI (good learning experience).

---

### Post by tgalati4 on 2013-10-13
If this is strickly for home use and you are just playing around, you can install the desktop version and use that as a server.  The graphical server takes perhaps 9% of the cpu cycles on older hardware and only 1 to 2% on the newer hardware.  To learn linux, find an old desktop machine to install the desktop version and then install the server version on a server machine and work with both.

---

### Post by mörgæs on 2013-10-13
@tgalati4

There's no PAE problem on server hardware. It's only relevant for a very limited number of portables.

---

