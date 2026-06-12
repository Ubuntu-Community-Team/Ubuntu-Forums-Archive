---
title: "Guitar Hero Midi Control?"
date: 2011-03-14
forum: Ubuntu Studio
---

### Post by m3x1c0 on 2011-03-14
Well the title pretty much says it all. Especially the question mark. I would love to figure out a way to build a linux pc dedicated to running midi instruments / other live sound antics. My first foray into this would be the issue of using regular usb hardware to control midi software. I really have no idea what i'm doing here so heres what little I do know.

1. When using Redoctane's original xbox explorer guitar (the one with the usb cable) the power light on the controller lights right up.

2. when using said controller in the frets on fire game I am able to easily reassign the keys to the controller [example: the buttons for the pick show up as joy #1, hat 0 (0,1) for pick down, and 0,-1 for up] this tells me the computer has no problem assigning it as a joystick. now the question is how do I assign it to midi and what program should i use?

---

### Post by m3x1c0 on 2011-03-21
*bump*

anyone? Really i just need to know how to map usb devices to use as midi. do i need some kind of converter or can it be done with software?

---

### Post by sgx on 2011-03-21
Hi, you'll need a class compliant midi device with a midi out, 
either 5pin din, or usb cable, plug it in, start qjackctl, click the setup button, look on the right side of the new panel for

Output Device  >
Input Device   >

and click the  > widgets to see your detected devices.

lsusb and usbview are good commands to spot devices

Here are links to screenshots and details of qjackctl

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

Lots of good reading, and use youtube searches to see things
in action, qjackctl, ardour hydrogen, zynaddsubfx, rakarrack
and ubuntu all have a range of videos.

Cheers

---

