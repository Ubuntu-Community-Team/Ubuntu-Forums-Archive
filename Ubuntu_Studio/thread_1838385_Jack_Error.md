---
title: "Jack Error"
date: 2011-09-03
forum: Ubuntu Studio
---

### Post by stagekraft on 2011-09-03
Hey all,

has anyone had this error, and what does it mean?

> JACK hes either been shutdown or it
disconnected Ardour because Ardour
was not fast enough. Try to restart
JACK, reconnect, and save the session.

I started getting this recently, when I'm playing back some tracks.

regards, John

---

### Post by sgx on 2011-09-03
Hi, in qjackctl setup panel, try increasing 

Timeout (msec)

to over 1000

Don't use Freeverb, or TAP Equaliser, other plugins
may also be culprits.

Try the latest ardour beta, it's a simple manual install.
In my limited tests,
the beta versions are very stable. 

Cheers

---

### Post by stagekraft on 2011-09-10
sgx:
 thanks for the input, but changing the timeout did not help.......
and I'm not running any plug-ins at this point......

any other ideas from anyone?

John

---

### Post by sgx on 2011-09-11
jack2 may be needed as it forgives many timing problems. If you already use it, try stair-stepping the frames/period period/buffer settings to higher values. 3 is recommended for periods/buffer on usb devices.
 

The kernel timer should be at 1000 mhz for solid audio i/o

Trying avlinux, or remixos live media may be worth a try, and compare
ardour/jackd/kernel versions

.Liquorix kernel is a popular replacement:  [http://liquorix.net/](http://liquorix.net/)

The last alpha 3.x ready-to-run binary is here, (lots of bug-fixes)

[http://ardour.org/node](http://ardour.org/node)

[http://ardour.org/forum/15](http://ardour.org/forum/15)  is the ardour linux forum

Cheers
there are also hard-disk-buffering settings in ardour menus, in case hard-disk speed is an issue

---

