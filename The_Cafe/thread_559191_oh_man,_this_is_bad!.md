---
title: "oh man, this is bad!"
date: 2007-09-24
forum: The Cafe
---

### Post by fuscia on 2007-09-24
so, for some odd reason, i decided to give mpd a shot. well, before the novelty wore off, i somehow got it working. now, i'm loving ncmpc, but i don't trust this mpd thing one bit (i haven't been this paranoid since the last time i reinstalled windows ME).

---

### Post by rsambuca on 2007-09-24
> **fuscia said:**
> so, for some odd reason, i decided to give mpd a shot. well, before the novelty wore off, i somehow got it working. now, i'm loving ncmpc, but i don't trust this mpd thing one bit (i haven't been this paranoid since the last time i reinstalled windows ME).

Huh?  [COLOR="Red"]M[/COLOR]ultiple [COLOR="Red"]P[/COLOR]ersonality [COLOR="Red"]D[/COLOR]isorder?

---

### Post by fuscia on 2007-09-24
> **rsambuca said:**
> Huh?  [COLOR="Red"]M[/COLOR]ultiple [COLOR="Red"]P[/COLOR]ersonality [COLOR="Red"]D[/COLOR]isorder?

holy poop! is that what i've installed???

---

### Post by ~LoKe on 2007-09-24
MPD is **beautiful**.  I almost cried when it stopped working for a couple weeks.

I suggest installing the "Sonata" front-end.

---

### Post by fuscia on 2007-09-24
> **~LoKe said:**
> MPD is **beautiful**.  I almost cried when it stopped working for a couple weeks.

I suggest installing the "Sonata" front-end.

i took about a five minute look at sonata - didn't like it.

---

### Post by Tux Aubrey on 2007-09-24
> Myeloproliferative disorders (MPDs) are a closely related group of hematological malignancies in which the bone marrow cells that produce the body's blood cells develop and function abnormally. The disorders are progressive blood cancers that can strike anyone at any age, and for which there is no known cure. The three main myeloproliferative disorders are Polycythemia Vera (PV), Essential Thrombocythemia (ET) and Chronic Idiopathic Myelofibrosis (MF). 

I think you are over-reacting, fuscia.  That doesn't sound anywhere near as bad as Windows ME.

---

### Post by fuscia on 2007-09-24
> **Tux Aubrey said:**
> I think you are over-reacting, fuscia.  That doesn't sound anywhere near as bad as Windows ME.

dude, you're on crack. ME is the very best thing microsoft ever produced. it was almost as if they said "screw security attempts, just go out and have fun." (which is what i did.)

---

### Post by FuturePilot on 2007-09-24
I have no clue what anyone is talking about. What is mpd?

---

### Post by fuscia on 2007-09-24
> **FuturePilot said:**
> I have no clue what anyone is talking about. What is mpd?

'music player daemon' (i think. i don't really know wtf it's called).

---

### Post by FuturePilot on 2007-09-24
Is it in the repos?

---

### Post by Frak on 2007-09-24
> **fuscia said:**
> 'music player daemon' (i think. i don't really know wtf it's called).
No, you got it :)

---

### Post by fuscia on 2007-09-24
> **FuturePilot said:**
> Is it in the repos?

yup. i also give my semi-stamped approval to ncmpc (which apparently has something to do with it) as well.

---

### Post by rsambuca on 2007-09-24
It only took me about 12 posts to figure out what you guys are talking about.

---

### Post by fuscia on 2007-09-24
> **rsambuca said:**
> It only took me about 12 posts to figure out what you guys are talking about.

that beats me.

---

### Post by FuturePilot on 2007-09-24
> **rsambuca said:**
> It only took me about 12 posts to figure out what you guys are talking about.

At least I wasn't the only one confused:lolflag:

---

### Post by sunexplodes on 2007-09-24
Man, I love the MPD/Sonata combo. 

I have a library of 4000+ songs, and my playlists and library load nearly instantly. It's fast as hell, resource-light, and feature-rich. What's not to love?

---

### Post by Tux Aubrey on 2007-09-25
Hurumph!  Fuscia recommends Windows ME (and, on another thread, Windows 95) - but _I'm_ the one supposedly on crack.:confused:

---

### Post by potrick on 2007-09-25
Not only that, but he compared MPD to ME. 

What the hell is going on?

---

### Post by 3rdalbum on 2007-09-25
I figured out how to set up MPD... but it took me a fair while. I love the idea of a very lightweight music player that doesn't even need a GUI program running in order to continue playback; but my music collection is spread across multiple partitions and MPD doesn't seem to be able to handle this even with symbolic links.

I'm sticking with Exaile.

---

### Post by mcduck on 2007-09-25
> **3rdalbum said:**
> I figured out how to set up MPD... but it took me a fair while. I love the idea of a very lightweight music player that doesn't even need a GUI program running in order to continue playback; but my music collection is spread across multiple partitions and MPD doesn't seem to be able to handle this even with symbolic links.

I'm sticking with Exaile.

It IS able to handle that, at least it works for me. Just symlink all your music directories into separate directories inside /var/lib/mpd/music (or whatever the default MPD music dir was).

Actually it even works if some of those directories are on removable drives, just don't update the library if those drives are not connected. I have about half of my music in three separate directories on a removable drive, and the rest inside my /home. No problem there.. :D

---

### Post by jethro10 on 2007-09-25
Can someone explain this a bit more for a thicky like me?
I'm a bit lost.

especially the client side of it, can the client be elsewhere to the main server?
Are there hardware clients?
why is this different from DAAP or the uPnP servers out there?
Is there a Windows client?

Ta
J

---

### Post by fuscia on 2007-09-25
> **jethro10 said:**
> Can someone explain this a bit more for a thicky like me?
I'm a bit lost.

especially the client side of it, can the client be elsewhere to the main server?
Are there hardware clients?
why is this different from DAAP or the uPnP servers out there?
Is there a Windows client?

Ta
J

there's a forum for it - [http://www.musicpd.org/forum/](http://www.musicpd.org/forum/) 

i don't really understand much of what i've read, so far (but, i had to look up daemon, finally).

---

### Post by mcduck on 2007-09-25
> **jethro10 said:**
> Can someone explain this a bit more for a thicky like me?
I'm a bit lost.

especially the client side of it, can the client be elsewhere to the main server?
Are there hardware clients?
why is this different from DAAP or the uPnP servers out there?
Is there a Windows client?

Ta
J

Yes, the client can run on other machine. There are both Windows and Mac clients available. Also if you are running a web server on the same machine where MPD is running you can use a web-based client which allows you to control MPD from a web browser running on any machine (including mobile phones, PDAs and such).

The thing is that MPD is not a streaming server. Whatever you use to control MPD, the music is played by the computer that runs MPD. But if you want there are ways to use MPD with streaming servers.

---

### Post by wieman01 on 2007-09-25
Metropolitan Police Department? Multiple personality disorder? What the heck... ;-)

---

