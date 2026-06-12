---
title: "AmSynth &amp; JACK - Very bad clicking problem"
date: 2008-10-17
forum: Ubuntu Studio
---

### Post by EcthelionGenesis on 2008-10-17
I installed amSynth recently, and found it rather good, aside from the problem of short clicks (caused, I think, by buffer overflow?) every half second or so. 

The error message recommended I install the JACK audio subsystem. So I did. I then got problems with amSynth not running (i.e. crashing before start), but fixed that with the information given [here]("http://ubuntuforums.org/archive/index.php/t-454067.html").

Now the amSynth interface loads, but the audio output is now even worse! Really, it's so bad that it sounds more like silence with a few short clicks of audio. What am I doing wrong?

Output from amsynth -d (thought it might help):

```
sam@Ubu-XPSM1330:~$ amsynth -d
amSynth 1.2.0
Copyright 2001-2006 Nick Dowell and others.
amSynth comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

*** CONFIGURATION:
MIDI:- driver:auto channel:1
AUDIO:- driver:jack sample rate:44100


*** INITIALISING AUDIO ENGINE...
loaded & initialised libjack.so :)
SSE2 detected
SSE2 detected
*** DONE :)


*** INITIALISING MIDI ENGINE...
<MidiInterface> Trying to open ALSA midi device...
<MidiInterface> opened ALSA midi device
*** DONE :)
```

Thanks in advance.

---

