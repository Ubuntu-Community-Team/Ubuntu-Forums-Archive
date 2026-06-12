---
title: "JACK hardware recognition"
date: 2008-08-26
forum: Ubuntu Studio
---

### Post by zsoltyV on 2008-08-26
Hi, I'm trying to get a Presonus Firepod to work with Ubuntu studio 8.04.  

I have been able to get JACK running using freebob, as well as the FFADO beta.  I can see firewire device device in device manager as well as gscanbus, i'm getting no errors in JACK's message window, and the blue light is on on the firepod, but i can't see any of the connections in the Patchbay or the connections windows (in Qjackclt).  There seems to be no "Client" associated with the firepod. (?)

I've tried two drivers, freebob and FFADO, with the same result.

Any input that may help me get to record some music would be appreciated.

-m

---

### Post by Stochastic on 2008-08-27
hmm, strange.  I'd guess it's an issue inside qjackctl.  First, while jack is up and running, try opening patchage - it's a replacement for the qjackctl patchbay that has more features (including the ability to save connections - though any LASH session would do the same in qjackctl).

If that doesn't solve it for you, then run jack in verbose mode from the command line: ```
jackd -r -v -dfreebob
``` then open either qjackctl or patchage.  If you still don't see connections, post the output of the jackd command, and I'll compare it with my results for any abnormalities.

---

### Post by zsoltyV on 2008-08-27
Ha - got it!

Thanks for the input, Stochastic.

My system was showing "capture_1" "capture_2" etc.  which i wrongly assumed to be **not** the firewire device, but it was.  The -v option for running jackd clued me in with this:
```

firewire MSG: Registering audio capture port C0_dev0_LineIn 1+2 left
registered port system:capture_1, offset = 4096
firewire MSG: Registering audio capture port C1_dev0_LineIn 1+2 right
registered port system:capture_2, offset = 8192
```

etc...

So, i guess it had been working all along.  now i understand it all a little better.  And firepod works with ffado!

-m

---

