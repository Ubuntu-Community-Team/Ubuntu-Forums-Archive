---
title: "XBOX 360 + Ubuntu = ?????"
date: 2010-08-28
forum: Server Platforms
---

### Post by JD32 on 2010-08-28
Kinda an out there question, I don't no if any one could even help me but here it goes. I'm running Ubuntu 10 as file server for my desktop and laptops. One goal i had in mind when setting this up was to stream movies from it through my XBOX 360. But my 360 doesnt detect the linux machine on the network. I have samba and i can share between my windows machines no problem. So i guess my question here is does anyone know how i can get my 360 to play next with my linux machine???

      I was thinking maybe if i could get windows media center (cause that's what the 360 looks for i think) to run on my linux machine. I'm not sure how well it would run tho?

---

### Post by baudday on 2010-08-29
See if this helps:
[http://ubuntuforums.org/showthread.php?t=794489](http://ubuntuforums.org/showthread.php?t=794489)

---

### Post by kgatan on 2010-08-29
One alternative is to use a uPNP service on the linux server, like Mediatomb.
Im not sure however how well Xbox 360 handles uPNP.

Mediatomb is easy to setup, you just select folders from a web gui and vola.

---

### Post by badbradmx on 2010-08-29
> **kgatan said:**
> One alternative is to use a uPNP service on the linux server, like Mediatomb.
Im not sure however how well Xbox 360 handles uPNP.

Mediatomb is easy to setup, you just select folders from a web gui and vola.
  from what ive read it works with the PS3 but the 360 is rather hit and miss, it works with uPNP but is very selective about certain aspects

---

### Post by arrrghhh on 2010-08-29
DLNA media servers are interesting... no body seems to match the protcol perfectly (and as I undestand it a lot of the 'standards' are loose and not strictly-enforced...)

Plus, the 360 does not even come close to meeting the standard.  The PS3 comes pretty close, and it works better for streaming media.

With that said there are several media streamers - I think twonky or tversity (both paid, closed-source) are pretty good with all types of media and media servers.  [PS3MediaServer](http://code.google.com/p/ps3mediaserver/), believe it or not does support the 360 on a basic level - but I don't have one, so I'm not sure how good the support is - but it is by far the best (free) media streaming software I've used for Linux.

I also tried uShare and Mediatomb - found they were both inferior to PS3MediaServer.

With that said, Mediatomb is in the repo's - I just found it much more difficult to get up and running after it was installed... Plus, I found a fairly well-maintained repo for PS3MediaServer.

---

### Post by spynappels on 2010-08-30
For a very basic but stable and useable streamer, also look at MiniDLNA.

---

### Post by JD32 on 2010-08-30
ya i think instead im just gonna hook an old laptop of mine to my TV and use that 2 stream. Just seems easier :D. 

The 360 being a Microsoft owned doesn't want you using much but there own products, that's the main problem. An laptop with Ubuntu gives me x1000 more options and features then my 360 anyway.

---

### Post by arrrghhh on 2010-08-30
> **spynappels said:**
> For a very basic but stable and useable streamer, also look at MiniDLNA.

Interesting, I haven't tried this one.  I'll have to give it a shot!

---

### Post by spynappels on 2010-08-30
I was looking for a streamer and someone recommended it, and I had it up and running in literally 5 minutes. Basic but great for what I wanted.

---

