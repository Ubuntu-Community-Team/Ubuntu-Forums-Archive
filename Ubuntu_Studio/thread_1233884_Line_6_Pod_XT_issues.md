---
title: "Line 6 Pod XT issues"
date: 2009-08-07
forum: Ubuntu Studio
---

### Post by Atanas88 on 2009-08-07
Hi everyone,

I am using Ubuntu 9.04 and I wanted to record through USB with my Pod XT so I installed the 0.8.1 usb drivers and It works great (I can record and play through the Pod XT with Ardour) ...
My problem is that when my Pod XT is connected to my laptop USB port it changes its settings while I am playing (It changes the amp and the effects) It happens quite a lot and it's really annoying.

Anyone knows how I could fix this ?

PS: Sorry if I made mistakes, I'm from France.

---

### Post by sgx on 2009-08-07
Hi, with midi connected, my external drum machine can change internal synth parameters against my will, merely by my changing beats, so knowing things are not always locked down, I would start in the bios, turn off any networking, bluetooth, webcam, etc
make sure the pod is the only usb item plugged in, start from power off,
and use no apps other than ardour, and jackd. If you are recording audio
from the pod line-out, to a computer line-in, make sure there are no midi connections that could transmit wild program-change data from some villain. Internal midi connections can be seen with qjackctl, or kaconnect, and can be disconnected in their gui. You might try different usb ports and cables too, trying to dodge a faulty connector, and also, try a different computer if possible, or load a newer stock kernel, the
RT kernels after Ubuntu Studio 8.04 have had issues, so go with 8.04 RT, or the newest synaptic repository stock kernel.
Detailed computer details would help the power users here to do a better diagnosis, I'm more of a 'wiggle the cord' technician :D

---

### Post by Atanas88 on 2009-08-08
Thank you for answering

I installed the rt kernel with apt get (basically I followed a part of the ubuntu studio preparation guide)
I also checked the  connections with Jack and I think there's nothing wrong.
I am going to try different USB ports and if it doesn't work I think I'll try with Debian amd64 or Studio64.

Do you have other suggestions ?

---

