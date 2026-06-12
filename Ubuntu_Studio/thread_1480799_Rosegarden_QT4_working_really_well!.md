---
title: "Rosegarden QT4 working really well!"
date: 2010-05-11
forum: Ubuntu Studio
---

### Post by Reeman on 2010-05-11
I have compiled and have Rosegarden 10.04.2 (latest release) working really well. No crashes or freezes and extremely fast with the current .deb QT4 libs. It is on Mint but there were no real show stoppers in compilation and all of the secondary functions are working without issue. I have to give kudos to the whole Rosegarden crew for pulling off a wonderful release of what is essentially the most usable and complete notation/recording/midi program for the Linux platform! If I could rap my head around how to .deb package the thing I would gladly send it to others who want the best available current compositional software.

I guess if I set /etc/security/limits.conf to allow rtprio for group audio programs I might have something really great as far as audio and midi recording and playback with low latency ...but even without:guitar: rtprio Rosegarden is not causing midi lag. So the latest release of Rosegarden is really something that should be better supported and know in the Linux community! 

Eric

---

### Post by luctor on 2010-05-12
A good thing would be to contact Philip Johnsson.
He's got a great PPA for audio related programs. I think he would be happy to package the latest Rosegarden

[https://launchpad.net/~philip5](https://launchpad.net/~philip5)

---

### Post by thorgal on 2010-05-12
> **Reeman said:**
> I have compiled and have Rosegarden 10.04.2 (latest release) working really well. No crashes or freezes and extremely fast with the current .deb QT4 libs. It is on Mint but there were no real show stoppers in compilation and all of the secondary functions are working without issue. I have to give kudos to the whole Rosegarden crew for pulling off a wonderful release of what is essentially the most usable and complete notation/recording/midi program for the Linux platform! If I could rap my head around how to .deb package the thing I would gladly send it to others who want the best available current compositional software.

I guess if I set /etc/security/limits.conf to allow rtprio for group audio programs I might have something really great as far as audio and midi recording and playback with low latency ...but even without:guitar: rtprio Rosegarden is not causing midi lag. So the latest release of Rosegarden is really something that should be better supported and know in the Linux community! 

Eric

It still doesn't use the Jack MIDI API. If it keeps stickting to the ALSA MIDI API, that's fine but then they should provide audio via ALSA as well for completion.

This being said, it was quite a big overhaul!

---

### Post by Reeman on 2010-05-12
> **thorgal said:**
> It still doesn't use the Jack MIDI API. If it keeps stickting to the ALSA MIDI API, that's fine but then they should provide audio via ALSA as well for completion.

This being said, it was quite a big overhaul!

If you use fluidsynth then you can route your midi and separate audio through jack as you create it in Rosegarden. It would be really nice if they can get midi straight to jack but jack does not understand midi bank data and can only handle the processed audio from either a hardware or in the case of fluidsynth a software synth.

All that aside if Rosegarden does eventually dump jack audio it would require a very major rewrite of the core program to include very major sound processing capabilities. This would in turn require all of the current Linux audio devs to get together and set up a rtprio audio api for Linux..not a bad idea but almost pie in the sky ...for now. Heres hoping!  

To achieve anything approaching high definition 24/96 multi-track audio and simultaneous multi-track midi requires capabilities like those that are available only using the asio api ....and the software that will do it is not exactly cheap. I know one studio that pays over 10k Canadian per seat!](*,) And it ain't even Windows ware. He has 4 and 8 core macs. 

The other major problem with this pipe dream:-\" is that the biggest corporate supporters of Linux do so because it has become a kick### embedded OS. And they implement there own stuff to work with very specific low end hardware ..not exactly the type of hardware capable of multi-track audio production.

But putting all the negatives about Linux not having a chance at the high end audio studio market....Rosegarden is one giant step in the right direction!

---

### Post by thorgal on 2010-05-12
I kind of agree. Note that I did not suggest they dumped jack :lol: but they could add a direct ALSA audio engine for completion. Of course, by choosing the ALSA engine, one would lose a few capabilities that jack provides, but some ppl cannot get jack to work properly on their system and they might still want to use rosegarden without buying a new h/w. 

(I know this is no fair comparison with RG but look at an app like gnusound. Never used it myself but it provides different audio engines).

---

### Post by philip5 on 2010-05-13
> **luctor said:**
> A good thing would be to contact Philip Johnsson.
He's got a great PPA for audio related programs. I think he would be happy to package the latest Rosegarden

[https://launchpad.net/~philip5](https://launchpad.net/~philip5)

I happily just did so for Lucid... :)

---

### Post by hxcobd on 2010-05-13
Rosegarden 10.02 crashes like crazy for me on 10.04, driving me insane... Hopefully this new one is more stable!

---

### Post by philip5 on 2010-05-13
> **hxcobd said:**
> Rosegarden 10.02 crashes like crazy for me on 10.04, driving me insane... Hopefully this new one is more stable!

Keep us posted if the updated version in my PPA is more stable.

Have fun!

---

