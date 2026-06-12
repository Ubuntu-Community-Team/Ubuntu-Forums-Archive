---
title: "Media server - what are the options?"
date: 2007-02-11
forum: The Cafe
---

### Post by epimer on 2007-02-11
First off, I'm not sure where this thread best belongs, so if mods feel it should be moved to networking or multimedia, please do.

The monitor for my desktop box died this morning (only a few months out of warranty, too...grr), and I'm far too broke to replace it right now, so I'm looking for opinions on what to do with the computer as it is. I have the desktop PC and my laptop, both of which run Edgy. My mp3s and various gubbins stay on my desktop PC, because it has 250 GB more storage than my laptop. So I want a good way to access all that musical goodness from my laptop.

Right now I have a Gnump3d server set up, which is useful for when I'm not on the LAN, and as a stop-gap for now. My primary complaint with it is that the streaming files messes up the song metadata, so isn't quite as good as having the files locally (and my Last.fm data!).

From reading around, it seems I have a couple of options. The first would be to mount the remote music directory on the desktop with ssh. That way, I could continue to use my favourite music player (Exaile!) and it would be almost the same as having the files stored locally. The second would be to install mpd on the desktop, and a client like pympd or gmpc on the laptop. Problem there being that I lose Exaile, which I'd rather not do.

So, does anyone have opinions on the pros and cons of these solutions? Handy resources? Or even suggestions that are much better than mine? Please share!

---

### Post by tbroderick on 2007-02-11
I think mpd is the best music player around. I would go with that.

---

### Post by qball on 2007-02-12
good choise :D

---

### Post by shining on 2007-02-12
Well, if you want to play the sound where the desktop is (ie it's in the correct place), then do it, no need to use the bandwidth for streaming ;)
And mpd is indeed just the perfect tool for that.

---

### Post by MetalMusicAddict on 2007-02-12
Mount your music folder as a network share. Better than a streaming server. Maybe I'm missing what your trying to do

---

### Post by epimer on 2007-02-12
MetalMusicAddict, no, you're not missing it - but I was overlooking the simplest possibility. It is indeed what I've done, and does just what I want. Good suggestion!

That can be step one in converting the thing to a decent server. I feel a reinstall coming on...

---

### Post by MetalMusicAddict on 2007-02-12
I run a headless desktop as a server myself. I run Xubuntu on it with VNC to control it. I have all my media (8 drives) on it as well as my printer. Everthings shared with Samba on a gigabit network.

Works great here. Lemmie know if you have questions.

---

