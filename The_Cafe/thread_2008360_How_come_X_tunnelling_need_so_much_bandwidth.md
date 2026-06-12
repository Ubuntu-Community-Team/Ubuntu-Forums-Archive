---
title: "How come X tunnelling need so much bandwidth"
date: 2012-06-22
forum: The Cafe
---

### Post by xusword on 2012-06-22
Hi

I recently need to remote to a linux machine. I have win7.

There are 2 ways available to me.

1. NoMachine NX client
2. CygWin/X tunnelling

When I remote through NX client, the display looks like crap. (Image compression)

I originally thought X tunnelling might be better; however, I just found out it is quite bandwidth intensive and it didn't work for me at all.

Is there any way of using X tunelling without taking that much bandwidth? (Maybe close to NX client level? With compression?)

thanks

---

### Post by trivialpackets on 2012-06-22
I'm certainly not sure, however my display for NX looks good remotely.  It is running Unity-2d, but it looks very good for a remote connection to me.  It's definitely good enough for me.

---

### Post by QIII on 2012-06-22
NoMachine NX is optimized for low bandwidth and high latency.

It works very well for me.  I get a very crisp and responsive desktop with low bandwidth use.  It's at least as good as RDP.

Try a different compression method.

---

### Post by mips on 2012-06-22
Well when you tunnel X all the display traffic goes to a remote server and that is pretty bandwidth intensive.

---

### Post by CharlesA on 2012-06-22
> **eric.proctor said:**
> I'm certainly not sure, however my display for NX looks good remotely.  It is running Unity-2d, but it looks very good for a remote connection to me.  It's definitely good enough for me.
That has been my experience too.

Altho some of the reds and blue text seem to glob together due to dithering and I cannot seem to get the bar at the top of the screen to resize  from the size the NX session was originally created. Example: I created the current session from a 1680x1050 screen and viewing it on a 1440x900 screen. The unity bar resizes fine, but that top bar doesn't.

Puzzling.

---

### Post by xusword on 2012-06-22
> **mips said:**
> Well when you tunnel X all the display traffic goes to a remote server and that is pretty bandwidth intensive.

Are there no way of reducing the bandwidth use?

I tried ssh -X -C -c blowfish-cbc,arcfour
Not helping a whole lot

---

### Post by Ji Ruo on 2012-06-23
> **xusword said:**
> Are there no way of reducing the bandwidth use?

I tried ssh -X -C -c blowfish-cbc,arcfour
Not helping a whole lot

X forwards the whole screen rather than updates of parts that change like some other less intensive protocols. So compressing it is really all you can do.

---

