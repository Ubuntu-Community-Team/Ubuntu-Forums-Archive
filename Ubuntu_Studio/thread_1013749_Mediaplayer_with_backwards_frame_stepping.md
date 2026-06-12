---
title: "Mediaplayer with backwards frame stepping?"
date: 2008-12-17
forum: Ubuntu Studio
---

### Post by ragtag on 2008-12-17
Is there any media player for Linux that will do backwards frame stepping ONE frame at a time.  Mplayer can do forward frame stepping by pressing '.' but not backwards. I do animation, so this would be a very handy feature.

Any ideas?

---

### Post by rylleman on 2008-12-17
Unfortunately there is no media player for linux that allow backward stepping. I'm also an animator and believe me, I have looked for a player for this...

There is the [[COLOR="Blue"]Cineplay player[/COLOR]]("http://www.silversoft.com/cineplay") that seems to be able to provide this but it is yet very unstable and also only offering an windows installer...
Also judging from their forum/website there is not very much development going on.

I have Quicktime player (7.1.6) installed with wine and it works well with stepping and everything.

For stepping in movies I'd say Quicktime and wine is your best bet.
[[COLOR="Blue"]Here's[/COLOR]]("http://www.wine-reviews.net/applications/quicktime-716-on-linux-with-wine.html") a gude to get it working.

---

### Post by ragtag on 2008-12-17
Thanks for the suggestion. That's kind of what I though would be the answer. :)  I guess there are too few of us who need this feature.

I did discover today that Blender can do frame stepping (at least in a x264 mov file I tried). While it may be a bit of a roundabout way to go, as it's so much more than a simple media player, but at least it boots almost instantly. :)

---

### Post by drelyn86 on 2008-12-17
You might try VirtualDub under Wine.

---

### Post by rylleman on 2008-12-18
Theres Avidemux on linux instead of Virtualdub. That one works but it's not primarily a player. Also I've been importing files into Kdenlive and doing playback there, they have excellent movie playback.
I started a thread at the Kdenlive forum yesterday suggesting doing a standalone Kdenplayer. I was suggested to have a look at Inigo which is a command line player and what is used by Kdenlive. Haven't been able to test that out though...

---

### Post by ragtag on 2009-01-21
Found another one that might do the job [http://djv.sourceforge.net/](http://djv.sourceforge.net/)

Haven't tested it yet though, but it definately looks interesting for what I need.

---

### Post by rylleman on 2009-01-22
That player was amazing for playback, very accurate and responsive and with frame stepping!

However it didn't seem to handle audio at all, or did I miss something? If it doesn't that's a major drawback!

Also I had issues running it on my laptop, complained about some OpenGL issue and only displayed black...
After some quick googling I think that has something to do with the Nvidia card.

---

