---
title: "Audio players performance comparison"
date: 2009-08-14
forum: The Cafe
---

### Post by Athropos on 2009-08-14
Hi all,

Here is an interesting (IMO) comparison between a few audio players:

[http://decibel.silent-blade.org/index.php?n=Main.Benchmark](http://decibel.silent-blade.org/index.php?n=Main.Benchmark)

As a programmer, I often hear that scripting languages like Python are not efficient and should always be avoided. Well, from what I can see here, an audio player written in Python can beat Rhythmbox, which is written in C (they both use the GStreamer back end).

---

### Post by Bachstelze on 2009-08-14
> **Athropos said:**
> 
As a programmer, I often hear that scripting languages like Python are not efficient and should always be avoided. Well, from what I can see here, an audio player written in Python can beat Rhythmbox, which is written in C (they both use the GStreamer back end).

This only proves that a poorly written C program can be more inefficient than a Python program. ;)

---

### Post by harry2006 on 2009-08-14
both are good in their own world! 
and i guess python itself is written in C, right?

---

### Post by Bachstelze on 2009-08-14
> **harry2006 said:**
> both are good in their own world! 
and i guess python itself is written in C, right?

Yes, which is exactly why it's *theoretically* slower than C itself. But of course, many other factors come into ply.

---

### Post by Trail on 2009-08-14
> 
Amarok is the clear winner on CPU usage during playback. It uses Xine, so it looks like there is room for improvement in GStreamer. 


Hmm interesting. Even though I use the Mplayer backend instead of Xine.

---

### Post by konqui on 2009-08-14
I prefer Amarok!

---

### Post by mrgnash on 2009-08-14
Cmus = 1.0% CPU and 1.9% RAM usage on an IBM Netvista (P4 2.66ghz, 512MB RAM). I think we have a winner :P

---

### Post by RiceMonster on 2009-08-14
> **mrgnash said:**
> Cmus = 1.0% CPU and 1.9% RAM usage on an IBM Netvista (P4 2.66ghz, 512MB RAM). I think we have a winner :P

We'll have to see how mpd compares to that :D. Unfortunatly I can't test it right now as I'm not on my home computer.

---

### Post by DMcA on 2009-08-14
> **RiceMonster said:**
> We'll have to see how mpd compares to that :D. Unfortunatly I can't test it right now as I'm not on my home computer.

Just what I was thinking. I've never tested it but mpd seems a lot less efficient that it should be given it's purpose. That said, it's probably much better than any of the others. I'd also be interested in looking at xmms2

---

### Post by Athropos on 2009-08-14
> **HymnToLife said:**
> This only proves that a poorly written C program can be more inefficient than a Python program. ;)

That's right, but then you're implying that Rhythmbox is poorly written? :)

---

### Post by harry2006 on 2009-08-14
i like command line audio/mp3 players like mpg123/mocp etc....they consume very less memory...
anyone out here to second my choice of command line players???

---

### Post by bear24rw on 2009-08-14
> **harry2006 said:**
> 
anyone out here to second my choice of command line players???

depends on the situation, i do cli and gui 50 50

---

### Post by blackmail on 2009-08-14
it is normal that players whitout a GUI consume less, but it is not an issue, i know that i am missing the topic, but the fact is that i have a friend who has a very slow system, and he decided to use programs with no interface, and i am considering that also, even tough i have a fairly good pc. as i am considering it is also more easy to automate a process with those little marvels, talking here about conky, rtorrent, or ctorrent, and other goodies.
NOTE: yes i know conky is used mostly as a performance indicating sidebar, but it is controlled through script files ... in terminal

---

### Post by th3james on 2009-08-14
Is it just me or is audio player performance a bit irrelevant now? Most peoples machines are more than fast enough to handle any of these programs, for me it comes down to which program most effectively handles my music library in terms of interface, and for that it's Exaile or Amarok for me.
That said, I have developed a bit of a soft spot for Songbird and its plugins recently...

---

### Post by kingbilly on 2009-08-14
My favorite music player does not handle my large collection of music very well.  

Listen (Stable)

I have tried other players but a few things keep me going back to Listen.

I used exaile for a while, but it doesn't let me duplicate a song in a play cue (sometimes I know i want to hear a song a few times, like when i'm playing along on my piano)

Then I got banshee, which I really liked, but I can't drag files from dolphin right into the player.  I also didn't like the filesystem-different-from-library thing.

sorry to get off topic

Amarok 2 is great with a huge collection.
I think i tried the latest listen on another partition, but it became incompatible with a python-musicbrainz update :(

---

### Post by Athropos on 2009-08-15
> **th3james said:**
> Is it just me or is audio player performance a bit irrelevant now?

Well, it depends. Songbird needs around 33% of a 2.16 GHz CPU to play a track while Amarok needs only around 8%. Since for me playing music is a background task, I don't find it irrelevant...

---

