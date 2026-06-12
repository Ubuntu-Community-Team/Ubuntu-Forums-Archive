---
title: "Sound Blaster low level distortion problem.."
date: 2012-11-22
forum: Ubuntu Studio
---

### Post by jesushero on 2012-11-22
I am using Ubuntu Studio 10.04 on one of my recording systems and I'm having a problem with recording from my Soundblaster card..

No matter what kind of signal I feed to it, and no matter what kind of recording setting I choose (48khz/44.1khz - 16/24bit) on Ardour/Jack and Audacity, I can only get the recorded signal at -8 dB on the meters. Even if I feed a really strong signal, it will just peak and distort. 

So, it seems like 0 db on the Soundblaster is -8 db on the software side. How can I fix that? I already played around with the ALSA mixer and couldn't get much to change.

I know it is a crappy soundcard, but I would like it to work on a basic level. I occasionally need to use this system for archiving so I don't really need any better quality than the SB but I do need it to work properly.

---

### Post by CrocoDuck on 2012-11-23
Hi. I have a soundblaster 5.1 that I use everyday with pulsaudio, under Ubuntu Studio 10.04. I don't use if for recording because the electromagnetic noise inside the pc, but it works great and the midi connector is very useful. As always, make sure that the hardware is ok: if you have not already done it check the cables. Maybe your soundcard has some parameter that you can set via jumpers on the PCB, like preamplifier's gain. Make sure that everything is properly set referring to your device's manual. You could make a trivial experiment: try to change the PCI slot where you plug the soundcard (sometimes it works). If hardware is ok we have to deal with software issues.

---

### Post by jesushero on 2012-11-23
Hardware is fine, I've used it with 8.04 with no trouble. It's just changed since the upgrade to 10.04, but I didn't try recording until now so didn't notice.

The problem seems to be that the 0 db point of the soundcard does not correspond to the 0 db point on the software. It needs to somehow be "calibrated", so that the 0 db point in the software goes 8 db lower. So when an incoming signal hits 0 db on the soundcard, it would register as 0 db in the software as well, instead of -8 db as it is now.

Is there a "calibration" thingie anywhere? If I just increase the line-in level on the software, it just peaks more consistently and wildly at -8, but won't go above that.

So all the controls seem to do what they're supposed to do, but there is just a level difference. 

I am more used to dealing with this in the analog domain.. Gain on the card itself won't make much difference, as in with a jumper. I just need to "tell" the software where the 0db point is.

---

### Post by jesushero on 2012-11-23
Just found this:

[http://ardour.org/node/2161]("http://ardour.org/node/2161")

I am not really impressed with the whole discussion there, as everyone is being mutually unhelpful. 

But the problem seems to be the same. 


Now, to rephrase the question, according to that thread:

Is there a way to tell Jack or Ardour to show 0 when it sees -8?

Why is this so important: Because my analog interface does not have an accurate meter to show me if it would peak or not. So I would like to "see" ardour's opinion on whether something is peaking. You know, when it goes red on the mixer. That sort of thing. I find it very useful.

It is just the "visual feedback" that I want, the sound is fine as it is for what I need this for. I have a proper system for professional recording and it works fine. So I don't care if anything changes with the sound or not, I just want to SEE 0 db. Can I do it?

---

