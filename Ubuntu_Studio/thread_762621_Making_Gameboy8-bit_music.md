---
title: "Making Gameboy/8-bit music"
date: 2008-04-22
forum: Ubuntu Studio
---

### Post by Eisenwinter on 2008-04-22
I'm looking for a music creation program, which will allow me to create 8bit music, or, "Gameboy music".

If anyone can point me towards some, I'll greatly appreciate it.

---

### Post by robeast on 2008-04-22
I found this not too long ago:
[http://www.cs.cmu.edu/~tom7/midimml/](http://www.cs.cmu.edu/~tom7/midimml/)

I haven't tried it, but it might be what you are looking for. Looks like you could have some trouble compiling it in Linux. Check the documentation.

---

### Post by Eisenwinter on 2008-04-22
Thanks.
I can't figure out how to compile it, though.

Also, there is no direct archive file for Linux (targz, tarbz2, etc), only a ZIP for Windows users.

---

### Post by robeast on 2008-04-23
Yeah, I'm pretty sure this was written for windows (lame : P ), but some finagling could probably get it to compile. I wonder if anyone would be interested in making a program like this for linux. It seems that it simply converts ay midi file so it is playable by an NES emulator.

---

### Post by Stochastic on 2008-04-23
Isn't it entirely possible to take any music you make and resample it to be 8-bit using a wav editor?  Or am I missing something?

---

### Post by robeast on 2008-04-24
Yeah, you could simply find the sounds you want...or as Stochastic said, down-sample whatever you want to 8 bits :), but you know that's not what we're talking about. You can get some great "NES-esque" sounds with simple combinations of oscillators and simply use Rosegarden, Muse, etc. I think Seq24 would be appropriate for the job.

---

### Post by warbread on 2008-04-24
Could [this ]("http://www.delamancha.co.uk/basic.htm")work?

You could also check around freesound.org or hammersound.net for 8 bit samples and/or soundfonts.  Sound fonts would be easy; you could load them into something like Qsynth and then control it with Rosegarden.

---

### Post by Eisenwinter on 2008-04-24
> All plugins are Windows VST only.

:\

I downloaded the ZIP file for basic64, but it only included a dll and a readme.

---

### Post by warbread on 2008-04-24
You'll need a VST host to run it.  LMMS has one.  That's where my VST knowledge runs dry, though.

---

### Post by chill32 on 2010-07-15
are there any good music makers?

---

### Post by RaumTrug on 2010-07-15
what exactly do you mean by "8bit Gameboy Music"? I guess you just mean the sound/style of tunes like they're heard from legacy gaming platforms.

now to point you to something you can achieve similliar results from: take a look at "milkytracker" ([http://milkytracker.org]("http://milkytracker.org/")), it's also in the universe repositories of ubuntu.

it's a "tracker" kind of music software - basically a clone of the ms-dos fast-tracker-2 - and, beware, not the easiest to handle. it produces .xm files, and can also render to .wav. basically you load in some samples (can be very small loops, aka "chip"-samples, also 8bit - you can use any sample, loop or even draw the sample yourself with the mouse, which is gread for "chip"-type instruments), and then you have up to 32 channels to put notes in. the notes are arranged into patterns, and the patterns can be sequenced to a song (no chance to sound multiple patters at once, only one at a time). also there's no real dsp-effects in that program, when tracker guys talk about "effects" they mean effect commands that do stuff like vibrato to the note, volume/panning slides, pitch slides and not much more. for example, if you want to echoe a track, you need to copy it, lower every note's volume and shift it in time, taking another channel per echo.

it's actually possible to do higher quality stuff with milkytracker, but most people into it do classical 8bit "chiptunes", which normally sound a lot like 8bit "gameboy" type music. you can even emphasis the low-quality-chip effect by choosing an amiga-type resampler and/or a low sampling rate. there's also huge repositories of (partially really old) tunes in many formats (mt can load well things like .mod, .s3m, i.e. even old amiga stuff). to learn from how to do it. if you think "hey, 16bit 48k samples sound too good" then just don't use them, and your tune will sound like from a cheap, old chip :twisted:

have fun trackin' tunes! :D

---

### Post by theraje on 2010-07-17
Unless I'm mistaken, LMMS actually has a built-in Game Boy sound chip emulator (and also a Commodore 64 SID emulator for the win!). :)

---

### Post by GhostofJohnToad on 2010-07-17
You could try running famitracker in wine.

---

### Post by maghoxfr on 2010-07-22
Yeah, Milkytracker is the way to go. The LMMS plugin that makes 8-bit sounds, gameboy-like is pretty good but way simpler.

---

### Post by Bussiere on 2010-08-20
> **RaumTrug said:**
> what exactly do you mean by "8bit Gameboy Music"? I guess you just mean the sound/style of tunes like they're heard from legacy gaming platforms.

now to point you to something you can achieve similliar results from: take a look at "milkytracker" ([http://milkytracker.org]("http://milkytracker.org/")), it's also in the universe repositories of ubuntu.

have fun trackin' tunes! :D
That was what exactly i was searching for.

Thanks a lot

Bussiere

---

### Post by b_c on 2011-04-13
> **chill32 said:**
> are there any good music makers?

... take this is an occasion to post a link to [Gameboy Madness]("http://www.babychlor.ch.vu")  

hope it's not that bad at least  :-\"

---

