---
title: "basic audio setup"
date: 2012-03-31
forum: Ubuntu Studio
---

### Post by earthshakergb on 2012-03-31
Is there a place I can find how to setup basic audio stuff?
Ok the audio is working, but if I need to change some settings I am not sure how to do it.
I have used the ALSA mixer, and the pulse, volume control but neither seem to control the levels from the microphone, or it could be the mic is just bad.
Anybody have a quickstart guide?

---

### Post by sgx on 2012-04-01
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

links 4 and eight cover basic setup for recording

output from these commands lets you see how the kernel
IDs your gear

aplay -l
arecord -l
aconnect -i
aconnect -o
cat /proc/asound/cards
cat /proc/asound/devices
lsmod
lspci
lsusb

lsmod lists kernel modules, and which ones are used
by one another. The naming of a module may be similar to
names in the output of the other commands. Info from the links,
can show where to insert names found in brackets.

qjackctl setup page

Input Device >
Output Device >
click the > for a dropdown list of your available sound devices.
The qjackctl Periods/Buffer setting should be 3 for usb devices.

Models and brands of your gear help insure good results.
Cheers

---

