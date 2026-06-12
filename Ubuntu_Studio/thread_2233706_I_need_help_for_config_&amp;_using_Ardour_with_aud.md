---
title: "I need help for config &amp; using Ardour with audio please"
date: 2014-07-10
forum: Ubuntu Studio
---

### Post by david243 on 2014-07-10
Hi everybody, 
I'm new user and I was working on macintosh with logig audio.
I'm musician, not informatician, and it seams to be difficult to set the configuration in midi and audio.

I got en EDIROL UA-20 that seams to be recognize on the system.
```
cat /proc/asound/cards
0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdbef8000 irq 22
 1 [UA20           ]: USB-Audio - UA-20
                      EDIROL UA-20 at usb-0000:00:02.0-1, full speed
```
```
cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio

```
```
aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: NVidia [HDA NVidia], périphérique 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
carte 0: NVidia [HDA NVidia], périphérique 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: UA20 [UA-20], périphérique 0: USB Audio [USB Audio]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
```

When I try to test the audio input&output with Audacity it works like it :
(JackCtl is stopped) , I choose ALSA, output UA20 UsbAudio hw1 & input UA20 UsbAudio line0 hw1
Then I can play and record sounds incoming the UA20
Happy !

Now when I want to do the same with Ardour, I choose in the menu "Audio/midi setup"
System : Jack
Pilote : ALSA
Device : UA20
But there's no sound even if I start JackCtl
I can see the view-meters in Ardour but there's no sound coming out the UA20

Do I miss anything ?
Someone could help me ?

---

### Post by jejeman on 2014-07-10
Is everything connected?

---

### Post by brianmc on 2014-07-11
> **david243 said:**
> Hi everybody, 
I'm new user and I was working on macintosh with logig audio.
I'm musician, not informatician, and it seams to be difficult to set the configuration in midi and audio.

I got en EDIROL UA-20 that seams to be recognize on the system.
```
cat /proc/asound/cards
0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdbef8000 irq 22
 1 [UA20           ]: USB-Audio - UA-20
                      EDIROL UA-20 at usb-0000:00:02.0-1, full speed
```
```
cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio

```
```
aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: NVidia [HDA NVidia], périphérique 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
carte 0: NVidia [HDA NVidia], périphérique 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: UA20 [UA-20], périphérique 0: USB Audio [USB Audio]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
```

When I try to test the audio input&output with Audacity it works like it :
(JackCtl is stopped) , I choose ALSA, output UA20 UsbAudio hw1 & input UA20 UsbAudio line0 hw1
Then I can play and record sounds incoming the UA20
Happy !

Now when I want to do the same with Ardour, I choose in the menu "Audio/midi setup"
System : Jack
Pilote : ALSA
Device : UA20
But there's no sound even if I start JackCtl
I can see the view-meters in Ardour but there's no sound coming out the UA20

Do I miss anything ?
Someone could help me ?

You're probably missing making all the relevant connections. I'd recommend avoiding letting Ardour start up JACK for you; that limits what you can do.

So, configure JACK using QJackCTL - since this is a USB soundcard, you'll need to specify a value of 3 for Periods/Buffer. If you'r*e* wanting MIDI as-well, then select the ALSA Sequencer in QJackCTL. Once you get JACK started with QJackCTL, *and not throwing lots of XRuns*, start Patchage. This is your digital Patchbay, and you'll see all the available connections in there.

That's the point at which you start Ardour. Personally, I go through the more-detailed settings in there and uncheck all the options for automatic connections (I do have 300W RMS per-channel hooked up to an Edirol DA2496... A feedback loop upsets the neighbours streets away).

Coming from a Mac background, you might-well find KXStudio a little easier to get going. I find the session management and whatnot a little lacking in Ubuntu Studio - but I prefer its desktop to the KDE one in KXStudio and hack the pair into an unholy alliance.

---

