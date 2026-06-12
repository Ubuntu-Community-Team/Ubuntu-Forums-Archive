---
title: "Important Finding...P2 button controls Webcam on Daru2"
date: 2008-02-18
forum: System76 Support
---

### Post by reh4c on 2008-02-18
Although others may already know it, I realized tonight that the "P2" button on the Daru2 enables/disables the Microdia webcam.  Here's some background.  I remembered last year that the webcam worked under Ubuntu 7.10, but it hasn't been working for quite some time.  Tonight, I decided to take a look at the output of "lsusb" and noticed that no webcam showed up.  At first, I thought it was broken.  Just for sh1*s and grins, I pressed the "P1" button and checked the output of "lsusb"...no change.  However, after pressing "P2" my Microdia webcam showed up!!!  Somehow I must have pressed it during the last few months.  Now, the Cheese program in Hardy Alpha is working fine.  Should work for previous versions (7.10) as well.  Please let me know.  My next question...what does the "P1" button control by default???  

Now, we just need to get that screen flickering/power management issue solved and get that goofy fingerprint reader running!!!:mad:

---

### Post by thomasaaron on 2008-02-18
Yes. That's kind of old news in these parts. :lolflag:

---

### Post by imhavoc on 2008-02-18
I feel like such a retard. Am I the only person that can't get the stupid webcam to work?

I realize that part of the problem is that I really don't have enough interest to stick with it until I get it working. If it's not going to cooperate relatively quickly, I'm gonna move on to something more important (to me).

---

### Post by thomasaaron on 2008-02-18
imhavoc, which computer do you have?

If you have the DarU2?
Try downloading "Cheese" from Applications >> Add/Remove.

If Cheese doesn't work, close Cheese, press the P2 button, and re-start Cheese.

Did that work?

---

### Post by reh4c on 2008-02-18
> **thomasaaron said:**
> Yes. That's kind of old news in these parts. :lolflag:

Better to be safe than sorry in passing info...:)

Does the "P1" perform any default function?  Thanks.

---

### Post by thomasaaron on 2008-02-18
True. True.

No, P1 isn't bound to anything.

---

### Post by imhavoc on 2008-02-19
> **thomasaaron said:**
> imhavoc, which computer do you have?

If you have the DarU2?
Try downloading "Cheese" from Applications >> Add/Remove.

If Cheese doesn't work, close Cheese, press the P2 button, and re-start Cheese.

Did that work?

Daru2, Kubuntu 7.10, P2, cheese installed from repositories as well as newer one from source.

The webcam 'on' indicator turns on, but Cheese freezes.

Go figure.

---

### Post by thomasaaron on 2008-02-20
Try turning on the webcam with P2 and THEN starting Cheese. Does that give different results?

---

### Post by imhavoc on 2008-02-21
> **thomasaaron said:**
> Try turning on the webcam with P2 and THEN starting Cheese. Does that give different results?

no. :(

(That's what I was doing, so I get the same results.)

---

### Post by thomasaaron on 2008-02-22
OK, let's handle this one via support(at)system76[dot]com. 
It is looking more like a hardware issue.

---

### Post by Vadi on 2008-02-22
What is the P2 button?

---

### Post by thomasaaron on 2008-02-22
It's a button above the DarU2 keyboard (second from the left).

---

### Post by kevin11951 on 2008-02-24
it might not be a hardware issue, go here:

[http://packages.ubuntu.com/gutsy/gnome/cheese](http://packages.ubuntu.com/gutsy/gnome/cheese)

and see the package no.
```
Package: cheese (**0.2.3**-0ubuntu1) [universe]
```

Then go to:

[http://www.getdeb.net/app/Cheese](http://www.getdeb.net/app/Cheese)

and see their package no.

```
Ubuntu Gutsy 32 bits - ** 2.21.5  **
```

looks like Ubuntu missed A LOT of releases!

---

### Post by 6174 on 2008-02-24
> **kevin11951 said:**
> 
looks like Ubuntu missed A LOT of releases!

I have a daru2 and cheese version 0.2.3 works with the webcam for me. However Ubuntu hasn't missed that many releases. If you go to the [cheese homepage](http://www.gnome.org/projects/cheese/) you'll see that they decided to change their release cycle to follow GNOME and accordingly changed their release numbering method. 

With a little bit of reading you'll find:
August 30, 2007 0.2.3 released
September 5, 2007 0.2.4 released
December 24, 2006 0.3.0 released
January 14, 2008 2.21.5 released

Looking at the dates involved, Ubuntu is pretty much up to date when you factor in the Ubuntu release cycle.

---

### Post by Vadi on 2008-02-24
They didn't miss a lot of releases. The program just changed the way their versioning works.

That said, do not use getdeb.net's package yet - it won't work. Use the one in ubuntus respositories, that one does work.

---

