---
title: "Intel HDA captures white noise even when the microphone is unplugged"
date: 2009-05-05
forum: Ubuntu Studio
---

### Post by maxalken on 2009-05-05
My notebook has an onboard HDA Intel chip, this is the info from 'lspci'
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

When I select "Front Mic" as input source, I can record sounds from the microphone, but the white noise is accompanied. The strange thing is when I unplug the microphone, I can still hear the white noise. It seems the white noise is from the internal circuit. Is there any way to make the white noise disappear or not so loud?

There are 5 devices to select in Volume Control:
[LIST]
[*]HDA Intel (Alsa Mixer)
[*]Realtek ALC268 (OSS Mixer)
[*]Playback: HDA Intel - ALC268 Analog (PulseAudio Mixer)
[*]Capture: Monitor of HDA Intel - ALC268 Analog (PulseAudio Mixer)
[*]Capture: HDA Intel - ALC268 Analog (PulseAudio Mixer)
[/LIST]

I only adjusted the volume of "Front Mic Boost", "Capture" and "Capture 1" in "HDA Intel (Alsa Mixer)". The higher volume, the louder white noise is played back. Are other devices related to this problem?

---

### Post by bluebook on 2009-07-11
I'm having the same problem. This just started happening so I'm not really sure what is going on. Anyone have any ideas?

---

### Post by igorzwx on 2009-07-11
You are unlucky.
It is not easy to make it work with OSS4 too.
But it seems that it is possible in some way.

Try to remove Pulse.
It may work with ALSA perhaps.

---

### Post by Kostas2010 on 2010-03-14
I have the same problem. Any news on this?

---

### Post by AutoStatic on 2010-03-15
The signal from the built-in mic or the mic itself probably suffer from interference from other components (harddrive, CPU, GPU, wifi etc.). Best way to get around this is to get yourself an external mic.

---

### Post by RaumTrug on 2010-03-15
this is just one guess of what the prob. might be and how I solved it years ago when I had similliar noise:

fire up an alsa mixer, and mute all capture and playback channels you're not using (i.e. cd, line, phone, modem or whatever is there in the mixer). if you're using mic, just leave master, pcm (i.e. front) playback and mic playback/capture on. maybe the mixer got reconfigured to playback/capture for example cd (even if cd is not plugged in on the mainboard), and that migh be delivering the noise if the level is high.

can be helpful to monitor the noise while you're fiddling with the mixer, to see what was causing it. of course this will only work when the driver exposes those controls, but my experience showed me that alsa drivers tend to expose irrelevant controls happily.

if that doesn't work, it might be hardware or driver fault, and then it's not easy to fix,  :(

---

### Post by ubunterooster on 2010-03-15
I always noticed that if any inputs are neither being used or muted, there will be noise, so I mute them unless currently using them.

---

### Post by Dimitree on 2010-03-15
I have the same problem, even with unplugged front mic it captures noise.

@AutoStatic i use external mic, the same setup had no problems under windows, and older Ubuntu versions, currently using Lucid.

I will try and play around with the settings guys, but i have a BIG BIG BIG hunch that the cause is Pulse audio (GOD BLESS YOU OH YOU WHO DECIDED TO PLAGUE THE WORLD WITH PULSE AUDIO).

Anyway i'll come back to you if something comes up.
Ofc first will try to find what might be causing this and what settings affect it.

Anyway catch you later .___.

(IMMATURE SOUND SYSTEM FOR EVERYBODY YEY!)

Oh btw, are you all using the 
options snd_hda_intel model=3stack-6ch
switch in asla base config ?

---

### Post by Dimitree on 2010-03-16
Well changing options in Asla base doesn't do anything, removing any customizations didn't change anything also.
Amazingly my Webcam has better sound then in windows and no white noise, but white noise on the front mic remains.
Changing options with alsamixer = nothing.
Changing options with pulseaudio = nothing.

I found better settings for my ALC888 thou :) huhu
options snd_hda_intel model=3stack-6ch-dig

Anyway it seams that any changes in Alsa don't do anything.
Tried with the default asla configuration and as soon as i selected the Mic it had White Noise attached to it ...

Now if someone can point me to how to remove pukeaudio I'll be very happy to try that option for you guys lol.

---

### Post by leftoflexo on 2010-04-02
when using pulse i always had the noise on my similar intel soundcard, when using jack with alsa there is much much less.

---

