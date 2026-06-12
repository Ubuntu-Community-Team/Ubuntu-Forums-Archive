---
title: "ADI 1988B line-in recording, not working!"
date: 2009-10-21
forum: Ubuntu Studio
---

### Post by artheus on 2009-10-21
Hey!

I bought a P5E64 WS Evolution Motherboard a while ago, and I'm really satisfied with it. The only thing I've stumbled upon now, as I am going to start recording some audio for a game I'm developing. Is that in Ubuntu, I can not Record anything from the Line-in.

Programs I've tested:

Audacity
Built in Audio Recorder
JACK + Ardour

None of those get any signal at all.. In the Mixer > Recording tab, I only get "IEC958 Capture", "Capture", "Capture 1" and "Capture 2".
Yes.. I've checked in the Preferences list..

I am able to hear playback and controlling the volume with Mixer > Playback Tab > Line-In Slider. But not able to record from it.

I really don't understand what might be the trouble..

I've tried all the different captures, unmuting them all, recording.. I know I've connected all the cables correctly, as I've checked it at least 20 times..

Please Help me!

//Artheus

---

### Post by AutoStatic on 2009-10-21
Hello Artheus, did you check all the sliders and switches with **alsamixer**?

---

### Post by artheus on 2009-10-21
It says:

```

     Card: HDA Intel
     Chip: Analog Devices 1988B

Muted [Playback] : Headphones, Front Mic, Front Mic Boost, Surround, Center, LFE, Side, Mic, Mic Boost, IEC958 Default PCM, Mono

Muted [Capture] : Front Mic Boost, Mic Boost

```

In Capture there are 

"IEC958 [dB gain=1.50, 1.50]"
"Capture [dB gain=1.50, 1.50]"
"Capture 1 [dB gain=1.50, 1.50]"
"Capture 2 [dB gain=12.00, 12.00]"
"Input Source [Front Mic]"
"Input Source 1 [Front Mic]"
"Input Source 2 [Front Mic]"
and the Mic boosts..

There is no Line-in, in the capture area. I can only see Front mic in, but I don't want to use the mic input.

Thanks,
Artheus

---

### Post by AutoStatic on 2009-10-21
And you can't switch sources in the Input Sorces fields of alsamixer? Up-Down selects another input.

---

### Post by artheus on 2009-10-21
Wow! Didn't know that! haha! I Feel stupid :P

Works perfectly now!

Thanks alot!

---

### Post by AutoStatic on 2009-10-22
You're welcome, glad I could help :)

---

