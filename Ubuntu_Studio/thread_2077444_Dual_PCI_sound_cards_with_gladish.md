---
title: "Dual PCI sound cards with gladish?"
date: 2012-10-28
forum: Ubuntu Studio
---

### Post by jalor@yousee.dk on 2012-10-28
I am trying to run two Hoontech DSP 2000 ([http://www.st-audio.de/products/dsp2000/info.html](http://www.st-audio.de/products/dsp2000/info.html)) PCI cards simultaneously on Ubuntu Studio 12.04.

The cards work fine one at a time.

I have made an .asoundrc file that combines the two cards into one virtual card, and am using an SPDIF cable to provide clock synchronization between the cards.

This works when I use qjackctl to start up jack (it starts /usr/bin/jackd). It is not entirely stable though: ardour crashes at times etc., there's numerous (spurious?) xrun reports - no problem with the sound, but xruns are reported in abundance nonetheless.

But if I use gladish to start my sound programs, gladish apparently starts /usr/bin/jackdbus instead.

(is this something with jack1 vs jack2 or how do I know which one Ubuntu Studio uses?)

Further, when it's gladish / jackdbus that is running, the contents of my .asoundrc seems to be completely ignored. No matter what try to write in the "input" and "output" sound device fields in gladish's jack configuration window - it only works if I write physical sound device names (hw0, hw1); writing the pseudo sound device named (multi_capture, multi_playback) does not work.

Is using multiple sound cards supported in Ubuntu Studio? In gladish? Anyone doing it? Pointers to some recent documentation?

Thanks in advance,
/Jacob.

---

### Post by jejeman on 2012-10-28
12.04 uses JACK2 by default. You can switch to JACK1 if needed.
You can always check which JACK package is installed.

---

### Post by sgx on 2012-10-28
> **jalor@yousee.dk said:**
> I am trying to run two Hoontech DSP 2000 ([http://www.st-audio.de/products/dsp2000/info.html](http://www.st-audio.de/products/dsp2000/info.html)) PCI cards simultaneously on Ubuntu Studio 12.04.



try extrapolating this info:
[http://www.remastersys.com/forums/index.php?topic=1208.0](http://www.remastersys.com/forums/index.php?topic=1208.0)

[http://www.remastersys.com/forums/index.php?board=20.0](http://www.remastersys.com/forums/index.php?board=20.0)

The forum boss there has used a pair of maudio delta pci cards,
if you ask, or search around a bit, there should be info,
some of which may help: define a master-slave, sync
the clocks, etc
Cheers

[www.bandshed.net/pdf/AV6Manual.pdf](www.bandshed.net/pdf/AV6Manual.pdf)   maybe some help in the manual.

---

### Post by jalor@yousee.dk on 2012-11-01
> **sgx said:**
> try extrapolating this info:
[http://www.remastersys.com/forums/index.php?topic=1208.0](http://www.remastersys.com/forums/index.php?topic=1208.0)

[http://www.remastersys.com/forums/index.php?board=20.0](http://www.remastersys.com/forums/index.php?board=20.0)

The forum boss there has used a pair of maudio delta pci cards,
if you ask, or search around a bit, there should be info,
some of which may help: define a master-slave, sync
the clocks, etc
Cheers

[www.bandshed.net/pdf/AV6Manual.pdf](www.bandshed.net/pdf/AV6Manual.pdf)   maybe some help in the manual.

(how did this post end up in ubuntu_mobile? odd)

Thanks for the links. They look like what I have been following ([http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html) and [http://alsa.opensrc.org/TwoCardsAsOne](http://alsa.opensrc.org/TwoCardsAsOne))

Checking, I'm using jackd2. 

Some more thorough experimentation show that: Jack uses the multi_capture/multi_playback device defined in /etc/asound.conf when I start jack with qjackctl and tells qjackctl NOT to use jackdbus.

If qjackctl stats jack with jackdbus enabled, only one of the hadware cards is used. 

So the question really boils down to: Does jackdbus ignore /etc/asound.conf file or what is going on?

---

