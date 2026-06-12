---
title: "Qtractorl, phasex broken after usb fiddling"
date: 2012-07-11
forum: Ubuntu Studio
---

### Post by hamnstar on 2012-07-11
Long story short, borked my snd-usb-audio kernel modules and recompiled them.  Now phasex segfaults and qtractor fails out immediately after loading.

details of operations i performed are here: [http://cheftroyrd.blogspot.ca/2012/07/getting-m-audio-fast-track-ii-working.html](http://cheftroyrd.blogspot.ca/2012/07/getting-m-audio-fast-track-ii-working.html)

I'm not certain why this isnt working and could use some direction...... notably phasex and qtractor no longer work.  No issues with ardour, qjackctl, or hexter so far.  

Running ubuntu studio 12.04

Please help!!!:confused:

---

### Post by sgx on 2012-07-11
If like many, you love the experiment, you might want to do a new install, with a separate /home partition, so when things go
sideways, you can reinstall, with most personal settings intackt
by not reformatting /home during a new install.

I have that itch sometimes, with a pile of usbsticks
and external drives to experiment with. 

In the interim, you can install an alternate kernel to boot from,
and reinstall all the dependencies of qtractor and phasex,
might get you back to recording. There is a recent release of
qtractor at the authors website.

[http://www.rncbc.org/drupal/node/503](http://www.rncbc.org/drupal/node/503)

Cheers

---

### Post by hamnstar on 2012-07-11
Thx for the suggestion, the /home partition sounds pretty enticing actually....

For now I stuck my old /home on my secondary hard disk and reinstalled.  didnt have too many settings anyway.  Reinstalled from DVD and that seems to have fixed the problem :)

Note: this took way less time than it did for me to half-assedly fix it in the first place!

---

