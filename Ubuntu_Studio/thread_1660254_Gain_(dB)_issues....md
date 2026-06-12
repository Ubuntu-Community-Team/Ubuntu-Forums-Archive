---
title: "Gain (dB) issues..."
date: 2011-01-05
forum: Ubuntu Studio
---

### Post by mango42 on 2011-01-05
Hi again from the silly questions department.

Recently I have been trying to get **Audacity** to 'play nice' with Jackd (0.118.0) without much success. What I was looking for was a *really slimline* applet to do the exact opposite to that excellent program 'Timemachine' - in other words, feed a .flac, .ogg, .wav or .mp3 file into resource-hungry programs like JAMin without the overhead of programs like Ardour or Qtractor.

So I tried **Audacious** (both versions)  but hit a snag with gain, as its output only seems to be about half that coming out of Qtractor - hmm - probably user error as it could also be some issue with me trying to run Pulse under Jack - eg: in QJackCtl options:- ```
a2jmidid & pacmd load-module module-jack-source channels=2; pacmd load-module module-jack-sink channels=2;
```

:confused::confused::confused:

I'm sorry if my query comes under the 'How long is a piece of string?' variety but it would be so very nice to hear that someone has Audacity running consistently & smoothly under Jack...

Why is this so hard? 'arder than Ardour (which refuses to fit in my 1024x768 screen so I don't use it), even...

---

### Post by cchhrriiss121212 on 2011-01-05
I think Audacity is problematic with jack because it uses portaudio. But from the sounds of it, you don't need it in this situation.
Some small jack aware players to try out:
VLC
alsaplayer
aqualung

---

### Post by AutoStatic on 2011-01-05
+1 for aqualung, one of the best JACK-aware music players. And the Audacity team should really consider offering native JACK support, this PortAudio stuff just doesn't work in a stable manner.

---

### Post by Pablo_F on 2011-01-05
> Ardour (which refuses to fit in my 1024x768 screen so I don't use it)

Hi Mango! This can be solved! I bet ardour can fit in your screen! I hope so.

First of all, you can drag the window with the mouse by pressing [Alt] key at the same time. This is not the solution yet but it comes handy in any window that does not fit in the screen. 

Now, in the ardour menu:

Window -> Preferences -> Misc -> Font scaling

Put eighty-something, instead of the default one hundred or so. Maximize / Minimize, or restart ardour and you will see.

Jamin can be inserted in ardour (some use it as an insert in master post-fader so you can hear the audio processed. Don't forget to disconnect the master outputs from the system: playbacks if you do this).

+1 for aqualung. mplayer is a very good option too. It has fantastic jack support (better than vlc here). You have to jackify it. Google for "multimedia players through jack"

Cheers, Pablo

---

### Post by mango42 on 2011-01-06
Hey, many thanks for all the useful responses from you stalwarts ;-)

I'll give [Aqualung]("http://archive.ubuntu.com/ubuntu/pool/universe/a/aqualung/aqualung_0.9~beta11-0ubuntu1_i386.deb") a try (Jethro Tull fans, are they?) and pray that its' gain settings agree with QTractors ;-)

Next time I can get Soundcloud upload to work, there will be a new track to bend your ears with.

---

