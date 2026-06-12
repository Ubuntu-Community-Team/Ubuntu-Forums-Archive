---
title: "Fan speed tied to USB keyboard"
date: 2012-04-12
forum: Server Platforms
---

### Post by kingbellows on 2012-04-12
Hi All,

I have a bit of an interesting issue for some people to think about.  I have a system on my desk that is being setup as a server.  I installed 10.04 on it, and almost everything is working perfectly...

Occasionally, the fan goes out of control (fast) for seemingly no reason.  It happens every few hours, and lasts several minutes.  I logged the fan speeds and temperatures every few seconds while this was going on, and found that the fan speeds increase dramatically during this time, but the system temperature stays statistically constant regardless of the fan speed (ie: there is no evidence that a higher temperature inside is causing the high fan speed).

Through fiddling and such, I've found that if a USB keyboard is attached to the system, the fan speeds stay fine (for weeks of observation).  When I remove the keyboard, within a couple hours the fans will spin up again for a few minutes, and so the cycle repeats.  I haven't found other devices (eg: USB key, USB mouse) that seem to 'fix' the fan speeds.

When the fans are going full tilt, attaching the USB keyboard brings them down in maybe 10-20 seconds.

This isn't really a major issue, but I figured I'd post it here out of curiosity.  As the machine is a server it will not have a keyboard connected to it in general (so I expect that the fans will be going up and down), however it will be in a location where it (most importantly) won't annoy me.

Using 10.04.3 on a Vostro 220s
(And I posted this in the server forum as I don't expect anyone with a keyboard connected to their system to have noticed any similar issues)

---

### Post by Jonathan L on 2012-04-12
HI kingbellows

I've not had this experience but have seen very peculiar behaviour from USB devices which make one think they are not always as bug-free bits of hardware as we'd hope.

Recently I had a brand new Kingston memory stick, and various Dell and IBM USB keyboards, all of which were tried in various computers.  But when you plug the memory stick into either of two brand new Dell servesr, the memory stick made the keyboard not work.  I spent some time finding this out and experimenting.  I'm stumped about how you could even achieve this on purpose!  Servers had to be configured from an actual CD-ROM, much to my irritation.

My only guess in your particular case is perhaps the temperature sensors or fan control IO is interfaced to the USB tree, and there's some bug or problem there.  Have you tried looking at the output of lsusb?

Kind regards,
Jonathan.

---

### Post by kingbellows on 2012-04-12
Interesting.  I'm glad that I'm not fighting any serious issues like those, mine is just mildly annoying.

Nothing looks interesting in the output, at least to me:
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Snapshots of the system during regular operation and when the fans are squirreling out: (goes Time, CPU temp, Case Temp, fan1 rpm, fan2 rpm, temp1, temp2)
Thu Apr 12 03:13:50 2012, 41.0, 25.0, 3229, 3276, 32.0, 30.0
Thu Apr 12 16:34:01 2012, 41.0, 25.0, 1130, 1928, 35.0, 34.0

So the fans practically double in speed, but it was actually cooler.

---

