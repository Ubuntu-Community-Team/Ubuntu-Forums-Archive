---
title: "Ubuntu desktop grabs USB devices before Virtualbox"
date: 2009-10-14
forum: Virtualisation
---

### Post by Airgead on 2009-10-14
Folks

Jaunty with Virtualbox 3.0.8r53138

I have been running virtualbox on Jaunty for a while now. I have USB working for my scanner. My problem is that when I plug a USB Flash disk or MP3 player into the PC, the Ubuntu destop grabs the device before Virtualbox can. It shows up in the list of connected USB devices in Virtualbox but greyed out and marked as "Status Unavailable". I have device filters set up for the devices so Vbox should grab them straight away (like it does with the scanner)

The problem only occurs on devices that the desktop auto mounts so I am 99% sure that the problem will be solved if I can stop Ubuntu from automounting the devices. 

I have unchecked the media_automount in nautilus preferences using gconf-editor and that stops the desktop icon from appearing but the device still seems to be grabbed by something before Virtualbox. An ipod shows as connected straight away so there is definitely something trying to talk to it.

I can live without usb flash drives bit I am desperately  trying to get my wife's nice new shiny 16g 5gen nano talking to itunes (no libgpod support yet). As this was her 40th birthday present from me its kind of embarrassing that I can't get the thing working so any assistance very much appreciated.

Cheers
Dave

---

### Post by cnbiz850 on 2009-10-14
I just found the solution here that helped me on the same situation:
[https://help.ubuntu.com/community/VirtualBox/USB]("https://help.ubuntu.com/community/VirtualBox/USB")

---

### Post by Airgead on 2009-10-14
> **cnbiz850 said:**
> I just found the solution here that helped me on the same situation:
[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

Champion. You have saved me much embarasment.

I had actually tried something very similar from another page and it didn't work. I found that page yesterday but it looked so similar to what I had already tried I didn't do it.

Cheers
Dave

---

### Post by Lazerfingers on 2009-10-15
I'm having the exact same problem as the OP only the fix listed in the previous link didn't seem to help my VB mount USB devices in XP.  I'm running 9.10 Beta and the Virtual Box 3 PUEL if either of those two pieces of info help.  Thanks for any and all assistance.

---

