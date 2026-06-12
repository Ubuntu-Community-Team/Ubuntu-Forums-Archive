---
title: "Hi, I'm new and have a few questions"
date: 2009-05-03
forum: The Cafe
---

### Post by JEL Productions on 2009-05-03
Hi everyone, 

Forgive me if this isn't the right spot to post this. I'm new and have a few questions about Ubuntu. I'm going to be buying a new Dell Inspiron 15 laptop very soon, and I'm considering putting Ubuntu on it (I don't like Vista; however I'll have to keep it on there as a dual-boot). 

The questions I have are fairly basic, and yes I've used Google to try and find answers. 

First, what kind of programming languages do you have to use in order to develop games on Ubuntu? I know it's possible to create 3D games and such (which I'm really into doing on Windows XP), but I'm used to BASIC, and I'm not sure what language one has to use on Ubuntu.

Also, what kind of video editing software is there available? Is there any that might support Chroma-Keying? It's not a big deal if none don't, I'm just curious. 

Any input is appreciated! Thanks!

---

### Post by tom66 on 2009-05-03
Game development on Linux is quite well supported... You have a number of options:

[list]
[*] OpenGL & C(++) - like DirectX on Windows, but open source. Commercially supported by graphics card vendors. SDL is another option. Based on OpenGL, it adds more features such as mouse input, window management, sound, keyboard, etc. so you don't have to worry about these.
[*] PyGame, a very cool Python game library. Based on SDL. Python is a fantastic language for a beginner and an expert alike. It really emphasises programming without all the nits and hacks involved. However, Python is quite slow and not suited to heavy processing, so often you'll find two parts to a game: the game engine, written in C(++) or another fast compiled language (which SDL is), and the controlling logic, written in Python or another scripting language.
[*] You've also got Java. Not sure how this works, but take a look.
[*] PyOpenGL. Like PyGame but OpenGL. 
[*] Other languages supporting OpenGL/SDL. (Many, many.)
[*] If you like tying yourself to proprietary standards, then you can develop with Winelib and write DirectX apps under Linux. However, full functionality is not implemented (most things are but there are still bugs).
[*] I'm sure many BASIC interpreters will work on Wine (in case you don't know, this 'implements' Windows and makes some Windows apps work) and some will exist for Linux. However, I don't know where to look.
[/list]

Chroma keying is supported by Cinelerra, a powerful non-linear video editor, as well as other programs. Cinelerra comes in two versions: the official version and the community version. Both have different features and both are awesome programs.

---

### Post by JEL Productions on 2009-05-03
Thanks! That's a great load of information. I've messed with Python, but not enough to learn the language very well, and it was a few years ago that I messed with it anyway. 
I'll definitely check into everything you said. Thanks again!

---

### Post by HermanAB on 2009-05-03
Basically, all computer languages since King Tut's Abacus are supported on Linux.
:)

---

### Post by init1 on 2009-05-03
> **JEL Productions said:**
> 
Also, what kind of video editing software is there available? Is there any that might support Chroma-Keying? It's not a big deal if none don't, I'm just curious. 

Any input is appreciated! Thanks!
Last I checked, there aren't many good video editors. Avidemux is good, but is rather simple. I've heard good things about Cinelerra, but it's crashed every time I've used it. Open Movie Editor looks like it would be good, but it's not very reliable. 
Of course, it's been about a year since I've tried these, so they might have improved. In any case, I hope you find one that works :D

---

### Post by upchucky on 2009-05-03
when you go to buy a laptop/pc take a couple of live cds with you like Ubuntu, Ubuntu alternate cd, Knoppix and any other live ones you may be interested in.

This way you can just plop the cd into the machine, boot it and see if everything runs, if the sales person objects, be polite explain it does nothing to the machine, if still they resist, find a new store.

---

### Post by JEL Productions on 2009-05-03
Thanks all! I really appreciate the advice and information. I've looked up Cinelerra and I like what I see. I also looked up 3D game making on Ubuntu and found a lot of promising looking things. 

Thanks again!

---

