---
title: "Logitech usb wireless doesn't wake up computer from suspend"
date: 2018-04-20
forum: Ubuntu Development Version
---

### Post by horizonbrave on 2018-04-20
Hi,
my usb wireless Logitech mouse is not able to wake up my computer (a laptop with the lid usually kept closed, so no access to the power button for resuming it).
Mouse is a Logitech M525, but the problem arise also with a M235 (all they have in common is using a "unifying" wireless receiver).
The BIOS "wake up from usb" option in the computer (a Dell Latitude E6520) is enabled.

Shouldn't easy?
I tried installing Solaar, but it just providing pairing and battery status functionalities.

Many thanks :)

---

### Post by jbicha on 2018-04-20
I think that's a known issue that you need to press the power button (or open the lid) to wake up from sleep. Sorry.

---

### Post by sonsofblades on 2018-04-24
Yeah, the unifying receiver doesn't seem to work as wake from suspend via USB 2.0. 

As an interesting side note, it doesn't happen with Logitech's hi speed usb dongles (g602, 603, etc)that come with their gaming mice, so it's a problem exclusive to the Unifying receiver. Wake from USB seems to work with those in 125hz mode and in 1000hz mode, from my testing with my g603, and in both speeds. Happens even with the lid closed too. 

I'm going to take a wild guess and say that the Unifying receiver has a rather aggressive sleep mode in it, just like their mice do.

---

