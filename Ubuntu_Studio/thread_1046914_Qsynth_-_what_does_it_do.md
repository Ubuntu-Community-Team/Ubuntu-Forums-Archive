---
title: "Qsynth - what does it do?"
date: 2009-01-21
forum: Ubuntu Studio
---

### Post by Hooya on 2009-01-21
I'm trying to get my machine set up to accept MIDI messages from a keyboard, essentially turning the computer into the sound producing device of a MIDI input.

I though Qsynth would be the program to use for that...  But I can't seem to get it to do anything.  The documentation says it plays MIDI files, so I"m trying to do that just to make sure it's working right.  I have a file that plays just fine in timidity, audio is great.  I try to open the file with qsynth and while the messages window says "playing nameoffile.mid" nothing is actually happening.  I just don't know what the program is doing.  There's no file open dialog, no play button, so I don't know exactly how you'd play a MIDI file with it.

I have managed to connect the Virtual Keyboard to QSynth in such a way that the little light on qsynth lights up when I hit a key on the keyboard, but still no sound.  I have loaded a soundfont. The Virtual keyboard will play through timidity if I connect them.

If qsynth isn't the program I want (To play the sounds from the MIDI messages of an external device) what program do I actually want to use?

---

### Post by eric71 on 2009-01-22
Qsynth is a soundfont player (via fluidsynth). You need to go into the Qsynth setup and load a soundfont, for instance one from here:

[http://www.personalcopy.com/linuxfiles.htm](http://www.personalcopy.com/linuxfiles.htm)

---

### Post by Hooya on 2009-01-22
I have loaded a soundfont.  I'll try a different one, but I don't think that's the problem.

---

### Post by Stochastic on 2009-01-22
> **Hooya said:**
> I have managed to connect the Virtual Keyboard to QSynth in such a way that the little light on qsynth lights up when I hit a key on the keyboard, but still no sound.  I have loaded a soundfont. The Virtual keyboard will play through timidity if I connect them.

Have you connected the audio output of qsynth into the soundcard outs in qjackctl or patchage?

Qsythn is exactly the program you want, but there are other similar programs too.

---

### Post by Hooya on 2009-01-22
I've tried various combinations of sending Qsynth to the system sounds.  Still nothing.

Strange thing, I can't seem to use a different soundfont than the one I first loaded.  I can change the sound of each channel but not to a different soundfont...

Edit: figured out that it's the lowest soundfont on the list that's loaded, not the first...  Go figure.

One more bit of info.  I'm not running the Real Time Kernel, but the Gain setting in qsynth under Setup > Settings is saying "yes" to real time, nothing else does.  Could this be my problem?

---

### Post by Hooya on 2009-01-22
Here are some screenshots of my configurations, if this helps anyone figure out what's going on.  The connections are what I think I need to have, but I get no sound.

Final Edit:  I finally got it to work.  My issue was in my Jack configuration.  It wasn't sending any viable audio to my device.  I enabled Real Time even though I'm not using the linux-rt kernel and went over the rest of my settings and now I have sound through Qsynth (as well as other Jack applications which didn't work before).

---

### Post by markbuntu on 2009-01-23
You should give patchage a try. It is by far the easiest way to see and set up connections, just point and click.

---

