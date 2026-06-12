---
title: "Screen recording software (videocapture)"
date: 2006-11-12
forum: The Cafe
---

### Post by MedivhX on 2006-11-12
Is there any program for recording screen activity in real time??? I need it to film my Beryl effects but I don't have video or digital camera...

---

### Post by maniacmusician on 2006-11-12
I think Kim for kde does this. Integrated right into konqueror

---

### Post by loell on 2006-11-12
recordmydesktop [recordmydesktop.sourceforge.net]("recordmydesktop.sourceforge.net")

you can get a deb package from here [http://www.ubuntuforums.org/showthread.php?t=294605]("http://www.ubuntuforums.org/showthread.php?t=294605")

---

### Post by iovar on 2006-11-12
Thanks for the recommendation loell, but 0.2.6 doesn't play nice with 
beryl/compiz.
The CVS one does though, but it needs some polishing and it doesn't yet 
integrate well with the frontend. 

@MedivhX:
If you can't find something else or want to try it anyway, I'm here if you
need any help with cvs checkout/compilation/running from cli.

---

### Post by MedivhX on 2006-11-12
Thanks i'll PM you if I need something. I wanted to ask what do you people think about this one [http://sourceforge.net/projects/screenkast](http://sourceforge.net/projects/screenkast)

---

### Post by loell on 2006-11-12
> **iovar said:**
> Thanks for the recommendation loell, but 0.2.6 doesn't play nice with 
beryl/compiz.
The CVS one does though, but it needs some polishing and it doesn't yet 
integrate well with the frontend. 

@MedivhX:
If you can't find something else or want to try it anyway, I'm here if you
need any help with cvs checkout/compilation/running from cli.

your welcome iovar, your program is really useful, and i'm looking forward for the  next near release :mrgreen: 

can you also provide a cvs instruction on the site?

---

### Post by mostwanted on 2006-11-12
I use Istanbul on Edgy. If you run the program and make sure to enable the "record 3D effects" tick box, it works fine.

---

### Post by OffHand on 2006-11-12
> **mostwanted said:**
> I use Istanbul on Edgy. If you run the program and make sure to enable the "record 3D effects" tick box, it works fine.

I copy that.

---

### Post by MedivhX on 2006-11-12
OK, but is there a repository for Istanbul???

---

### Post by loell on 2006-11-12
already made a deb package from cvs , improved in performance and as iovar already said it can now record beryl/compiz through autodetection

[http://www.f-forge.com?d=rbYOwMRHNZxKBF7CeP06](http://www.f-forge.com?d=rbYOwMRHNZxKBF7CeP06)

---

### Post by iovar on 2006-11-12
> **loell said:**
> already made a deb package from cvs , improved in performance and as iovar already said it can now record beryl/compiz through autodetection

Nice package!
If you can checkout, compile and package a cvs version you should consider MOTUing;)

@MedivhX, Screenkast is a vnc session recorder. You need a desktop recorder
for this (xvidcap, istanbul, recordMyDesktop ).

Istanbul's is in universe, but if you use loell's package you may get better performance. 
recordMyDesktop does the encoding when it's finished.

In any case, if you end up using it this will give you max performance:
```
~$ src/recordmydesktop --quick-subsampling --zero-compression
```
Hit ctrl-c to end a recording.

O.k I'm done promoting my program :-#

P.S. the dependencies for recordmydesktop should all come with a default installation of edgy.

---

### Post by MedivhX on 2006-11-12
Ok, people thank you all!!! I will install Istanbul and RecordMyDesktop!!!

---

