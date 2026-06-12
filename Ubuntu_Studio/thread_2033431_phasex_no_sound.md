---
title: "phasex no sound"
date: 2012-07-26
forum: Ubuntu Studio
---

### Post by Chiel92 on 2012-07-26
Hi,

I get no sound out of phasex. I tried 2 following configurations in patchage.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=221828&d=1343298298[/IMG]



[IMG]http://ubuntuforums.org/attachment.php?attachmentid=221829&d=1343297604[/IMG]



Both of them produce no sound. Do I overlook something?
This configuration however, using aeolus only, produces proper sound:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=221827&d=1343298284[/IMG]

I use ubuntu studio 12.04. Thanks in advance for any help!

Regards

---

### Post by CrocoDuck on 2012-07-26
Hi. Try to connect a virtual keyboard to phasex's green input in order to check phasex's synthesis. Some phasex preset actually need some parameter adjustment before to sound properly. Check with a lot of presets (and/or by playng around with parameters). Make sure to have properly understood what phasex's audio inputs actually are: "*Up to two JACK input channels (as mono, dual mono, or stereo) may     be used as frequency sources for both oscillators and LFOs.  An     input envelope follower and input boost allow for sources like     guitar or vocals to be processed with ease.*" : [http://disabled.github.com/phasex-dev/features.html](http://disabled.github.com/phasex-dev/features.html)

---

### Post by primatic51 on 2012-10-29
With the old official Phasex site down, there seems to be little documentation for getting some of the features to work. Like, I understand what the audio inputs are, but could someone explain practically how to implement them in the program? How would I give myself voice effects? I have a microphone and a midi keyboard.

---

### Post by CrocoDuck on 2012-10-30
Experimenting with Phasex I found that you can use the audio input as a source for all the oscillators (as written in the guide). Is like using a synthetiser (of course, as Phasex is a synthetiser), but the wave forms for the oscillators are given by the inputs. To hear sound you have to play notes while "putting signals" into the Phasex inputs. So have a try by:

Connecting the mic to the soundcard and the midi controller to the computer, then:

Start Jack and Phasex

Go in Audio tab into connections and Connect the System Capture to Phasex's audio input

Go in the ALSA tab and Connect the midi controller to the Phasex input

Configure the Phasex oscillators you want in order to use input as source for them

Now try to sing and play the keyboard togheter.

---

### Post by sgx on 2012-10-30
> **Chiel92 said:**
> Hi,

I get no sound out of phasex. 
phasex can be fussy, I would make sure the default
patchbankstart text file is 924 bytes, and that everything
that exists in /usr/share/phasex, is also in
/home/username/.phasex

By default, no sound is loaded, so one must be selected.
I would start phasex before any other instruments.

Try using qjackctl for connections, and try jackd midi:
Install a2jmidid and use command

a2jmidid -j default, and use those connections for phasex.
Cheers

---

