---
title: "Open source questions"
date: 2007-01-25
forum: The Cafe
---

### Post by helloworld86 on 2007-01-25
hi guys, i'm doing a project on open source and was wondering what your opinions are!

my first question is, which is the better audio codec to use? i.e. MP3 or OGG etc...
Games engines: any experience with any? if so which do you think are good/bad etc...

---

### Post by Brunellus on 2007-01-25
The answer is:  it depends.

Ogg vorbis is a free format;  you can use it without worrying about any adverse legal consequences.  It also yields higher quality in smaller filesizes, albeit at the cost of being more processor-intensive to decode.

MP3 is non-free, but "standard".

---

### Post by helloworld86 on 2007-01-25
ok, thank you

---

### Post by IYY on 2007-01-25
> my first question is, which is the better audio codec to use? i.e. MP3 or OGG etc...

They are approximately the same in quality and compression. MP3 is more popular, whereas OGG is more free. I'd say that if your engine supports OGG, you should use it. If it's just music for your iPod or something like that, MP3 is a good choice. Conversion between the formats is easy anyway.

> Games engines: any experience with any? if so which do you think are good/bad etc...


Depends on what type of game it is. I've tried the *Irrlicht Engine* for 3D games, and while I didn't actually make anything complex in it, I've looked over the examples and it seems to work very fast, and be fairly simple to code in if you know C. Plus, it's cross platform.

For 2D games, you should use SDL for the graphics.

---

### Post by helloworld86 on 2007-01-31
I have one more question, are the games engines stored on the games (i.e. disks)? or on the games console?
thanks for the replies so far

---

### Post by Brunellus on 2007-01-31
> **helloworld86 said:**
> I have one more question, are the games engines stored on the games (i.e. disks)? or on the games console?
thanks for the replies so far
On disk, with the rest of the program.

---

### Post by az on 2007-01-31
> **helloworld86 said:**
> hi guys, i'm doing a project on open source and was wondering what your opinions are!

my first question is, which is the better audio codec to use? i.e. MP3 or OGG etc...
Games engines: any experience with any? if so which do you think are good/bad etc...

Many people say that ogg gives you better quality for the same file size.  Ogg is free to distribute, whereas, if you were thinking about selling a game, you would have to pay a royalty if you chose mp3 as the format you use to encode/decode your music.

It's interesting that HALO II, a product of Microsoft, uses ogg to compress their audio.  They picked a free format over their own wma encoding.  Perhaps it would have incurred tax expenses or something.

---

### Post by freebeer on 2007-01-31
> **azz said:**
> 
It's interesting that HALO II, a product of Microsoft, uses ogg to compress their audio.  They picked a free format over their own wma encoding. 

Microsoft also used ogg in their game Allegiance (perhaps others?).  I'm told by the devs* that the sound files are read in, then decomressed as .wav files for use in game.

*by "devs" I mean the current Allegiance game developers.  When Microsoft ceased support for the game, they released the source code! (yep, Microsoft isn't always evil ;)  ) The game continues on in the hands of volunteer people.  Sadly, the game cannot be currently played on Linux, though.  :(

---

