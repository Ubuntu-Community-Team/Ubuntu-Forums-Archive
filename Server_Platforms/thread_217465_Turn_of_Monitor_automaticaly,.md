---
title: "Turn of Monitor automaticaly,"
date: 2006-07-17
forum: Server Platforms
---

### Post by eldaria on 2006-07-17
Hi everyone.

I was wondering if there is a way to make an Ubuntu server turn of the monitor automatically.

I can only find instruction on how to do this with a gui installed, but since I don't have or want a gui on my server how can I do this?

I noticed that it does blank the screen after a while but monitor is still on.
Same monitor connected to a Windows box with powersave enabled will turn off with LED going off.

Regards.
Brian.

---

### Post by alecjw on 2006-07-17
Why do you need a monitor? I took out the graphics card from my server.

I only left in the motherboard, the hard drive, the PSU, the RAM and the network card -- you don't need a monitor, just access it via SSH; that's what I do.

---

### Post by eldaria on 2006-07-17
Well I also use SSH when I'm remote.

But when server is standing next to my desktop and I have a spare screen and a keyboard switch, it is easier to just switch over. :-)

So still need to know how to activate powersave. :-)

---

### Post by k94382 on 2006-08-31
so if you dont have a monitor, how would you install the server edition in the first place?????

---

### Post by eldaria on 2006-08-31
Install it and then you remove the monitor. ;-)

---

### Post by k94382 on 2006-08-31
> **alecjw said:**
> Why do you need a monitor? I took out the graphics card from my server.

I only left in the motherboard, the hard drive, the PSU, the RAM and the network card -- you don't need a monitor, just access it via SSH; that's what I do.

true but without a video card and any port to attach a monitor, how would you do that?

---

### Post by eldaria on 2006-08-31
Same thing, install it then remove hardware that you don't need.
I would leave the graphic card, for if ever you need local access, you at least don't need to open up the PC.

---

