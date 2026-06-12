---
title: "Is it possable to make a program that installs and configures windows wireless driver"
date: 2009-03-22
forum: The Cafe
---

### Post by swoll1980 on 2009-03-22
Like using a few programs as a backend like ndiswrapper, and cabextract to just pull a win driver.exe off the internet, install it , and configure it, you know the modprobe, adding it to etc/module, and all that good stuff.

---

### Post by kevdog on 2009-03-23
Why would you want to use ndiswrapper when many chipsets now have native drivers available?

---

### Post by Chemical Imbalance on 2009-03-23
I believe ndisgtk does everything you mentioned except download the binary blob.

---

### Post by Polygon on 2009-03-23
cause some various chipset versions are still not supported by the native drivers....some ndiswrapper is still needed.

usually those drivers come with a .inf file  which is the install information

---

### Post by swoll1980 on 2009-03-23
> **kevdog said:**
> Why would you want to use ndiswrapper when many chipsets now have native drivers available?

Even a lot of the ones that do have native drivers, have issues. like mine is extremely slow with native driver.

---

### Post by swoll1980 on 2009-03-23
> **Chemical Imbalance said:**
> I believe ndisgtk does everything you mentioned except download the binary blob.

Not even close. First off you have to find a driver that isn't in the form of an exe, which most of them are. Then you use ndisgtk, then you have to configure the module to start at boot. Before the elitist break in, and start crying about how easy this is(which I'm sure you will anyways) just remember, your not an average user. I'm wondering if it would be possible to make a program that can eliminate these hassles. Also don't feel the need to give me advice. I know how to do all these things, and think new users could benefit from a more intuitive approach.

---

### Post by kevdog on 2009-03-23
What chipset do you have?  You know that the ndiswrapper project hasn't been maintained since late 2007?!

---

### Post by swoll1980 on 2009-03-23
> **kevdog said:**
> What chipset do you have?  You know that the ndiswrapper project hasn't been maintained since late 2007?!

I have a bcm4306 tansfer rates with native driver are 73kb/sec they should be like 500kb/sec range is significantly impaired as well.

---

### Post by kevdog on 2009-03-23
Hmm
I have a bcm4306 chipset as well and have been most impressed with the openfwwf driver.  I haven't actually measured transfer speed (don't know of a reliable utility for this), however just to me -- ndiswrapper vs openfwwf -- no difference to me as a user.  In addition I can do monitor mode with openfwwf -- try that with ndiswrapper!

---

### Post by SunnyRabbiera on 2009-03-23
Would need something similar to wine I assume, its possible to make a app like this but how practical is it in the end?

---

### Post by swoll1980 on 2009-03-23
> **kevdog said:**
> Hmm
I have a bcm4306 chipset as well and have been most impressed with the openfwwf driver.  I haven't actually measured transfer speed (don't know of a reliable utility for this), however just to me -- ndiswrapper vs openfwwf -- no difference to me as a user.  In addition I can do monitor mode with openfwwf -- try that with ndiswrapper!

I noticed it the most when updating or downloading things. Transfer rates from the repos were horrible, I plugged it in and they were fine, so I tried the windows driver, and again they were fine, tried the native ones again just to make sure, and I was back down to 73kb/sec again, tried transferring files from my network, still slow, tried download 2 files to see if I could break the 73kb/sec barrier, but got 2 x 36kb/sec instead, installed win drivers works fine again. Also with win drivers I can go anywhere in my house, and get full bars. with the native drivers if I'm ten feet away I loose a bar if I go in my bedroom I only get 1-2 bars, and even loose the signal sometimes.

---

### Post by Chemical Imbalance on 2009-03-23
> **swoll1980 said:**
> Not even close. First off you have to find a driver that isn't in the form of an exe, which most of them are. Then you use ndisgtk, then you have to configure the module to start at boot. Before the elitist break in, and start crying about how easy this is(which I'm sure you will anyways) just remember, your not an average user. I'm wondering if it would be possible to make a program that can eliminate these hassles. Also don't feel the need to give me advice. I know how to do all these things, and think new users could benefit from a more intuitive approach.

just extract the .exe then

i dont use ndisgtk so i guess i heard wrong

I understand what you mean about the beginner's perspective, but I don't believe "not even close" is very fair.  Talk to the devs of ndisgtk and request features.

---

### Post by dirtylobster on 2009-03-23
Check out Linux Mint.

---

