---
title: "Cant detect/ solve soundcard conflicts with JACK applications"
date: 2015-11-20
forum: Ubuntu Studio
---

### Post by konstantin11 on 2015-11-20
Dear community,

I just switched from Xubuntu to Ubuntu studio for I found that I use one maschine for recording only. Now I encounter problems I can't handle so I'm grateful for every hint.

Immediately after installation I had no sound output and input in the programms I used intuitively under Xubuntu (Rosegarden, Audacity, Musescore). Instead Audacity showed me like 40 different output and input devices to choose from (formerly 3 or so). I figured, that the only combination working is

ALSA + output:default + input: pulse: Rear Mic:0 + Stereo

Now I have at least sound-output and basic recording working. All the other programs including JACK-Control dont seem to offer a) this combination ob b) dont let me play sounds with any other thing I tried.

Thank You for your time and any possible hints on how to move on from this,


Konstantin

---

### Post by CrocoDuck on 2015-11-20
How many soundcards in your system? Give us the output of these commands:

```

aplay -l
arecord -l
cat /proc/asound/cards
cat /proc/asound/devices

```

---

### Post by konstantin11 on 2015-11-20
Hi!
[B]
aplay -l [/B]outputs 
```
**** Liste der Hardwaregeräte (PLAYBACK) ****
Karte 0: Intel [HDA] Intel, Gerät 0: ALC 889A Analog [ALC889A Analog]
    Sub-Geräte: 1/1
    Subgeräte #0: subdevice #0
Karte 0: Intel [HDA] Intel, Gerät 0: ALC 889A Digital [ALC889A Digital]
    Sub-Geräte: 1/1
    Subgeräte #0: subdevice #0
```
[B]
arecord -l [/B]outputs 
```
**** Liste der Hardwaregeräte (CAPTURE) ****
Karte 0: Intel [HDA] Intel, Gerät 0: ALC 889A Analog [ALC889A Analog]
    Sub-Geräte: 1/1
    Subgeräte #0: subdevice #0
Karte 0: Intel [HDA] Intel, Gerät 0: ALC 889A Digital [ALC889A Digital]
    Sub-Geräte: 1/1
    Subgeräte #0: subdevice #0
Karte 0: Intel [HDA] Intel, Gerät 0: ALC 889A Digital [ALC889A Digital]
    Sub-Geräte: 2/2
    Subgeräte #0: subdevice #0
    Subgeräte #1: subdevice #1
Karte 1: SAA7134 [SAA7134], Gerät 0: SAA7134 PCM [SAA7134 PCM]
    Sub-Geräte: 1/1
    Subgeräte #0: subdevice #0

```
**cat /proc/asound/cards **outputs 
```
0  [Intel     ]: HDA-Intel - HDA Intel
                 HDA Intel at 0xfa200000 irq 29
1  [SAA7134   ]: SAA7134 - SAA7134
                 saa7134[0] at 0xfa115000 irq 19
  
```

**cat /proc/asound/devices **outputs 
```
 1:        : sequencer
 2: [ 0]   : control
 3: [ 0- 0]: digital audio playback
 4: [ 0- 0]: digital audio capture
 5: [ 0- 1]: digital audio playback
 6: [ 0- 1]: digital audio capture
 7: [ 0- 2]: digital audio capture
 8: [ 0- 2]: hardware dependent
 9: [ 1]   : control
10: [ 1- 0]: digital audio capture
33:        : timer
  
```

I played around a little with other combinations and looked for ways but still all the applications depending on JACK dont want to record or play.

Thanks for any further answers!

---

### Post by CrocoDuck on 2015-11-21
I would try to use your Intel HDA full duplex. Open qjackctl and set hw:0 in the jack "Input Device" and "Output Device" fields. You should be able to see a matching description in the dropdown menus as well.

---

