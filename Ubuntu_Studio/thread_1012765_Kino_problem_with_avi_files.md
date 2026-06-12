---
title: "Kino problem with avi files"
date: 2008-12-16
forum: Ubuntu Studio
---

### Post by jodei on 2008-12-16
Hi All,

Right, so I'm completely new to this sort of thing so apologies if I sound like a complete idiot!

I have some .avi files that I'd like to edit in Kino, they were created on a Windows machine, which can be a problem gauging some of the issues I've come across when looking into getting this resolved.  I understand that I need to change the format of the files so that Kino can work with them, so I do the following...

ffmpeg -i bug.avi -target pal-dv bug.dv

...but get the following error:

bug.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.

Can anyone out there please help me?  The original input files are just fine from what I can tell...

Thanks very much in advance :)
j

---

### Post by albinootje on 2008-12-16
What happens when you load your avi file in avidemux ?
Does that go well ?

---

### Post by herteljt on 2008-12-16
> **jodei said:**
> Hi All,
I understand that I need to change the format of the files so that Kino can work with them, so I do the following...

ffmpeg -i bug.avi -target pal-dv bug.dv

...but get the following error:

bug.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.



Have you tried converting the files with winff? It is a gui for ffmpeg that takes a lot of the confusion out of converting. For me using ffmpeg properly can be a stumbling block.

[http://code.google.com/p/winff/](http://code.google.com/p/winff/)

---

