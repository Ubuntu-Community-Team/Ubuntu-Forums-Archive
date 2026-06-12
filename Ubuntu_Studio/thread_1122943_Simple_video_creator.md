---
title: "Simple video creator"
date: 2009-04-11
forum: Ubuntu Studio
---

### Post by nbakewell on 2009-04-11
Hello all,

I'm in need of just a really simple video creator.  All I want to do is take a folder I have of about 30 pictures, build them into a video that displays each photo for like 3 seconds, and plays a mp3 in the background.  Maybe add an intro screen.  I've tried out one program (but now for the life of me can't remember what it's called [i'm not at my home computer], I think "kito" or something) but it didn't seem to fit my purposes, or just did too much.

Any recommendations?  Thanks!

---

### Post by cotcot on 2009-04-12
kdenlive

smile : (former manslide) See info (sorry in French) [[COLOR="Red"]here[/COLOR]]("http://www.smile.tuxfamily.org/?q=node/33"). Téléchargement is French for Download. Extract the download file and double click on the smile executable in it.
If you have 64 bit you need to recompile smile with ```
qmake-qt4 smile.pro
make
```

---

### Post by roblloyd on 2009-04-14
You can do all of this with [mencoder]("http://en.wikipedia.org/wiki/Mencoder") i think. It's a command line tool that does all things audio/visual.

I use it to make time lapse type movies. like [this]("http://wellithinkitscool.blogspot.com/2009/01/bored-on-bus.html"). 

Its pretty nifty, as long as you're comfortable in the command line.

hope you find a solution

---

### Post by babounours on 2009-04-14
I would say ffmpeg:
ffmpeg -r 0.3 -b 400000 -i Picture-0%3d.jpg -i sound.mp3 Movie-output.avi

---

### Post by mrebanza on 2010-06-17
ffMEG worked great . . . extremely FAST . . . except now when I upload to Youtube they cut it off at 3 secs WTF!!!!!:confused:

---

