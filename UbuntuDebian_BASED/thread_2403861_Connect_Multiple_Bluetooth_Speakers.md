---
title: "Connect Multiple Bluetooth Speakers"
date: 2018-10-17
forum: Ubuntu/Debian BASED
---

### Post by only.palmero on 2018-10-17
Hi team!


I'm trying to connect several bluetooth devices with Raspberry PI to use them as speakers.


However, the system only detects the first device that connects as a sound card, the rest keep the bluetooth synchronization active, but it does not interpret them as audio cards even though it is indicated by blueman-manager.


Is there anything I can do to keep all devices synchronized and supported as audio cards?


I've disabled the internal bluetooth by modifying the file */boot/config.txt* adding the line _dtoverlay=pi3-disable-bt_, then I used a bluetooth USB capable of connecting with multiple devices like the ASUS BT400. After pairing and connecting to the speakers, I launch the command _pacmd list sinks_ and _pactl list cards_ to see the configuration but I discover that Pulseaudio has only emulated the first device _bluez.XX.XX.XX.XX ..._ .


I suppose the problem exists in the **Bluez and PulseAudio** modules. Can somebody help me?

---

### Post by coffeecat on 2018-10-17
Based on [this stackoverflow question](https://stackoverflow.com/questions/52804518/connect-multiple-bluetooth-speakers-with-raspberry-pi), it appears you are using RetroPie as an operating system.

*Thread moved to **Ubuntu/Debian BASED**.*

---

