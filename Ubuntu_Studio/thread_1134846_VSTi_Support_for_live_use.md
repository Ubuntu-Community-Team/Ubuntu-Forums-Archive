---
title: "VSTi Support for live use?"
date: 2009-04-24
forum: Ubuntu Studio
---

### Post by Noise... on 2009-04-24
I'm new to Ubuntu Studio, and I'm currently dual-booting with Vista. 

One big thing that I need to be able to do, is to use VSTi's for live applications. For example, plugging in my keyboard, then setting up a VSTi, and having my headphone jack go out via a 1/8" to 1/4" adapter to an amplifier.

I use this a lot for piano and rhodes sounds. Is it possible to do the same in Ubuntu Studio?

---

### Post by Stochastic on 2009-04-24
Yes it is possible in Ubuntu Studio.  You may find it a touch more complex though.

First you should know that VST is not a widely supported format in Linux audio due to Steinberg's license. You may have more pleasure working with some DSSI instruments, or other soft synths (possibly a soundfont synth if you're looking for rhodes sounds).

To get VSTi instruments running on a standalone setup like you describe, you'll need to install one of the hosts.  Unfortunately, because of the pesky VST license, no sandalone hosts are in the repositories so you'll need to manually install them.  There is hope that with the new Vesteige headder these issues will go away in the future, but for now you must manually install them.

The standalone VSTi hosts that I'm aware of are:
Jost: [http://www.anticore.org/jucetice/?page_id=4](http://www.anticore.org/jucetice/?page_id=4)
FST: [http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/)
DSSI-VST (a plugin for DSSI hosts to be able to handle VST): [http://breakfastquay.com/dssi-vst/](http://breakfastquay.com/dssi-vst/)

I should note that other apps (not standalone hosts) can be compiled with or come already packaged with VST support, those include: Audacity, Ardour, LMMS, Renoise, EnergyXT, Reaper(must run in wine)

Also you may find this database of VST instruments and plugins that run on Linux very useful: [http://ladspavst.linuxaudio.org/](http://ladspavst.linuxaudio.org/)

---

