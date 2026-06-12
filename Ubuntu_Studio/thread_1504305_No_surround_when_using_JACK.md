---
title: "No surround when using JACK"
date: 2010-06-07
forum: Ubuntu Studio
---

### Post by GoofusGreen on 2010-06-07
I put Ubuntu Studio on this machine last week, and I'm having issues working out the sound. I'm running qjackctl but not start-pulseaudio-x11 on startup. The settings in qjackctl for startup and shutdown scripts are:

```
On Start: artsshell -q terminate; killall pulseaudio
After Start: pulseaudio -DnF ~/.pulse/pulsejack.pa
On Shutdown: killall pulseaudio
After Shutdown: killall jackd & pulseaudio --start
```

Where pulsejack.pa is the same as default.pa except with two additional lines:

```
### Run PulseAudio through JACK
load-module module-jack-source
load-module module-jack-sink
```

When I run this way, in System-Preferences-Sound, I see the JACK sink listed as stereo and I don't see my sound card (a C-Media 7.1 card). In qjackctl, Audio has "system" with only two playback channels. Also, in the PulseAudio manager, the jack-sink shows only two channels as well.

When I run without JACK, my sound card shows up just fine and I get surround sound without any issues.

I seem to remember that when I first installed Ubuntu Studio, qjackctl did list "system" as having 8 playback channels.

How can I get JACK (I think this is the problem) to recognize my sound card as having more than 2 channels?

---

### Post by thorgal on 2010-06-08
sounds like your problem is not jack but the pulseaudio jack modules which only show up in stereo mode. I never used PA so I don't know if this is something you can configure in the PA config file.

if you apply jack on your soundcard, regardless of PA, it will display all channels as system ports that the backend driver found. If your card is driven by ALSA, the ALSA driver notifies the jack ALSA backend about the h/w info. Jack only applies what it knows from the driver.

---

### Post by Pablo_F on 2010-06-08
> 
if you apply jack on your soundcard, regardless of PA, it will display all channels as system ports that the backend driver found. If your card is driven by ALSA, the ALSA driver notifies the jack ALSA backend about the h/w info. Jack only applies what it knows from the driver.

And alsa could see different "devices" in the same card, I would add.

Some commercial cards have different "devices", one for capture/front playback, another one for multichannel playback and maybe more, depending on the card and the alsa module. 

Pulseaudio is smart and resolves this well but jack is not prepared for this kind of commercial soundcards, so you might have to choose one "device" for capture and another one for playback in the jack setup, according to what "aplay -l" has to say. 

hw:0,0 means, card 0, device 0.

I think that you can make something in ~/.asoundrc to have two or more "devices" in a unique "virtual device".  

How this is solved with the pulse-jack module, I don't have a clue.

Cheers! Pablo

---

