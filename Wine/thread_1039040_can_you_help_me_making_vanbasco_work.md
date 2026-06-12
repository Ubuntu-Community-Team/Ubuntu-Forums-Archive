---
title: "can you help me making vanbasco work ?"
date: 2009-01-14
forum: Wine
---

### Post by giorsat on 2009-01-14
hi. i installed wine and vanbasco , the karaoke player (I always wondered why linux has not a decent karaoke player with pitch adjusting and text showing). Anyway, fact is that sound is missing and the program freezes

this is what I did
- installed wine and timidity
- installed vanbasco
- in winecfg i choose alsa then I choosed oss
- I started vanbasco with wine "C:\blahblah\vmidi.exe"
- then  I tried pasuspender -s pulseaudio -- wine "C\\blah blah\vmidi.exe"
but every time the sistem freezes and no sound at all . 
can you hel find a perfect setup?

---

### Post by pogay on 2009-02-26
I also work with midi, and vanbasco was my favorite MIDI-Player under Windows, it works also under Vista.  

As there is no KMID in the repos of Ubuntu 8.10 I tried to install vanbasco under wine. 

Everything seemed to be fine, but **when playing the track, it freezes**. 
The same on my Ubuntu 8.04 Installation, I tried a lot of sound configuration and different "windows". 
Sound works under wine, as QMP works perfectly. 
Wondering whether it's a midi specific problem.  

It seems to be possible to run Vanbasco under ubuntu8.04,  ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=2309](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2309))
So I'm still looking for a solution, as
KMID also seems to have bugs, the playlists are IMHO not functionable, otherwise you can change instruments, what would be enough for me.)

I tried rosegarden, which works nicely. 
But there is unfortunately no minimal-Player based on RG, as far as I know. 

Patrick

---

### Post by pogay on 2010-01-05
Hurra, fand ich die Lösung: [http://www.youtube.com/watch?v=sRQUQYlSUCI](http://www.youtube.com/watch?v=sRQUQYlSUCI)

im *Karaoke*-Textfenster:  rechte Maustaste, Einstellungen.

dann Tab midi:
1]Midi auf timidity stellen (statt midi-mapper) 
  bei mir waren keine Port-Nr, nur mehrere Timidity-Einträge.
2]und  "general midi" statt windows  unter Reset-Modus 

Es soundet!!!

bin immer noch auf der Suche nach einem guten Midi-karaoke-Player unter Linux.

Patrick  

engl:
Solution from youtube link above
*from Karakoke text window, kontext (right mouse), settings 
*midi 
*I put it form midi-mapper to timidity (I had no ports, but several "timidity" entries
*reset mode: general midi instead of windows 

for the solution above timidity has to be installed. 
(midi may play without timidity via gstreamer plugin)

Is there another midi-karaoke-player under Linux beside kmid? (which was not in 8.10)
kmid was not bad, but the playlists didn't seem to work.

---
www://wprj.net/tunes - some ABC notated SATB midi stuff for my chorus
midi, mp3, pdf sheets are generated on the server. :-)

---

