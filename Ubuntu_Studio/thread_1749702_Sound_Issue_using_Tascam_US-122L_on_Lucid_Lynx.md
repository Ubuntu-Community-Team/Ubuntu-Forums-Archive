---
title: "Sound Issue using Tascam US-122L on Lucid Lynx"
date: 2011-05-04
forum: Ubuntu Studio
---

### Post by jmjoy on 2011-05-04
Greetings

I am a relatively new user to Linux. I started using it on and off since last October.

I have found several helpful forum threads on my issue from google  searches, but I have reached the point where I can't find anyone with  the specific problem I am having.

Basically, I have a midi keyboard, microphone and speakers connected to  my Tascam US-122L which is hooked up to my laptop via USB. I am able to  open up Rosegarden. I imported a midi file of a Zelda song to test out  my sound. After some fiddling around (outlined below), I have made some  progress. With the JACK sound server started, I can hear the midi sounds  coming from my laptop speakers. I can also record and play midi to  Rosegarden using my keyboard. When I record an audio segment and play it  back, the midi tracks play through my laptop speakers while the audio  track plays through my Tascam-connected speakers.

If I try changing the connections in qjackctl to have the midi data  output to the Tascam device instead of my internal sound card, I hear  nothing from my keyboard.

The final issue I have is that my Tascam device doesn't appear in  pavucontrol or the sound preferences so I can't use my external speakers  at all right now through my Tascam audio/midi interface.

I followed step 3 of [http://wiki.briata.org/doku.php](http://wiki.briata.org/doku.php) to get the .asoundrc file. After some failures with JACK, I also installed a realtime-enabled kernal (2.6.31-11-rt)

The Tascam device seems to be connected because the command **cat /proc/asound/modules** yields

0 snd_intel8x0
1 snd_usb_us122l

and **cat /proc/asound/cards** yields

0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 21
1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/004)

What I want to end up with is the ability to play all audio from my Tascam speakers, and to be able to have midi data from Rosegarden output to my midi keyboard (which is connected to the Tascam US-122L interface). I know that my hardware is capable of this because I have been doing it with Cubase LE4 as well as Ableton Live on my XP operating system for a couple years.

Any help would be greatly appreciated!

---

### Post by Pablo_F on 2011-05-05
Hi,

It seems that Jack is using the Tascam, so you have it right.

Note that both sound preferences and pavucontrol are front-ends for pulseaudio, the default audio server in ubuntu. pulseaudio is not good for music creators, because is not designed with that purpose in mind and almost all music-oriented apps are not pulseaudio-aware, but jack-aware. 
What is more, when you have jack up and running, the configuration in the sound preferences is completely irrelevant. Maybe there is a way that you can tell pulseaudio that your tascam exists, but this is not what you are looking for, at least not now. 


As for the MIDI side, note that Rosegarden midi sequencer does not produce sounds by itself, you need to use either a external synth or a synth plugin.

Now it seems that you are using a non-jack-aware external soft synth, probably timidity. Rosegarden sends midi data to timidity, which sends audio data to the default audio card (the onboard) which is not being used by jack. Take a look at Rosegarden, Studio, Manage Midi Devices.

So, if you lack a hardware synth, you need either a jack-aware external soft synth, such as qsynth with a soundfont loaded (access via "manage midi devices") or a synth plugin (dssi plugin) such as hexter or fluidsynth-dssi (access via midi track configuration, "no synth" button, then you choose the plugin).

EDIT:
I read it further sorry, your midi keyboard is a synth? Then connect the midi track to the tascam alsa midi port.

To make sure, show the contents of:

arecord -l && aplay -l

arecordmidi -l && aplaymidi -l 

Cheers, Pablo

---

### Post by jmjoy on 2011-05-05
Well, I have some interesting results.

**arecord -l && aplay -l**
**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**arecordmidi -l && aplaymidi -l**
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 20:0    TASCAM US-122L                   TASCAM US-122L MIDI 1
131:1    rosegarden                       sync out
131:2    rosegarden                       external controller
131:3    rosegarden                       out 1 - General MIDI Device
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 20:0    TASCAM US-122L                   TASCAM US-122L MIDI 1
128:0    TiMidity                         TiMidity port 0
128:1    TiMidity                         TiMidity port 1
128:2    TiMidity                         TiMidity port 2
128:3    TiMidity                         TiMidity port 3
131:0    rosegarden                       record in
131:2    rosegarden                       external controller

When I reroute the rosegarden midi output to go through tascam instead of timidity, I hear sounds but it isn't quite right. It seems to only play selectively. I have a song playing with five midi tracks. It sounds fine when output through timidity. However, through tascam to my keyboard, it only plays select notes from two of the tracks. It plays the same notes each time I play the song, but I can't see any reasoning to it. Would this be due to the sound bank on my keyboard?

Also, I notice that when I boot up my machine, a message appears saying **mount: mounting none on /dev failed: No such device**. This only happens when I boot up using the realtime enabled kernal; no message appears booting with a generic kernal. I had my tascam usb plugged in when this happened so perhaps that is the reason. Not exactly sure what that message means.

So, my studio setup is at least able to communicate (somewhat) both ways with my keyboard using jack. What should I try to do so that pulseaudio can play audio through my speakers via usb when using programs like firefox and rhythmbox?

---

### Post by Pablo_F on 2011-05-05
> When I reroute the rosegarden midi output to go through tascam instead of timidity, I hear sounds but it isn't quite right. It seems to only play selectively. I have a song playing with five midi tracks. It sounds fine when output through timidity. However, through tascam to my keyboard, it only plays select notes from two of the tracks. It plays the same notes each time I play the song, but I can't see any reasoning to it. Would this be due to the sound bank on my keyboard?

It could be but I am not sure. Note that you can use different MIDI channels. As another proof of concept, try with a jack-aware external softsynth, such as qsynth.

> Also, I notice that when I boot up my machine, a message appears saying mount: mounting none on /dev failed: No such device. This only happens when I boot up using the realtime enabled kernal; no message appears booting with a generic kernal. I had my tascam usb plugged in when this happened so perhaps that is the reason. Not exactly sure what that message means.

There is a bug report in launchpad about this if you are curious. Anyway, don't worry. It is harmless. And nothing to do with the tascam. 

> What should I try to do so that pulseaudio can play audio through my speakers via usb when using programs like firefox and rhythmbox? 


Yes, you can. There is a package called pulseaudio-module-jack. You have to install it and then load the pulseaudio-module-sink, IIRC. I do not use it but search the forums.

Alternatively, you can "jackify" most multimedia players, including rhymthbox, rather easily. Check [http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507](http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507)

Cheers! Pablo

---

### Post by jmjoy on 2011-05-05
Thanks Pablo!

Due to your help, I have things working sufficiently right now for what I wanted to do.

Admittedly, I was mostly just going through this stuff as a learning process. It is quite likely I won't even be doing any serious music production on this system anyways.

Thanks again!

---

