---
title: "Signal-Processing Software"
date: 2009-05-12
forum: Ubuntu Studio
---

### Post by Ubuntist on 2009-05-12
I'd like to do some signal processing.  For example, I'd like to apply a band-pass filter to an audio file stored in Ogg.  Does anyone know of any relevant OSS software packages out there?

---

### Post by eldragon on 2009-05-12
hmm, i dont remember what you could, and what you could not do with wavesurfer... but worth the try

otherwise, use octave....but you will need to know how those things are implemented in order to be useful (IDFT the desired filter, and convolute it with your file)

---

### Post by zero7404 on 2009-05-12
not sure if audacity will do it, but it's a pretty capable audio editing tool. it's also available for windows, so it's cross-platform....

---

### Post by markbuntu on 2009-05-12
There a Ladspa plug ins that will do that and a lot more. I do not know hw they work with OSS but they should.

---

### Post by Ubuntist on 2009-05-13
Thanks, everybody!  I didn't know that Octave had sound capability, and I'd never heard of Ladspa, which I'll look into.  Audacity, BTW, was the first thing I thought of, but it does not seem to have the capability that I need.

---

### Post by jpkotta on 2009-05-14
> **Ubuntist said:**
> Thanks, everybody!  I didn't know that Octave had sound capability, and I'd never heard of Ladspa, which I'll look into.  Audacity, BTW, was the first thing I thought of, but it does not seem to have the capability that I need.

Unless you need a specific filter, Audacity has a graphical eq.  The GUI is kind of broken, but it works.

---

### Post by Stochastic on 2009-05-15
If you do: ```
sudo apt-get install ubuntustudio-audio-plugins
``` Audacity will have a large amount of LADSPA plugins that it can use (including bandpass, lowpass, highpass, and notch filters).

---

