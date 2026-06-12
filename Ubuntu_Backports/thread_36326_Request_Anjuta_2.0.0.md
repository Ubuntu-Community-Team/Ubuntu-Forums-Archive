---
title: "Request: Anjuta 2.0.0"
date: 2005-05-22
forum: Ubuntu Backports
---

### Post by tzutolin on 2005-05-22
Just released :) 
2005-05-15
[http://anjuta.sourceforge.net/](http://anjuta.sourceforge.net/)

---

### Post by ow50 on 2005-05-22
> This is an alpha & unstable release and may not be suitable for production use.
Because of that we might not see a debian source anytime soon.

I tried to compile this from source about a week ago but it proved to be too painful. Too many un apt-gettable dependencies and finally some failure compiling.

---

### Post by jdong on 2005-05-23
Let's wait for Debian Sid sources. Even then, the dependencies might prove to be too painful.

---

### Post by Cwiiis on 2005-06-05
I was quite eager to use the new Anjuta, so I've built Ubuntu Hoary packages for all necessary deps that aren't already in Ubuntu (gdl, gnome-build, graphviz 2.2.1 (from debian unstable source packages), glade3 (cvs) and anjuta 2.0).

All seems to work on my system ok - The anjuta package doesn't conflict/replace the current anjuta/anjuta-common and I'm sure I haven't split/categorised the packages right, so any advice on how to fix the latter problem, I'll see what I can do (didn't fix the former because I just haven't gotten round to it yet).

There's also a missing dependency on autogen - it runs without it, but it's useless. I had to add a symlink from libgtkembedmoz.so in /usr/lib/mozilla-firefox in /usr/lib - The library path should be setup to not have to do this, so I'm guessing this is an Ubuntu fault, and not a fault of my packaging.

Anyway, you can find all the packages here:
[http://chrislord.net/stuff/debs/](http://chrislord.net/stuff/debs/)

And the debian directories, tar.bz2'd up in the parent directory.
(the graphviz debian directory, you can of course get from the debian unstable source package)

I had to make one little change to a Makefile in graphviz to add -lXaw to one of the linker lines, but otherwise it should all compile fine

---

### Post by Slo Mo Snail on 2005-06-06
Maybe I'll add packages later for ppc and i386 in extras... All deps doesn't seem to interfere with  the packages already in hoary... but I'll look further at it this evening (e.g. in 9 hours ;) )

---

### Post by Cwiiis on 2005-06-06
Unfortunately, it seems a bit buggy... The new interface is amazing though, I'm very much looking forward to when this hits stable :) I'll look into some of the bugs, see if any are my fault/fixed in CVS

Another change I made I forgot to mention - I altered glade3 cvs's automake file to install glade-project-window.h, which anjuta required.

---

### Post by ow50 on 2005-06-06
I tried these yesterday. Anjuta and especially glade3 are still a bit buggy. These packages, don't know which one, caused some sort of a mime database corruption for me. All files became either text/plain or octet-stream. Uninstalling these packages and reinstalling all *mime* packages fixed that. I don't think this is ready for extras repositories yet.

---

### Post by Cwiiis on 2005-06-06
[QUOTE=ow50]I tried these yesterday. Anjuta and especially glade3 are still a bit buggy. These packages, don't know which one, caused some sort of a mime database corruption for me. All files became either text/plain or octet-stream. Uninstalling these packages and reinstalling all *mime* packages fixed that. I don't think this is ready for extras repositories yet.[/QUOTE]

mm, same thing happened for me - Hopefully now that there are packages out there though, other more intrepid people will be able to investigate :) If anyone finds out what causes problems, I'll be happy to fix and repackage, I'm just lacking time at the moment (exams).

---

### Post by Slo Mo Snail on 2005-06-06
Ok, with such bugs it really isn't ready for extras ;) Let's wait a while until it gets less destructive ;)

---

### Post by GriMsb on 2005-06-08
How can I get the help files for anjuta 2? I have tried from anjuta.org but I don't know how to download, or where are the files.
(I know C language, but I am a newbie for linux)
thanks a lot

---

### Post by holomorph on 2005-07-28
What is the status of this as far as getting a working package into backports?   Anjuta version 2.0.1 is out now, perhaps this fixes some of the bugs? I don't know, but there are definately some features listed that are really lacking in the stable 1.x release.

---

### Post by Cwiiis on 2005-07-28
I've packaged up all the Anjuta dependencies correctly (with -dev packages seperate), but I haven't had the time to do Anjuta 2.0.1, I just have it installed in /usr/local - It still isn't advanced enough yet to supercede the 1.x series, but it'll probably get there by the next version. If you want me to upload packages for the deps that aren't in Ubuntu, just give me a shout (don't use the ones the ones linked to in my first post)

---

### Post by ow50 on 2005-07-28
Even the 2.0.1 is still very buggy.
> This is an alpha & unstable release and may not be suitable for production use.
I don't quite understand their version numbering. One might have expected 2.0.0 to be stable, but maybe they'll release 2.1.0 when it's stable.

I personally don't think these unstable releases should be officially backported, but if someone has made their own debs, please post links.

---

