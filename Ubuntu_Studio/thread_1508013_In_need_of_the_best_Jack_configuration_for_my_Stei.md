---
title: "In need of the best Jack configuration for my Steinberg MI4 usb sound card"
date: 2010-06-12
forum: Ubuntu Studio
---

### Post by accoustika on 2010-06-12
hello, I'm new to Ubuntu and I'm still trying to get the hang of it. I'm using the newest release of Ubuntu Studio and i have a Steinberg MI4 usb sound card and i need to have the best jack configuration for it as well as other settings that can give me optimal performance. Thank you

---

### Post by zettberlin on 2010-06-12
I use a MAudio MobilePre USB and it works for me like this:

/usr/bin/jackd -t2000 -u -dalsa -dhw:1 -r48000 -p128 -n3 -Xseq

---

### Post by AutoStatic on 2010-06-13
Optimal performance? Try these settings:
[LIST]
[*]Frames/Period: 48
[*]Sample Rate: 48000
[*]Periods/Buffer: 2
[/LIST]

That should give you a 2 ms latency. If you can get that running in a stable manner with your USB card then your system is well configured for use with realtime audio stuff. What I'm trying to say is that it's not only the config of your card that matters.

---

