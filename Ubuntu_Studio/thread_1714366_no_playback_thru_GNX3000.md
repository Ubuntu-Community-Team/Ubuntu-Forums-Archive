---
title: "no playback thru GNX3000"
date: 2011-03-25
forum: Ubuntu Studio
---

### Post by GhostofJohnToad on 2011-03-25
Been trying to get my Digitech GNX3000 guitar device working with Ubuntu Studio 10.10.  Device was recognized by just plugging in the USB.  A little tweaking to some settings in qjackctl and was able to get input working.  Recoded some little bits in Ardour fine.  When I went to playback I have no sound.  I have he GNX3000 working fine for both recording and playback in windows so I know the USB port is working.  Messed around with all the possibilities in Ardour for playback ports, but nothing.

One thing I noticed is under qjackctl it lists hw:1 - GNX, and hw1:0 - USB.  I tried switching between the two for output but nothing gets me closer.  

Anyone have any ideas or already have this thing working?

---

### Post by GhostofJohnToad on 2011-03-25
ok, I got the playback working.  It was one of 2 things.  Either unplugging the cord I had left plugged into the one of the output jacks of the GNX3000(usually goes to the amp).  Or it was merely plugging into a different usb port on my computer.  More than likely the 2nd.  

Although now that I have it working I am not too happy that the GNX3000 doesn't have hardware monitoring cause now the latency is an issue.

---

### Post by sgx on 2011-03-26
Is the Periods/Buffer setting in the qjackctl setup panel at 3?
Even numbers 2 and 4 are supposed to be bad luck for usb devices.
The other values can be adjusted according to need. The output
device can be your system soundcard, when used with a guitar input
device. 
Cheers

---

