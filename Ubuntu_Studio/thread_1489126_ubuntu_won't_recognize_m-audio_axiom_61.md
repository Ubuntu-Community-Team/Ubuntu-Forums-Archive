---
title: "ubuntu won't recognize m-audio axiom 61"
date: 2010-05-20
forum: Ubuntu Studio
---

### Post by HyperFlexed on 2010-05-20
Hi, just purchased the M-Audio Axiom 61 (as I had read reports of it working right out of the box for some people).

I haven't had as much luck. I've plugged in the device, looked in JACK, and I see nothing.

Tried lsusb:

```
audio@picard:~$ lsusb
Bus 001 Device 005: ID 0c0b:b159 Dura Micro, Inc. (Acomdata) 
Bus 001 Device 004: ID 03f0:2504 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 002 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Doesn't seem to be there. I'm not even sure what the device would show up as. Anyone have any ideas of what I could install to solve or diagnose this problem?

I tried installing ubuntustudio-audio and ubuntustudio-audio-plugins to no avail.

---

### Post by sgx on 2010-05-21
Hi, in the qjackctl setup page, on the middle right

Input device >
Output device >

click the >

If Axiom is not there, turn axiom off, unplug it, 
reboot computer, plug in the Axiom
turn it on, and check again.

And try various combos of the above, since usb is
not an equal opportunity emplugger ;)

---

### Post by HyperFlexed on 2010-05-21
I feel stupid now. I think it wasn't plugged into a usb 2.0 port. I have ports on the front and back of my PC. Plugged into back. Works now :)

---

### Post by sgx on 2010-05-22
> **HyperFlexed said:**
> I feel stupid now. I think it wasn't plugged into a usb 2.0 port. I have ports on the front and back of my PC. Plugged into back. Works now :)

One time I typed

cd /user/bin    and panicked because such an important folder disappeared

another time I crushed a mouse because it was impossible to configure
sound that worked perfect the day before, and I was a bit perturbed.
(The headphones were plugged into a keyboard, not the computer)

:guitar:

Cheers

---

