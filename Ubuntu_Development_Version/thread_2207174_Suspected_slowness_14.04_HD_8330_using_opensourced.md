---
title: "Suspected slowness 14.04 HD 8330 using opensourced drivers."
date: 2014-02-22
forum: Ubuntu Development Version
---

### Post by open2reason on 2014-02-22
I am running 14.04 latest daily 64bit (AMD a4-5000 HD 8330 + 4GB ram) and have noticed what I think to be a slowdown and general sluggishness when using [http://www.kongregate.com/games/preecep/desktop-tower-defense](http://www.kongregate.com/games/preecep/desktop-tower-defense) browser based 2d game when comparing the running under 12.04.4 with that under 12.04.4 . In 14.04 I am using the latest open sourced drivers as illustrated under Ubuntu Software > Additional Drivers.

Can anyone please advise me of a command I can use that will allow me to measure any difference between the 12.04.4 and 14.04 performance?

Thanks a lot.

---

### Post by ventrical on 2014-02-22
working good here on my AMD HD 5450 Silent w  Gallium 0.4 on AMD Cedar

---

### Post by open2reason on 2014-02-22
A whole can of worms.

Glxgears on 12.04.4 with VESA: KALINDI                 using AMD/ATI propriety FGLRX (post release updates) gives a score in the range of 1276 - 1235
Glxgears on 14.04      with Gallium 0.4 on AMD KABINI using x.org xserver AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source) gives a score of 60.

At this point I attempted to change the 14.04 system from open source to AMD/ATI graphics accelerators from fglrx-updates (propriety) and the update system failed with an error while applying the new drivers.

Will have another attempt tomorrow to recreate 14.04 results and errors.

Any hints as to filling in a launchpad request if one is requested / required?

Thanks.

---

### Post by ventrical on 2014-02-22
You have to create a launchpad account here :

[https://launchpad.net/](https://launchpad.net/)

 and the rest is self explanatory.

---

### Post by zika on 2014-02-23
> **open2reason said:**
> I am running 14.04 latest daily 64bit (AMD a4-5000 HD 8330 + 4GB ram) and have noticed what I think to be a slowdown and general sluggishness when using [http://www.kongregate.com/games/preecep/desktop-tower-defense](http://www.kongregate.com/games/preecep/desktop-tower-defense) browser based 2d game when comparing the running under 12.04.4 with that under 12.04.4 . In 14.04 I am using the latest open sourced drivers as illustrated under Ubuntu Software > Additional Drivers.

Can anyone please advise me of a command I can use that will allow me to measure any difference between the 12.04.4 and 14.04 performance?

Thanks a lot.gtkperf

---

### Post by open2reason on 2014-02-26
Zika,
thanks for your tip. I'll give 14.04 another try in a couple of weeks or so.

---

