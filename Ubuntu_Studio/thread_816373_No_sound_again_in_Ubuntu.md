---
title: "No sound again in Ubuntu"
date: 2008-06-02
forum: Ubuntu Studio
---

### Post by wavesound on 2008-06-02
Hi All
Seems sound is of no importance in Ubuntu anymore.
Just installed the hardy heron on a new HP machine with a realtek card.
I had sound on movie player on the digital input but no sound on youtube or any  flash players.

Changed to the normal sound inputs and now I get various errors from alsa can't connect, permission denied and such.

I have googled and seen many threads on this problem but no real solutions.
Are we happy to push Ubuntu/Linux with this problem to our windows friends?

Thing is it all worked on the older Ubuntu, why is now shipping as broken? :(

cheers
Bob

---

### Post by thorgal on 2008-06-02
hardy took the risk to use a new audio server called pulseaudio. But apparently, little to no regression testing was done to ensure that everything worked OOB ... quite a mistake to my mind.

PS: for your problem, firefox has a conf file in /etc/firefox (called firefoxrc IIRC). You can choose to use pulseaudio as the DSP wrapper but I don't remember which word to put in there (FIREFOX_DSP="padsp" I think but I don't really know, I don't use the same system myself).

---

### Post by wavesound on 2008-06-02
> **thorgal said:**
> hardy took the risk to use a new audio server called pulseaudio. But apparently, little to no regression testing was done to ensure that everything worked OOB ... quite a mistake to my mind.

PS: for your problem, firefox has a conf file in /etc/firefox (called firefoxrc IIRC). You can choose to use pulseaudio as the DSP wrapper but I don't remember which word to put in there (FIREFOX_DSP="padsp" I think but I don't really know, I don't use the same system myself).

HI Thanks for the quick reply.
I had seen some threads on the pulseaudio stuff being broken.
I'll check out the Firefox thing as well
Many thanks
Bob

---

### Post by nalmeth on 2008-06-02
I suppose your mileage may vary when it comes to pulseaudio - but its been great for me so far. 

Anyway, you will find better help for this problem in the Multimedia & Video section, as this section is for Multimedia Production rather than support for general sound issues.

---

### Post by wavesound on 2008-06-03
> **nalmeth said:**
> I suppose your mileage may vary when it comes to pulseaudio - but its been great for me so far. 

Anyway, you will find better help for this problem in the Multimedia & Video section, as this section is for Multimedia Production rather than support for general sound issues.

HI All
I found this thread on here:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Don't forget to turn up the front volume you get when you install pulseaudio it easy to follow and worked! :)

As I'm about to setup a digital recording studio here and I wanted the basics working,  as trying to sort problems with my RME card and 32 tracks can be a nightmare.

Cheers
Bob

---

