---
title: "How does it work?"
date: 2010-11-08
forum: Ubuntu Studio
---

### Post by daveuu on 2010-11-08
Hi

I'm looking for up-to-date documentation on the Ubuntu Studio 10.10 implementation of ALSA, JACK and PulseAudio. I realise that each of the former have in depth documentation on how each works from the respective developers but I've recently installed Ubuntu Studio 10.10 and I've had issues with sound :-(

I realise the power of JACK and the power of PulseAudio and I think I understand the necessity of ALSA but I also know they each overlap in functionality and can be implemented in different ways with varying degrees (in)compatibility. So what I'm really after is a definitive guide describing how the nice people behind Ubuntu Studio have implemented them so I can learn how to solve my problems . . . . (like which libraries do what and how they interact)

thanks and I'm sorry if I've over looked the obvious up-to-date documentation URL. :confused:

daveuu

---

### Post by cchhrriiss121212 on 2010-11-09
Maybe it would be easier if you explain what your audio issues are? (I saw your mixxx thread but I'm not a mixxx user)

The first thing to understand about linux OSs is that they are just a collection of packages made by many different parties. The people who put together studio do not develop either Ubuntu or the packages contained within. This is why getting pulse and jack to work together is so problematic.

To sum up audio:
ALSA is the base of the audio chain, pulse and jack are both severs that run "on top" of ALSA. Studio is built on regular Ubuntu which uses pulse. Studio relies on jack for audio work which requires pulse to be either suspended upon startup or integrated into jack. I find that pulse adds nothing helpful so I do not use it on my system.

---

### Post by JC Cheloven on 2010-11-09
I'd say that finding out how libraries interact is overkilling, regarding solving a problem of an average, even advanced, user. It would be too close to grab the source code to draw your own conclusions. A task for devels, I think. Perhaps being more specific about your problem would be more practical?

> **cchhrriiss121212 said:**
> I find that pulse adds nothing helpful so I do not use it on my system.
+1
ATM the nice functionality pulse offers is ok for a general purpose desktop, but may become "a stick in the wheel" for a dedicated audio computer.

---

### Post by daveuu on 2010-11-11
Thanks for getting back to me.

Specifically, Mixxx failed to connect to any sound 'sink' (pulse, ASLA, oss etc) which I guess could be a Mixxx specific problem but it is included in the Ubuntu Studio Distribution. Sometimes it apparently connected but had all sorts of graphical failures like failing to render waveforms and freezing.

I had a wet dream of playing my Yamaha WX5 though a good software physical modelling synthesiser that responded realistically to breath levels etc to get a nice tone then putting it through a decent guitar amp simulator and connecting my Waves Ground control pedal MIDI thing to fanny about with the sound a bit more while I jam away . . .

But then I realised my brand new Ubuntu Studio 10.10 64-bit OS couldn't handle VST instruments and that several included apps struggled to make a sound.

Believe me I have FOSS in my blood and I understand the failure of hardware vendors to supply drivers etc. I anticipate a simple world of ALSA and JACK but I have meddled with my libraries in desperation and have potentially made a mess: for ALSA and JACK with full MIDI and audio availability (I believe I have generic USB kernel supported sound cards [M-audio fasttrackpro]) in Ubuntu 10.10's world, which Pulse libraries do I need to remove?

thanks

---

### Post by cchhrriiss121212 on 2010-11-11
VSTs are a proprietary standard made with windows only systems in mind so they will never have a great level of support. However, many people report success when using Reaper through WINE as a VST host, according to one user all his VSTs are supported if they do not require a USB dongle or something.

And you do not need to remove pulse or anything else right now as it won't interfere when running jack. I mentioned it as an example of how to slim down the audio chain (but you can remove it if you like).

 > I have meddled with my libraries in desperation and have potentially made a messTo agree with JC above, please do not do this, your issues are not library related. 

Let's try to get jack set up correctly without running anything else:
In qjackctl you should type hw:Pro as the selected interface. I think you may also need to force 16bit and use 48kHz as a sample rate. See here:
[http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro](http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro)
Frames can be 256 for now and set periods to 3.

Press start then open up patchage and confirm that you see the audio connections (in blue boxes) and the midi connections (in green boxes). If you have that running OK then we can troubleshoot any programs you want to run.

---

