---
title: "Opensource alternative to Flash?"
date: 2007-06-28
forum: The Cafe
---

### Post by sbjaved on 2007-06-28
Somebody know a good alternative to Flash (not the plugin) for Ubuntu? Or any way to run Flash 8 on Ubuntu?

---

### Post by mips on 2007-06-28
[http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)

Only one I know of.

---

### Post by Steveway on 2007-06-28
Flash9 is avaiable for Ubuntu and an Opensource alternative is Gnash. (Though it's only on par with Flash7)

---

### Post by jiminycricket on 2007-06-28
swfdec too.  I think Gnash is attempting to include some Flash 9.

---

### Post by justin whitaker on 2007-06-28
> **sbjaved said:**
> Somebody know a good alternative to Flash (not the plugin) for Ubuntu? Or any way to run Flash 8 on Ubuntu?

I think, if I read this correctly, you are looking for something like Flash for developing sites. Have you looked at any of the stuff on OSFlash?

[http://www.osflash.org/](http://www.osflash.org/)

Check our Red 5, Open Laszlo, Xical, Haxe.....mostly, you are going to need to do some actionscript coding.

---

### Post by airtonix on 2007-06-28
there is a program in the repos....called synfig...it is pretty darn close to flash studio.

---

### Post by Tomosaur on 2007-06-28
Do you mean an alternative to flash (ie a completely different technology)? If so, then Microsoft have recently announced Silverlight, and thanks to the guys at Mono, there is now an open-source implementation of Silverlight in record time. Silverlight looks very promising, and now we can all benefit from it rather than just Windows users.

If you meant something to create flash files with, then there are open source implementations, yes. I reccommend HaXe, which is available in the repositories. The website is [here](http://haxe.org). It can compile a variety of different JS-like languages, including ActionScript, and can make flash 9 compatible SWFs.

---

### Post by frup on 2007-06-28
Wow, I had been wondering about this but since I don't need it never searched... are my eyes deceiving me or are these OSS versions almost more powerful implementations (even if not finished completely)... like being able to use many languages for example?

---

### Post by Tomosaur on 2007-06-28
> **frup said:**
> Wow, I had been wondering about this but since I don't need it never searched... are my eyes deceiving me or are these OSS versions almost more powerful implementations (even if not finished completely)... like being able to use many languages for example?

Many OSS projects are more extensive, powerful, and feature-filled than their proprietary counterparts, because open-source means that the developers have access to the underlying code behind millions of other projects, which helps interoperability etc. This comes at a price, however - for a project which supports many different things (for example, many different languages), then the developers have less time to focus on supporting each thing fully and in the best possible way. Proprietary software is able to focus on one niche, and can do it extremely well, but this means that the user is limited in what they can actually do with that software. Proprietary developers also have to deal with the massive costs involved in licensing code from other developers, whereas open-source developers can stick with purely open source stuff. So, if you want choice, possibilities, and freedom, then use open-source. If you want vendor liability, very high quality / stability, then use proprietary. Open source means there's (usually) no liability - you use at your own risk, and it may not always work as you expect. Proprietary means you can (sometimes) hold the company responsible if something goes wrong as a result of using their software, although many proprietary licenses take away this right. Proprietary also means that whilst you may get a very high quality product, you are probably limited in what you can do with it, and need to buy more and more software to perform some task, which you could just do easily and for free with open-source.

That's not to say that open-source stuff is low quality!

---

### Post by sbjaved on 2007-06-28
A lot of people misunderstood. I want flash like utility for *developing animation* not for playback.

---

### Post by mips on 2007-06-28
> **sbjaved said:**
> A lot of people misunderstood. I want flash like utility for *developing animation* not for playback.

Then you should say so, don't be vague.

---

### Post by Footissimo on 2007-06-28
Flash 8 may well work on Wine with some fiddling - it's got gold/platinium rating on the WineDB

---

### Post by sbjaved on 2007-07-01
> **mips said:**
> Then you should say so, don't be vague.
Sorry. You're right. I should've been clearer.

---

### Post by deanlinkous on 2007-07-01
[http://www.synfig.com/](http://www.synfig.com/)

---

### Post by littlest_elf on 2008-08-26
there's this new thing - 3dmlw which seems to be a very promising alternative to flash, especially if you're looking for something to make animations etc with, not just a player. 3dmlw supports several 3d file formats and has blender support, a little bit of skeleton animation too. worth to check it out (:

---

### Post by geoken on 2008-08-26
Flex builder Linux + Inkscape is the closest you will come to the Flash IDE workflow using native apps. The flex compiler (which was open sourced by Adobe a long time ago) can treat SVG's as native sprite objects. It actually casts the as Shape (IIRC). It works better than trying to pull resources from compiled SWF's that aren't perfectly formatted (ie. the stuff you'd get from apps like synfig and Ktoon).

Using this workflow will probably also teach you that vectors aren't always optimal and in many situations you get a smaller file size and better performance with bitmap assets.

---

