---
title: "Edirol UA-4fx Kernel patch to the Advanced mode - help"
date: 2008-07-10
forum: Ubuntu Studio
---

### Post by rlameiro on 2008-07-10
Hi everyone. 
I have an [Edirol UA-4FX (USB)]("http://www.roland.com/PRODUCTS/en/UA-4FX/index.html") Audio/MIDI interface that works in linux, but only 44.1khz and 16 bits, no midi. The interface have an advanced switch that enables more sample rates and also 24bits. 
I found a patch in the in [http://alsa.opensrc.org/index.php/Edirol_UA-4FX](http://alsa.opensrc.org/index.php/Edirol_UA-4FX) but the problem is that I don't know how to patch the Kernel to put it to work.

I would like to have at least the midi working, the high sample rates are not a priority since for now I am looking to make real time music performances using midi controllers to start Pd patches etc.
Any help will be apreciated

---

### Post by rlameiro on 2008-07-13
*bump*

---

### Post by rlameiro on 2008-07-16
bump again, sorry:) anyone who knows how to pach this to the kernel?

---

### Post by hypermusician on 2008-07-25
I also have this sound card and would like to know how to do this. Haven't been able to work it out so far.

---

### Post by djxcon on 2008-08-05
Have any of you found that when this card is running in Jack, there is a high pitch sound coming into the inputs and this sound actually gets recorded?  I can hear this sound as soon as Jack is enabled.  This is not happening in Windows and I only make that point to show that this is not a problem with the device itself.  

I am also not trying to hijack this thread, as I also would like to know how to apply the patch.  I have reviewed the ALSA site and found that running the ```
cat /proc/bus/usb/devices
``` command does not yield the same results as what's on the page.

---

### Post by chunter on 2008-10-05
*bump*

The trick is to save a .diff file that has code text quoted in this link: [http://alsa.opensrc.org/index.php/Edirol_UA-4FX#Getting_Advanced_mode_to_work](http://alsa.opensrc.org/index.php/Edirol_UA-4FX#Getting_Advanced_mode_to_work)

Then find the part of the linux kernel source that contains the three files mentioned, 'cd' to it, then use "sudo patch < your-saved-edirol-patch.diff" and finally, do a compile.

I'll give more detailed instructions on that when I have a little more time (and actually have mine working).

---

