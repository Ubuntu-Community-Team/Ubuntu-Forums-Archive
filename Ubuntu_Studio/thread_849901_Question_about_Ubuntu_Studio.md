---
title: "Question about Ubuntu Studio"
date: 2008-07-05
forum: Ubuntu Studio
---

### Post by mazz72 on 2008-07-05
Hi all.

I do alot of audio/video production work and want to start doing it in Ubuntu (if I can do this, I can rid myself of Windows forever). 

Now...Ubuntu Studio is an entire OS in itself, correct? So if I install that, would that mean I'd have to then reinstall all of my programs that I now have, and redo all of my customizations that I've done since I've been using Ubuntu, or can they be transferred over to Studio?

If I am going to have to start from scratch with Studio, how can I go about installing all of the audio and video editing programs in Studio, without installing the actual OS? I've seen the list in Synaptec, but I'm not sure which ones I'd have to install to get full use of those programs without installing the entire OS...if that can, indeed, be done.

Thanks for any help you can offer. Much appreciated.

---

### Post by heddleston on 2008-07-05
the big thing ubuntu studio is the rt-kernel, everything else is just a differently looking theme and the software packages. if you want to upgrade to the whole thing, try this:

> sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

if you just want the software packages, then leave out the linux-rt part & ubuntustudio-desktop (which is the theme) if you are going to be doing audio stuff though, id recommend putting in the rt kernel.

---

### Post by Stochastic on 2008-07-05
The only thing I'd add to heddleston's answer is that the meta-packages are all installable by themselves, you don't need to install ubuntustudio-video if you will never edit video; same with audio, graphics, even desktop if you don't like the look of the ubuntustudio theme/icons/bootsplash/etc...

---

### Post by brunolabs on 2008-07-05
Install from Synaptic Package Manager:

- ubuntustudio-audio
- ubuntustudio-video

---

### Post by mazz72 on 2008-07-06
> **brunolabs said:**
> Install from Synaptic Package Manager:

- ubuntustudio-audio
- ubuntustudio-video

Cool. That's what I needed to know. Thanks a lot! :)

---

### Post by Stochastic on 2008-07-07
> **mazz72 said:**
> Cool. That's what I needed to know. Thanks a lot! :)

You really should also install linux-rt through synaptic too if you're doing audio work.

---

### Post by Bucky Ball on 2008-07-17
Hey Mazz72, you should check out these two options:

[http://www.dynebolic.org/](http://www.dynebolic.org/)

[http://devel.goto10.org/puredyne/](http://devel.goto10.org/puredyne/)

Could be just what you're after. Access UStudio packages and customise. Plus portable, which might be good in your situation (see the docking option etc). I haven't tried them yet but downloaded them awhile ago. And this may be of interest;

[http://ubuntuforums.org/showthread.php?t=794423&highlight=64+studio](http://ubuntuforums.org/showthread.php?t=794423&highlight=64+studio)

Good luck

---

