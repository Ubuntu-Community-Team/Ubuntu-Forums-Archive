---
title: "how is MIDI in ubuntu?"
date: 2009-12-01
forum: Ubuntu Studio
---

### Post by expxe on 2009-12-01
will i have any problems if i buy a midi/usb cable and connect my digital piano to my computer?

im on ubuntu 9.10 64 bit

---

### Post by raboofje on 2009-12-01
> **expxe said:**
> will i have any problems if i buy a midi/usb cable and connect my digital piano to my computer?

Basically, it depends on the device. Did you have any specific device in mind?

---

### Post by trulan on 2009-12-01
Mine works.  It's a Turtle Beach something-or-other - I bought it about five years ago.  It was basically plug and play - I mean it took me a bit of fiddling to get any sound out of my computer with it, but that was because I wasn't using the MIDI software properly.  The cable itself was no trouble at all.

---

### Post by expxe on 2009-12-01
i was thinking of picking up this or something similar

[http://www.dealextreme.com/details.dx/sku.11277](http://www.dealextreme.com/details.dx/sku.11277)

[http://www.dealextreme.com/details.dx/sku.730](http://www.dealextreme.com/details.dx/sku.730)

---

### Post by VertexPusher on 2009-12-02
Any USB MIDI interface that is class-compliant (i.e. it works without special drivers on Windows and Mac) should work out of the box in Ubuntu, too.

---

### Post by trulan on 2009-12-02
I read the discussion about those cables a little bit.  This one:

[http://www.dealextreme.com/details.dx/sku.11277](http://www.dealextreme.com/details.dx/sku.11277)

was reported to work under Ubuntu 8.04 by one of the reviewers, so it should be fine on any recent Ubuntu release.  It was also reported to install with no special drivers, another good sign.  The other one looked a little less promising IMO.

Do your own homework though too, it's your money you're spending, not mine.  ;)

Here's what I have - looks like Turtle Beach only sells one cable.  It's a bit expensive from their site, but here it is for reference anyway:
[http://www.turtlebeach.com/products/usb-midi-cable/home.aspx](http://www.turtlebeach.com/products/usb-midi-cable/home.aspx)

---

### Post by kayosiii on 2009-12-04
I would be very suprised if either of those didn't work. Basically I have bought more than one cheap midi->usb adapter from ebay and they were plug and play.

---

### Post by expxe on 2009-12-04
ok cool. now, what affects latency? does it have to do with the cable/chip quality or something else? if the cable is "slow" is there no way to make it faster? the two cables ive posted about don't look exactly the best quality

---

### Post by kayosiii on 2009-12-05
The cables are limited to the speed of an old fashioned midi cable - as a lot of outboard midi equipment expects that speed, since that hasn't really changed since the early 80s you can expect that the communication is quite slow by todays standards but since the amount of information being transmitted is not that great it doesn't tend to matter.

Latency would tend to come more from software misconfiguration I would expect.

---

### Post by nathan726 on 2009-12-24
I bought a midi-usb cable on ebay for $8:

[IMG]http://image.ecplaza.com/offer/s/super2008/5603619_s.jpg[/IMG]

I plugged it in, set my keyboard to midi mode, then used jack connections (on the alsa tab) to connect the midi cable output to a program input (zynaddsubfx).
It works great. I can't notice any latency problems.

---

