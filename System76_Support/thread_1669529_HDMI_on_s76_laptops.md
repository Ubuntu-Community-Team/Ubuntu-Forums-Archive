---
title: "HDMI on s76 laptops"
date: 2011-01-17
forum: System76 Support
---

### Post by val67 on 2011-01-17
Hi,

can someone confirm if HDMI is working on s76 laptops?

thanks,

val.

---

### Post by isantop on 2011-01-18
HDMI output works great. We're having some issues with audio, but the video out works fine. We expect all of the issue with HDMI to be solved by 11.04

---

### Post by val67 on 2011-01-18
> **isantop said:**
> HDMI output works great. We're having some issues with audio, but the video out works fine. We expect all of the issue with HDMI to be solved by 11.04

Thanks.

Which laptops have working sound with HDMI?

---

### Post by isantop on 2011-01-18
We currently have HDMI audio on the Lemur and the Pangolin. We're working on the Gazelle and the Serval.

---

### Post by samalex on 2011-01-27
Since moving to 10.04 HDMI video works but audio doesn't.  I think that's a Linux problem in general though and not specific to S76 laptops.

---

### Post by val67 on 2011-01-27
> **samalex said:**
> Since moving to 10.04 HDMI video works but audio doesn't.  I think that's a Linux problem in general though and not specific to S76 laptops.

so according to isantop both audio&video works on Pangolin and Lemur, right?

---

### Post by isantop on 2011-01-27
That is correct, both work fine on both of those laptops.

---

### Post by Derath on 2011-01-28
Isantop: Regarding the sound for Pangolins, Is there a way to do it without PulseAudio? Due to Pulse causing major sound issues in Wine, I have completely dumped it, and running alsa only. I have successfully gotten KDE's sounds through the HDMI cable, but for some reason, any sound from Firefox plays through the laptop speakers rather than the HDMI out.

Any suggestions aside from installing pulse?

---

### Post by isantop on 2011-01-28
Unfortunately, no, I think PulseAudio would be the best bet.

What problems was it causing in Wine?

---

### Post by Derath on 2011-01-28
Well, the game client has an embedded voice chat feature, with Wine configured for Alsa (as the pulse settings winecfg provide no audio input or output whatsoever, the settings show that they are there, but no sound is processed), I would get three different but distinct and critical results.

First possible result: Microphone input provides a squealing, choppy sound instead of voice, and that's even with a headset/mic combo, so no feedback loops.

Second possible result: Other players' voices are no processed by the sound card. In this odd result, the server and client register that the player is using voice chat and speaking, but the sound is never reproduced in an output path.

Third possible result: Sounds in the game appear distorted and begin fading to nothing, then no sound at all is produced, even though there are in-game actions that produce sound effects.

Since these make the sound system completely unusable in terms of game-playability, I've removed pulse. I have tried Jack, but unsure exactly how to configure it, so I removed it. I am also completely unfamiliar with ESD, so haven't tried it either. More or less, it seems Alsa is the only one stable enough to produce expected results, even though it's only single input/output system.

---

### Post by Noah0504 on 2011-01-29
> **samalex said:**
> Since moving to 10.04 HDMI video works but audio doesn't.  I think that's a Linux problem in general though and not specific to S76 laptops.
Agreed!  Not a big deal to me as I don't use it very often, but with the video working great, a set up speakers or internal speakers aren't that much of a hassle to use.

---

### Post by compholio on 2011-01-31
> **Derath said:**
> ...
 I have successfully gotten KDE's sounds through the HDMI cable, but for some reason, any sound from Firefox plays through the laptop speakers rather than the HDMI out.

Any suggestions aside from installing pulse?

Try [changing the default ALSA audio device]("http://alsa.opensrc.org/FAQ026").

---

