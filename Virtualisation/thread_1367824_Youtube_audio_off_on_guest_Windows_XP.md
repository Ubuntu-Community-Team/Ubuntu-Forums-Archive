---
title: "Youtube audio off on guest Windows XP"
date: 2009-12-29
forum: Virtualisation
---

### Post by natgab on 2009-12-29
I using the latest VirtualBox, to run Windows XP as guest on my computer, with Ubuntu Studio 9.04 as host.

I really like it so far, but I am having a little trouble.  I can watch YouTube ok, but it seems like the sound is off by a half second in XP?  

The video looks decent, I gave it the full 128MB and 2D & 3-D acceleration. Both as a smaller window and as full screen (19" widescreen). It is set as AC97 sound.

Very pleased with VirtualBox otherwise, works well and had easy set-up :KS

---

### Post by fouadatmeh on 2009-12-30
Hello,

Try these audio settings in Virtualbox, they seem to work fine:

Host Driver:OSS Audio Driver
Controller:ICH AC97
 
Hope That Helps...

---

### Post by natgab on 2009-12-30
Hey thanks,

It made a difference and now seems to be in sync.  Weird thing is that it only seemed to be YouTube.  I tested the Quicktime HD trailers and those where in sync.  Maybe its more of a streaming problem?

Now off to play with a virtualbox version of Haiku...

---

