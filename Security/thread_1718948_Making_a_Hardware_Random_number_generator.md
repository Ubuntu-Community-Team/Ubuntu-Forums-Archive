---
title: "Making a Hardware Random number generator"
date: 2011-04-01
forum: Security
---

### Post by smittycity on 2011-04-01
So... I think this is the rite spot to post. I have one of these:

[http://www.radmeters4u.com/](http://www.radmeters4u.com/)

I'd like to somehow connect a serial port to a headphone jack, plug it into the geiger counter and literally dump random noise from the geiger counter into the entropy pool used by /dev/random

So... where should I start?

---

### Post by BkkBonanza on 2011-04-01
Nuclear powered random number generator? I doubt that would be very random. Not because the background radiation isn't but because the handling of the signal through a serial port would introduce patterns.

You would be better to feed the signal into a A/D converter (like a sound card or usb sound dongle) and then work with the digital output from that device. Even still I suspect it wouldn't be more random than /dev/urandom.

---

### Post by smittycity on 2011-04-01
Ok, so wire up a headphone jack to a usb. My goal is simply to tell the kernel to use the device as a new source of entropy, not to replace /dev/random or /dev/urandom. So where do I start?

---

### Post by BkkBonanza on 2011-04-01
Once you can record sound coming in from the usb sound dongle, you could probably write a driver to take the sounds data and present it as a device eg. /dev/nuclear. That's pretty advanced though. You may be able to just create a syslink from the sound device to a dummy /dev/nuclear for example. But a driver would allow you to alter the data stream in some way.

You'd probably need some filter / amplifier circuit on the sound input too, but maybe not. An op amp could be used for that. First, see what others have done with Google.

eg. 
[http://www.vanheusden.com/aed/](http://www.vanheusden.com/aed/)

[http://www.entropykey.co.uk/](http://www.entropykey.co.uk/)

... that's just the first minute looking.

Also interesting,

[http://world.std.com/~reinhold/truenoise.html](http://world.std.com/~reinhold/truenoise.html)

[http://qrbg.irb.hr/](http://qrbg.irb.hr/)

---

### Post by smittycity on 2011-04-01
Rite, I actually don't post on anything very often because google treats me so well, but this was a bit broad and the first thing I started looking for was for how to write a serial port driver. So thank your for your search terms! The audio entropy daemon looks very promising.

---

### Post by tgm4883 on 2011-04-01
If you are doing this for fun, good on you. If you are doing this because you want entropy, you might want to check out [http://www.entropykey.co.uk/](http://www.entropykey.co.uk/)

Note: I'm not affiliated with this company.

---

### Post by Agent ME on 2011-04-02
If I remember right, you can just write to /dev/random to influence the system random number generator.

---

### Post by rookcifer on 2011-04-02
OP, you would probably do well to check out sci.crypt.  There's a lot of knowledgeable people there (as long as you can tolerate the typical Usenet trolls).  

As for the geiger counter, theoretically it should give a true quantum source of noise, but practically it will be difficult to make that happen.  For one, you will have to debias the output because, as the guy above said, you will have electrical interference when you hook it into your machine.  Another issue is you must design some sort of mechanism to warn of hardware failures.

So, as you can see, designing a TRNG is very difficult.  You would be better served to just use /dev/random for crypto keys and the like, as it will likely offer better numbers than a homebrew RNG design and has been around long enough to give us an idea of its security.

---

