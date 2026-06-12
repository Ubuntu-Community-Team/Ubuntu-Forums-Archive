---
title: "How do I set up my M-Audio fast track usb?"
date: 2012-05-09
forum: Ubuntu Studio
---

### Post by pixelmad on 2012-05-09
I am new to Ubuntu Studio 12.04 and pretty much a Linux noob.
That being said, I have just finished installing UbuntuStudio 12.04
and I want to record with my M Audio Fast Track USB device.

I do not know where to begin looking for help and can't seem to find
any relevant tutorials on how to do this, or even where to begin...
Please can someone help me with this?

---

### Post by sgx on 2012-05-10
Hi, look at links 4 an 8 at the qjackctl wiki

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

It will have screenshots and info. jackd is the sound server,
qjackctl the gui for its settings and connections.

Start qjackctl, click theSetup button

look in qjackctl setup page, on the right side
Input Device >
Output Device >

click the >  
to open a dropdown menu, the m-audio should be there when recognized.
Use a Periods/Buffer setting of 3.

useful commands, look at their output to ID your soundcards
in linux terminology

cat /proc/asound/cards
aplay -l
arecord -l
aconnect -i
aconnect -o

The m-audio name found in brackets, can be used in the qjackctl dropdown menus instead of hw:0,0 or hw:1 or other similar numeric entries, if those do not work.  ice_1712 is the m-audio kernel module, if you see that within brackets, it can also be used

Mine is a different maudio card, the setting is hw:0,0
and the dropdown list has

ICE1712 multi
M Audio Audiophile 24/96

All three choices will work. Yours may be slightly different.
The wiki pages should show the
connections process, highlight an item of software or hardware
on each side of the display, and press the connect button.
Connect a continuous sound source to computer line-in, so you hear
a successful connection.

envy24control is a mixer for maudio devices (others also work fine)
make sure sound is unmuted.

Cheers  (see youtube for ardour, hydrogen, zynaddsubfx, rakarrack
as these often show the setup and connections of qjackctl)

---

