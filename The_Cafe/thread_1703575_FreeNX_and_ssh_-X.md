---
title: "FreeNX and ssh -X"
date: 2011-03-09
forum: The Cafe
---

### Post by t0p on 2011-03-09
I used to use FreeNX from time to time; but then I discovered X-forwarding over ssh (ssh -X) and now I use that instead.

Is there some wonderful functionality of FreeNX that I could be losing out on by using ssh -X exclusively?  Or is FreeNX (and its attendant clients) just, as I suspect, a nice, pretty GUI way of doing precisely the same thing?

Please note: this is not a troll post or flame baiting.  I know some people hate the CLI with a passion.  But, since ssh -X allows you to use GUI programs from the remote machine... why FreeNX?

---

### Post by koenn on 2011-03-09
NX is largely "network optimized" X forwarding : it adds compression and caching

---

### Post by Pogeymanz on 2011-03-09
I was under the impression that FreeNX is more like VNC.

ssh -X (or -Y) is just for running apps from the server, not loading a whole desktop.

---

### Post by koenn on 2011-03-10
> **Pogeymanz said:**
> I was under the impression that FreeNX is more like VNC.

ssh -X (or -Y) is just for running apps from the server, not loading a whole desktop.

that's a rather superficial division. 
You can pull an entire window manager through an ssh -X tunnel, although it's more often used for individual apps. 

see  also [http://nomachine.com/documentation/html/intr-technology.html#3](http://nomachine.com/documentation/html/intr-technology.html#3)

---

