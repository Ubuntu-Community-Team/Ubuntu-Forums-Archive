---
title: "Echo AudioFire4 - output not working"
date: 2010-04-19
forum: Ubuntu Studio
---

### Post by gaz514 on 2010-04-19
Hey people,

I recently got an Echo AudioFire 4 FireWire audio interface.

I've got FFADO to recognise it, upgraded the firmware to version 4.8, and Jack starts up fine. I've tried it with both the regular Jack and Jack2 and I get the same result.

Jack presents six inputs and six outputs for the card, as it should. They're named dev0_Unknown, dev0_Unknown1, ..., dev0_Unknown4; the inputs and outputs have the same names, as opposed to the out1, out2, in1, in2 that you get with ALSA. The inputs work perfectly fine: I can record sound in Ardour with them. However the outputs just won't work. Ardour gives the following errors when trying to connect the master, click, etc. track outputs to the system outputs:

[ERROR]: cannot setup master outputs
[ERROR]: AudioEngine: cannot connect ardour:auditioner/out 1 (ardour:auditioner/out 1) to system:dev0_Unknown (system:dev0_Unknown)
[ERROR]: AudioEngine: cannot connect ardour:auditioner/out 2 (ardour:auditioner/out 2) to system:dev0_Unknown0 (system:dev0_Unknown0)

(and similar for the click and master outputs). And Jack reports the following:

Destination port in attempted (dis)connection of ardour:auditioner/out 1 and system:dev0_Unknown is not an input port
Destination port in attempted (dis)connection of ardour:auditioner/out 2 and system:dev0_Unknown0 is not an input port

No more detail than that I'm afraid.

Disclaimer: I'm not actually an Ubuntu user; I'm on Arch Linux, but the Arch community doesn't have many pro-audio users, whereas this forum seems very active. I'm pretty sure it's a Jack or FFADO issue rather than an Arch one, especially as I'm not using the stock Arch kernel (stock kernel only has the new FireWire implementation enabled, and FFADO needs the old one).

Thanks in advance.

Screenshot of what qjackctl shows:

[img]http://koston.vm.bytemark.co.uk/jack.png[/img]

---

