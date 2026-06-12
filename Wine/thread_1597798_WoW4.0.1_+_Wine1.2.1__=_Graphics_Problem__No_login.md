---
title: "WoW4.0.1 + Wine1.2.1  = Graphics Problem / No login"
date: 2010-10-15
forum: Wine
---

### Post by Lolpanda on 2010-10-15
```
Fglrxinfo: 


OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 3.3.10237 Compatibility Profile Context
```



```
glxinfo | grep rendering
direct rendering: Yes

```

FGLRX version and Xorg are both default that ships with Ubuntu 10.10

If I issue the OpenGL flag to launcher, or set gxAPI to OpenGL under config, when I start the login screen, the entire thing is garbled (See screenshot). 

if I don't issue OpenGl, its okay (more or less, small glitches, but very small) I can actually see what I'm doing, but upon login I get "Unable to Validate Game."  

Ran Repair.exe, it says WoW's fine.

Card is the 3200 HD as you can seen.

If anyone has any ideas / input I'd be happy to hear it

Hell for all I know this could be a fact that 10.10 shipped with Beta fglrx drivers and the stable isnt out yet, I dont know. If thats the case, fine, I wait a few weeks for the actual release, if its something else, I'd like to try and fix it.

---

### Post by cwwilson721 on 2010-10-15
Man, we ought to starta WoW subforum in wine

With BIG CAPITOL LETTERS on the title saying:
[SIZE="5"]***Don't complain about video issues until you install the proprietary drivers!***[/SIZE]

I know I'm being a bit harsh here, but, C'mon People! How hard is it to read the EXCELLENT HOW-TO in these forums, and JUST DO IT?

Then, if/when you run into issues, post.

---

### Post by Lolpanda on 2010-10-15
Yo, CW, STFU. I AM using the propriatery drivers, and you'd know that if you weren't so that  lazy you didn't  even read the output of fglrxinfo: says ATI not Mesa. So when you can actually read through a post, you can come back. In the meantime, GTFO of my thread.

If anyone has some ACTUAL advice on my poblem, I'd still love to hear it.

---

### Post by cwwilson721 on 2010-10-15
> **Lolpanda said:**
> ...Hell for all I know this could be a fact that 10.10 shipped with Beta fglrx drivers and the stable isnt out yet, I dont know. If thats the case, fine, I wait a few weeks for the actual release, if its something else, I'd like to try and fix it.No, you did NOT say that. 

Use the Hardware Drivers app, and install the latest drivers.

---

### Post by Lolpanda on 2010-10-15
Fglrxinfo TELLS you I am using The Proprietary drivers, If I wasnt it wouldve shot back "mesa" instead of ATI. And the comment about the drivers was an offhand remark to the fact that the drivers shipped with 10.10 aren't stable -- they're a beta release Ati gave to the dev's with xorg 1.9 support so that Ubuntu Meerkat could ship o ntime with working drivers.

---

### Post by dino99 on 2010-10-16
dont stay with wine 1.2.1, now 1.3.5 is out

---

### Post by cwwilson721 on 2010-10-16
> **Lolpanda said:**
> Fglrxinfo TELLS you I am using The Proprietary drivers, If I wasnt it wouldve shot back "mesa" instead of ATI. And the comment about the drivers was an offhand remark to the fact that the drivers shipped with 10.10 aren't stable -- they're a beta release Ati gave to the dev's with xorg 1.9 support so that Ubuntu Meerkat could ship o ntime with working drivers.
Well, obviously, you know what is what, and that I don't.

So while you whine, I'm playing WoW on 10.10 on my second box w/Ati in crossfire at 125FPS

I obviously don't know. So I bow to you, O Greatest Font of Knowledge.

---

### Post by Lolpanda on 2010-10-16
> **cwwilson721 said:**
> Well, obviously, you know what is what, and that I don't.

So while you whine, I'm playing WoW on 10.10 on my second box w/Ati in crossfire at 125FPS

I obviously don't know. So I bow to you, O Greatest Font of Knowledge.

You are a piece of work, Cw... Sorry that I know how to actually read an entire post (Wasnt even that long, geez)

---

