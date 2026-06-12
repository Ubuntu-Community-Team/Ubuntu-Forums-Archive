---
title: "Alsamixer not showing M-Audio Audiofile 192 inputs"
date: 2009-05-25
forum: Ubuntu Studio
---

### Post by Pinck on 2009-05-25
Hey,

I've been banging my head against this for some time, including a fair bit of googling.

For my M-Audio Audiophile 192 I can't seem to use the inputs.  When I go into alsamixer, my capture definitely does not look right.  Up and down arrows do nothing to this slider.

Any thoughts on where to start?

---

### Post by thorgal on 2009-05-25
use the mixer app called envy24control
it is part of the alsa-tools-gui package.

This is THE mixer app for envy24 based cards like yours.

You may need to read a bit about how to use it as it is a bit subtle:

[http://alsa.opensrc.org/Envy24Control](http://alsa.opensrc.org/Envy24Control)

---

### Post by Pinck on 2009-05-25
Is there a way to get Envy24Control to work for non-ice1712 cards?  My Audiophile 192 is ice1724 based.

john@ubuntu:~$ envy24control
No ICE1712 cards found
john@ubuntu:~$ 


Thanks!

> **thorgal said:**
> use the mixer app called envy24control
it is part of the alsa-tools-gui package.

This is THE mixer app for envy24 based cards like yours.

You may need to read a bit about how to use it as it is a bit subtle:

[http://alsa.opensrc.org/Envy24Control](http://alsa.opensrc.org/Envy24Control)

---

### Post by Pinck on 2009-05-26
Please let me know if there's any files/logs I should be looking at or what.  I really just don't know where to go from here.

---

### Post by thorgal on 2009-05-26
hi there,

looks like I misled you thinking your card was ice1712 based. 

mmm, tough luck, looking at the ALSA page and no particular mixer app shows up for it. You will have to be on an ALSA user mailing list of some kind as this is not specifically ubuntu related

---

### Post by Stochastic on 2009-05-26
The Audiophile 192 should work with envy24control.  You may have something not setup right.

Are you getting sound out of the card right now?  What setup steps have you taken with this card?

---

### Post by nubasorious on 2009-08-07
Unfortunately I went through the same headache as you have.  Audiophile 192 not supported by Ubuntu.  I went and traded (unfortunately downgraded) mine in for a Audiophile 2496 card which works really well in Ubuntu Studio Hardy....now if I could only get it to work in Ubuntu Studio Jaunty!!!!!!!!!!  arg!:confused::twisted:](*,)

Ryan

---

### Post by sgx on 2009-08-08
> **nubasorious said:**
> Unfortunately I went through the same headache as you have.  Audiophile 192 not supported by Ubuntu.  I went and traded (unfortunately downgraded) mine in for a Audiophile 2496 card which works really well in Ubuntu Studio Hardy....now if I could only get it to work in Ubuntu Studio Jaunty!!!!!!!!!!  arg!:confused::twisted:](*,)

Ryan
Newer and better in linux are not always the same thing. Was your 24/96 a new one, an older used model, or a new old-stock? Mine is vintage 2003, I have read folks say new 24/96, and all 24/192 will not work, and if yours is recently manufactured, but works, I don't want to wrongly steer people away from a product that is still useful.
Cheers

---

### Post by sgx on 2009-08-08
> **nubasorious said:**
> Unfortunately I went through the same headache as you have.  Audiophile 192 not supported by Ubuntu.  I went and traded (unfortunately downgraded) mine in for a Audiophile 2496 card which works really well in Ubuntu Studio Hardy....now if I could only get it to work in Ubuntu Studio Jaunty!!!!!!!!!!  arg!:confused::twisted:](*,)

Ryan
Newer and better in linux are not always the same thing. Was your 24/96 a new one, an older used model, or a new old-stock? Mine is vintage 2003, I have read folks say new 24/96, and all 24/192 will not work, and if yours is recently manufactured, but works, I don't want to wrongly steer people away from a product that is still useful.
Cheers

---

