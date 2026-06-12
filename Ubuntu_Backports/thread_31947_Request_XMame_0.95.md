---
title: "Request: XMame 0.95"
date: 2005-05-05
forum: Ubuntu Backports
---

### Post by Dax0r on 2005-05-05
Universe contains version 0.86 which seems to have many bugs and its very old.

Xmame 0.95 is here : [http://x.mame.net/](http://x.mame.net/)

---

### Post by jdong on 2005-05-06
Debian Sid contains version 0.94-1, which I'll backport.

I do not like going newer than Debian Sid.

---

### Post by Dax0r on 2005-05-06
thank you   :)

---

### Post by McQuaid on 2005-05-06
Maybe I should put it in a second request but it's related.  

Requesting Gxmame, a really good gtk2 front end for mame.

---

### Post by Technoviking on 2005-05-06
[QUOTE=McQuaid]Maybe I should put it in a second request but it's related.  

Requesting Gxmame, a really good gtk2 front end for mame.[/QUOTE]
I have made a backport of gxmame 0.34b and sent it to jdong.

Mike

---

### Post by jdong on 2005-05-06
xmame 0.94 bombs out with compilation failures, presumably because of Xorg vs XFree incompatibilities.

---

### Post by Technoviking on 2005-05-06
I think libglide3.so.3 is needed by xmame 0.94/0.95.

Mike

---

### Post by denzilla on 2005-05-06
Shame you can't just DL a binary and execute mame like in Windows. I'll never truely be able to free myself of Windows because all the emulators I like are either not maintained to the same degree as windows versions or are a pain in the @ss to get working on Linux.

---

### Post by leech on 2005-05-09
I just installed Xmame packages that are in Debian Sid and it worked fine.  Also there is a repository that has gxmame in it.

Just add 
```
deb http://anarxia.dyndns.org/debian/ ./

``` to your /etc/apt/sources.list or through Synaptic.

Leech

---

### Post by McQuaid on 2005-05-10
I'd rather not add debian sid repositories in ubuntu.  I hope the error can be resolved for xmame.  Is any effort being put in still in getting it to work?

---

### Post by leech on 2005-05-14
By the way, xmame 0.96 is now out as well.  Though the Debian Sid packages are still at 0.94.  

This is the one thing that really is preventing me from moving from my diced together debian/ubuntu setup to Breezy.

Leech

---

### Post by leech on 2005-05-14
[QUOTE=McQuaid]I'd rather not add debian sid repositories in ubuntu.  I hope the error can be resolved for xmame.  Is any effort being put in still in getting it to work?[/QUOTE]

If you'd prefer, you could always get the cvs version of gxmame then just do a 'sudo dpkg-buildpackage' from the gxmame directory.  It has everything to build the debian package right there.

Leech

---

