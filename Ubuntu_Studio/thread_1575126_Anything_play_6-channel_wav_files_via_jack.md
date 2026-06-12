---
title: "Anything play 6-channel wav files via jack?"
date: 2010-09-15
forum: Ubuntu Studio
---

### Post by davemar on 2010-09-15
I'm trying to get an Apogee Rosetta 800 (firewire 8-channel audio device) playing out 6-channel (5.1) audio, but struggling. I've got it recognised in jack, and jack is running with it set up with all 8 outputs turned on as far as I can tell. 

I'm aiming to play out 6-channel 16-bit wav file (linear PCM).

My first program to try was audacity, and that did actually play something out, but only through 2 channels. It seems incapable of 6-channel playback?

My next port of call was aplay, but after setting up an .asoundrc file with 8 channels specified through jack, all I kept getting was a "File format not available" error.

I also tried alsaplayer and could get playback using a 2-channel wav file through any two speakers I chose, but couldn't manage all 6 at the same time with the 6-channel file.

VLC didn't even know jack exists it seems.

So is there anything that can play 6-channel files with this setup?

---

### Post by AutoStatic on 2010-09-15
Try the vlc-plugin-jack package. I also think mplayer could do the job.

---

### Post by Pablo_F on 2010-09-15
[http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507](http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507)

[http://www.mplayerhq.hu/DOCS/HTML/en/advaudio-surround.html](http://www.mplayerhq.hu/DOCS/HTML/en/advaudio-surround.html)

Cheers! Pablo

---

### Post by davemar on 2010-09-17
I managed some success with mplayer, but the channel ordering is wrong. I see there is a -channel option with a rather cryptic set of numbers to reorder the channels. I'll see if I can things right with that.

Still no joy with vlc.

Still wish Audacity could do it though, as it is the most useful application for the sort of stuff I do.

---

### Post by cchhrriiss121212 on 2010-09-17
Ardour can handle 6 channel audio.

---

### Post by AutoStatic on 2010-09-17
Qtractor too, but not a 6 channel WAV file. I doubt if Ardour can do that also.

---

### Post by cchhrriiss121212 on 2010-09-17
> **AutoStatic said:**
> Qtractor too, but not a 6 channel WAV file. I doubt if Ardour can do that also.
Any reason why it wouldn't? 
I just gave both programs a test with a sample 5.1 wav file, Ardour loads the file and plays it back but plays each channel through every speaker.
Qtractor seemed to work fine, though I am only testing this with my stereo set up.

---

### Post by AutoStatic on 2010-09-18
> **cchhrriiss121212 said:**
> Any reason why it wouldn't? He he, it's just my ignorance. I've never played around with audio files with more than two channels, I'm a 2.0 guy ;) But when I think about it it should be perfectly feasible to load a track with more channels. And if you output it to a bus with the same number of channels you can route it to any speaker you want.

---

