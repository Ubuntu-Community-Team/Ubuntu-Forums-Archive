---
title: "Help me please with sound device cannot hear sound from Digital Stereo (HDMI)"
date: 2010-10-11
forum: Ubuntu Studio
---

### Post by MasterRRR on 2010-10-11
Hello everybody,
sorry for my bad english 
I have the following problem with my sound on UBUNTU 10.04 LTS
1. I've installed the newest ALSA sound drivers
2. I tried to hear sound from Sound Preferences -> Profile: Digital Stereo (HDMI) and nothing is hearing there is only sound in WEB Browser Firefox, there are no any other sound in PulseAudio Volume Control equalizer shows movement as the sound should be but there is no sound.
3. The sound of computer works only via : Sound Preferences -> Profile -> Analog Stereo Duplex - there is both sound and mic ... ;( 

Please advise me what to do how can i use sound via other device.

Computer is Acer Aspire 7738G

Thanks to everyone who can help!

PS: What is this device Digital Stereo (HDMI) maybe i'm wrong or something else? Should i hear sound from it via PC Speakers on laptop or no ?

---

### Post by RaumTrug on 2010-10-11
dude, I bet the digital (hdmi) stuff is connected to some output of your graphics card, designed to be sent to some flat-panel lcd television device along with some graphics data. useful to watch videos from your computer on your big tv with sound. if you're unsure what "hdmi" or "digital output" are, why don't you just search the web for it, or even just look at wikipedia: [http://en.wikipedia.org/wiki/Hdmi](http://en.wikipedia.org/wiki/Hdmi)

so if you choose that option, sound won't be cast to any internal speakers or headphone output, the "analog ..." options are for that! just because it's "analog" and not "digital" doesn't mean it's worse, but just that there's an amplifier in the hardware. "digital" stuff is meant to be decoded somewhere else (behind the cable you connect to your computer), and will be amplified (i.e. converted to an analog signal that's audible) there.

so: if you can use your audio input/output with the "analog duplex" profile fine, everything is alright, no need to choose digital.

and...err...please ask questions like that not in the "studio" sub-forum, it's dedicated to things like music/video production with ubuntu, and specially the "ubuntu studio" distribution, questions regarding multimedia devices with a general setup of ubuntu go the the "multimedia & video" subforum!

---

