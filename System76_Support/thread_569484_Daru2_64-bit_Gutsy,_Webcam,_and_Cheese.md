---
title: "Daru2 64-bit Gutsy, Webcam, and Cheese"
date: 2007-10-07
forum: System76 Support
---

### Post by reh4c on 2007-10-07
I can happily report that Cheese 0.2.3 works perfectly when installed with Synaptic on Gutsy 64-bit beta on my Daru2.  Still pics and videos with sound look very good.  I did have to adjust sound settings for the external mic to work...a bit tricky.  :guitar:

Also, onboard SD card reader works perfectly "out of the box"!!!

---

### Post by palintheus on 2007-10-16
what did you have to do to get the external mic working, I am debating going to the 64bit, and want to upgrade to gutsy soon.

Also have you noticed any other issues?

---

### Post by thomasaaron on 2007-10-16
You could try adding this line to the bottom of the /etc/modprobe.d/alsa-base file:
 options snd-hda-intel model=targa-dig

(This may work best with Alsa 1.0.15rc3.)

Then reboot.

---

### Post by theologian aaron on 2007-10-16
Are there any noticeable advantages to 64-bit?  I've been wondering about this for awhile.  I run 64-bit feisty on a desktop, and it's seems that the glitchyness outweighs the tiny increase in speed.

Is it just novelty?  I'm not above doing things just because they are cool.  We are all nerds after all!

---

### Post by steveneddy on 2007-10-16
> **theologian aaron said:**
> Are there any noticeable advantages to 64-bit?  I've been wondering about this for awhile.  I run 64-bit feisty on a desktop, and it's seems that the glitchyness outweighs the tiny increase in speed.

Is it just novelty?  I'm not above doing things just because they are cool.  We are all nerds after all!

Your PC was designed to run a 64 bit OS and the "glitchyness" is non-existent.

My laptop is snappier, smoother, sounds better and the video looks great - I can really tell a difference.

All of the codecs are available for 64 bit and you shouldn't have any problems running anything that you want.

Install the new Gutsy 64 bit when it comes out, you will be much happier.

:popcorn:

---

### Post by greg_g on 2007-10-17
My only question is why do they label the disk iso as "amd64" not "64bit"

---

