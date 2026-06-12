---
title: "Ratel Value - Mouse works oddly"
date: 2009-02-05
forum: System76 Support
---

### Post by Teasdale on 2009-02-05
I love my new ratel Value, except for this one thing. All I replaced was the tower - I'm using the same keyboard, monitor and mouse I used with my old PC (it had Ubuntu 7.10). The mouse always worked fine. But suddenly, with the new PC, it doesn't always highlight what I want it to - it sometimes starts to highlight, but then un-highlights. Or it refuses to highlight. It doesn't drag the scrollbar on the side of windows to allow me to scroll to the end of a document - I have to keep clicking and drag it down little by little. And it's finicky about dragging and re-sizing windows. Sometimes it works, but more often it doesn't.

I've played around with my preferences/mouse settings, and I can make it react faster or slower, I can change the double-click speed - but nothing seems to help its actual performance. I'm having to use keyboard shortcuts because the mouse is so frustrating. Is there some other setting hidden somewhere that I need to play with?

---

### Post by Guille Damke on 2009-02-05
Hi Teasdale,
I am sorry, I know it sounds silly, but are you sure the mouse works well in other computer? Probably, it is failing now just by a bad-luck coincidence, can you borrow and try another mouse? It can be a way to discard the simplest possible cause.
I hope you solve this soon.

---

### Post by jdb on 2009-02-05
> **Guille Damke said:**
> Hi Teasdale,
I am sorry, I know it sounds silly, but are you sure the mouse works well in other computer? Probably, it is failing now just by a bad-luck coincidence, can you borrow and try another mouse? It can be a way to discard the simplest possible cause.
I hope you solve this soon.

I had a problem similar to that once & it was caused by the wrong mouse driver in /etc/X11/xorg.conf

Memory fades, but I think it was set to mouse for a USB mouse but I had a PS/1 mouse & had to change it to psmouse.

jdb

---

### Post by Teasdale on 2009-02-05
> **jdb said:**
> I had a problem similar to that once & it was caused by the wrong mouse driver in /etc/X11/xorg.conf

Memory fades, but I think it was set to mouse for a USB mouse but I had a PS/1 mouse & had to change it to psmouse.


A wrong driver seems to fit - /etc/X11/xorg.conf is a text file that doesn't seem to give options for mouse drivers. It says this:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"

---

### Post by Teasdale on 2009-02-05
I've looked up ps/1 and looked at the back of my computer. I *do* have a ps/1 connector, so I'm pretty sure I need to to switch my mouse from usb to ps/1.

Is making changes to the xorg.conf file the only way to do that? Do I need to add a section to the document, like this?

[I]Section "Mouse"
Identifier "???"
Driver PS/1?
EndSection[/I]

---

### Post by drewbenn on 2009-02-06
Teasdale, I'd really take a second look at Guille Damke's suggestion.  The behavior you're seeing sounds almost identical to the problems I'm having right now, with a mouse that has a failing left click.  Sometimes the left click just doesn't "take."  It will also release itself while I'm holding down the left button, e.g. when dragging a scroll bar around.  I can't tell, by feel, the difference between a good click and a failed click (and I'm normally pretty sensitive to these things).  You should really either try a different mouse, or try that mouse on another computer.

Editing your xorg.conf for a USB mouse shouldn't be necessary, either.  And there's no reason to use the PS/2 connection when you have a USB connection available.

---

### Post by thomasaaron on 2009-02-06
I second (third?) that. I've never had to configure the xorg.conf for a standard USB mouse. I'd not get into that until I tested with another known-good mouse.

---

### Post by jdb on 2009-02-06
> **Teasdale said:**
> I've looked up ps/1 and looked at the back of my computer. I *do* have a ps/1 connector, so I'm pretty sure I need to to switch my mouse from usb to ps/1.

Is making changes to the xorg.conf file the only way to do that? Do I need to add a section to the document, like this?

[I]Section "Mouse"
Identifier "???"
Driver PS/1?
EndSection[/I]

Switching to a USB mouse is probably the easiest fix.
I use a PS/1 on that desktop because it connects to an old belkin mouse/keyboard/monitor switch box that won't handle USB.


Below are some excerpts from the xorg.conf on my desktop that has a PS/1 mouse.

Mouse1 is an arbitrary name, but the name in the "ServerLayout" section has to match the name in the "InputDevice" section.

Be sure to make a backup copy of xorg.conf before you make any changes in it.


```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse1" "AlwaysCore"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection


Section "InputDevice"
    Identifier  "Mouse1"
    Driver      "psmouse"
    Option      "Device" "/dev/input/mouse0"
    Option      "SendCoreEvents" "true"
    Option      "Protocol" "PS/2"
    Option      "Buttons" "3"
EndSection



```


jdb

---

### Post by Teasdale on 2009-02-07
I plugged another mouse in - and it seems to be working. So it must have been an odd coincidence that my mouse went bad at the same time I replaced the PC? Thanks for all the help!

---

### Post by Guille Damke on 2009-02-08
Hi Teasdale,
I hope that the new mouse keeps working fine, let us know. I think this told us what Murphy's law is!
The final proof would come if you try the old mouse in another machine.
Good luck using the new mouse, and enjoy GNU/Linux.

---

