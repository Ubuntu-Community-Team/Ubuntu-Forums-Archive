---
title: "Logitech"
date: 2007-03-08
forum: System76 Support
---

### Post by Stereotypical Rage on 2007-03-08
Good Evening all,

I noticed that on system76's site that they offer the Logitech Cordless Desktop EX 110 as a $39 upgrade. I just purchased this very same model for a friend of mine, where I installed Edgy Eft for him. The one thing is that the mouse DOES NOT work! It's got power and all, but I don't think the right modules are installed. Can someone tell me what modules I need to get the mouse to work? Keyboard words great. (Have yet to try the multimedia keys)

Thanks in advance,

Stereotypical Rage

---

### Post by crichell on 2007-03-08
Maybe the mouse is bad - or there's a bad IR connection/component.  It works out of the box on Ubuntu - if you plug in another USB or PS2 mouse and it works then the Logitech should work as well.

---

### Post by Stereotypical Rage on 2007-03-08
I installed the server version of Edgy first due to the fact that it would not the graphical installer. The system I installed it on was a Dell Dimension XPS T750r. If it works out of the box, then I am pretty sure I am missing a module or two.

Also, yes another USB mouse works. I borrowed my girlfriend's BenQ mini mouse
[IMG]http://static.actebis-images.com/productimages/I216883.jpg[/IMG]

---

### Post by crichell on 2007-03-08
> Also, yes another USB mouse works. I borrowed my girlfriend's BenQ mini mouse

Since that mouse is working your logitech should work - the modules are the same - check for "hci_usb" and "psmouse".  A wireless mouse appears to Ubuntu no different than a USB or PS2 mouse - it's connected to the same port.  (A bluetooth mouse is an exception though - different port.)

---

### Post by Stereotypical Rage on 2007-03-09
Thank you Carl. I shall try this when I get off work at 2:30a EST

Don't forget about the new DST rules that go into effect come this Sunday!

---

### Post by Stereotypical Rage on 2007-03-09
crichell: They are both loaded as per lsmod.

This just appeared in my /var/log/messages....

Mar  9 04:48:23 OldGuy kernel: [17181569.036000] usb 1-1: new low speed USB device using uhci_hcd and address 3
Mar  9 04:48:23 OldGuy kernel: [17181569.212000] usb 1-1: configuration #1 chosen from 1 choice
Mar  9 04:48:23 OldGuy kernel: [17181569.232000] input: Logitech USB Receiver as /class/input/input4
Mar  9 04:48:23 OldGuy kernel: [17181569.232000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:07.2-1
Mar  9 04:48:23 OldGuy kernel: [17181569.264000] input: Logitech USB Receiver as /class/input/input5
Mar  9 04:48:23 OldGuy kernel: [17181569.264000] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:07.2-1

and this...
Mar  8 21:31:32 OldGuy kernel: [17179592.704000] logips2pp: Detected unknown logitech mouse model 127 (Both Keyboard and Mouse plugged into the PS/2 Port)

I have yet to reboot to see if it works, but hmm...

Edit: Nope rebooting did not solve it.

---

### Post by Stereotypical Rage on 2007-03-09
I just had to do a **sudo dpkg-reconfigure xserver-xorg** and select ImPS/2 :guitar:

---

