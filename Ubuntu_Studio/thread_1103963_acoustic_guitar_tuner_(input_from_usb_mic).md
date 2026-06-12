---
title: "acoustic guitar tuner (input from usb mic)"
date: 2009-03-23
forum: Ubuntu Studio
---

### Post by amrclutch1 on 2009-03-23
Is it possible to use the input from a USB microphone to tune a guitar? If so, is anyone aware of an application that is capable of this?

---

### Post by thorgal on 2009-03-23
[http://www.geocities.com/SiliconValley/Hardware/2684/kguitune_page.html](http://www.geocities.com/SiliconValley/Hardware/2684/kguitune_page.html)

don't know if it takes any input (ALSA, OSS, jack ?) as it's not specified but it must support at least one audio interface, hopefully ALSA by default if your USB mic is driven by ALSA.

---

### Post by buminatrain on 2009-03-29
in my opinion the best option for this is fmit, i wrote a quick tutorial for installing and running this in ubuntu on my blog [http://rocket-to-the-moon.com]("http://www.rocket-to-the-moon.com") in your case your mic will probably be hw:1

---

### Post by Stochastic on 2009-03-29
+1 for fmit.

---

### Post by kayosiii on 2009-04-01
fmit (you will need to have a functional Jack)

---

### Post by MrChainBlueLightnin on 2009-09-24
I installed FMIT, and it shows up under applications.  However, when you click on it nothing happens. Any suggestions?

---

### Post by kayosiii on 2009-09-25
you need to have jack running
you will also need to route inputs its input to the inputs from your device

I reccomend installing patchage for this task

---

### Post by Rhetoric Camel on 2009-10-06
tried Fmit, I don't have Jack but I am using a usb mic, I get it to show that there is sound coming in through the mic, but the tuner itself doesn't move at all, so it's not doing much as a tuner. Is it because I don't have jack although it's showing signs of picking up noise?

---

### Post by kayosiii on 2009-10-06
> **Rhetoric Camel said:**
> tried Fmit, I don't have Jack but I am using a usb mic, I get it to show that there is sound coming in through the mic,
so you are seeing a waveform in the capture sound area of the ui?

>  but the tuner itself doesn't move at all, so it's not doing much as a tuner. Is it because I don't have jack although it's showing signs of picking up noise?

You need a pretty good signal to be able to get it to tune...
Your peak wavforms should be getting close to the edge of the window... but not clipping it. repositioning the guitar can help with this.
the note stability button should go green when it can detect the note.

It might be worth recording from the mic and see whether you are getting decent settings.

---

### Post by Rhetoric Camel on 2009-10-10
thanks for the help I figured it out, my mic was turned all the way down, it was enough for recording in audacity but wasn't enough to pick up the sound properly in FMIT... great tuner. Thanks for the help.

---

