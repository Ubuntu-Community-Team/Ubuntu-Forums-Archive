---
title: "Amateur theatre software sound desk"
date: 2010-08-13
forum: Ubuntu Studio
---

### Post by AlanQ on 2010-08-13
I'm a member of an amateur theatre group.
Our next play will involve many sound effects, several of which will have to play simultaneously. So this time two Sony mini-disc players won't be enough :)

I'm looking for software that will do this.
Ideally I'd like to be able to adjust the volume of individual tracks as they play.

I found a thread on this here
[http://ubuntuforums.org/showthread.php?t=1353257](http://ubuntuforums.org/showthread.php?t=1353257)
but it seemed to reach a dead-end.

It would be pretty galling to have to use Windows software ([http://www.audiovisualdevices.com.au/software/multiplay/multiplay.php](http://www.audiovisualdevices.com.au/software/multiplay/multiplay.php) ?)

I have a copy of Ubuntu Studio 10.04 inside Virtualbox to play with.
I'm completely new to audio software but very willing to learn.

Any suggestions gratefully received.
Thanks
Alan
(Very happy Ubuntu desktop user: started with 6.10, now using 10.04)

---

### Post by AutoStatic on 2010-08-14
Hello AlanQ, this may sound weird but I think Hydrogen (as of version 0.9.5 beta2) might suit your needs. Hydrogen enables you to load in different tracks/samples/songs and cue/play/stop them via MIDI control messages.

---

### Post by AlanQ on 2010-08-14
Thanks, Auto.
I'll have a play...
Must it be 0.9.5 beta2 ? The current stable on Studio Lucid (10.04) is 0.9.4-1 .

---

### Post by Jose Catre-Vandis on 2010-08-14
Use audacity to combine them to one sound file?

Or use audacity to play them back, having loaded them up and "aligned" the sounds?

Or try programmatically - e.g.
```
aplay /usr/share/sounds/alsa/Front_Center.wav & aplay /usr/share/sounds/alsa/Front_Left.wav
``` plays these two sounds simultaneously!

You can use && to play one after the other. You should be able to script to get more control if needed

---

### Post by AutoStatic on 2010-08-14
> **AlanQ said:**
> Must it be 0.9.5 beta2 ? The current stable on Studio Lucid (10.04) is 0.9.4-1 .Yes, because older versions do not allow you to cue anything because of the lack of the Stacked Pattern Mode and the playlist functionality that were only introduced with the 0.9.5 branch.

---

### Post by AlanQ on 2010-08-15
Thanks for the ideas, Jose.
It has crossed my mind that, given there's so much sound software in Ubuntu Studio, it should be possible to pipe one into another to achieve any result you need.
I can see myself writing a bunch of forking scripts :)

In the mean time, I shall go get Hydrogen 0.9.5...

Cheers
Alan

---

### Post by Jose Catre-Vandis on 2010-08-16
It's a good word "forking" :)  Relates nicely to scripts, especially when debugging :)

---

