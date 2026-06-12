---
title: "Wireless Card Problem"
date: 2011-12-23
forum: Ubuntu One (CLOSED)
---

### Post by Flugan on 2011-12-23
[NOTE: This is in the wrong category I know, please move it]

So, I've just recently installed Ubuntu on my laptop and I'm having some problems with my wireless network connection.

The network card I'm using is Broadcoms BCM43224 and as I booted up Ubuntu I was immediately told that I should install the STA drivers for my card. It took 15 seconds to just go into "System Settings", going to "Additional Drivers", have it search around for a few seconds and the activate "Broadcom STA wireless driver". 

But for some reason it still doesn't work.

Typing lshw -C network into the terminal and the card shows up, configuration: driver=bcma-pci-bridge so I guess the driver's installed?

Typing iwconfig just shows:

lo                                no wireless extensions.
eth0                            no wireless extensions.

And nothing more.

I'd be very grateful if anyone could help me out, if you need more info then just ask :)

---

