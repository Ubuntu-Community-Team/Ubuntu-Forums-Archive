---
title: "What do you think about X11/Xorg"
date: 2008-02-22
forum: Testimonials &amp; Experiences
---

### Post by roaldz on 2008-02-22
In my time of using Ubuntu, which is from 4.10 Warty Warthog, and before that some other distro´s too, I have always found that the X11 protocol, or Xorg is slow. Not the kind of slow that you can´t work with it, but slow in certain things.
For example, resizing windows. This is fast if I install windows on the same machine. 
I don´t want to put up Windows against Ubuntu, there are other threads for that. I just want to mention that it IS possible to make resizing windows MUCH faster (say, realtime, no shocking, no outlined borders, drawing glitches etc.).
It´s even slower with compiz enabled! That´s the weird part. If you have fast GLX acceleration, why not let the graphics card take it over? It is MUCH more suited for the job. It´s designed for it!
Please let me hear your thoughts on this one. 

Roald

---

### Post by ukripper on 2008-02-22
You can create your own desktop environment if you feel GNOME is slow for you.
[http://www.linux.com/feature/126177](http://www.linux.com/feature/126177)

Goodluck

---

### Post by dasunst3r on 2008-02-22
That's funny, because my windows react almost instantly when I move them.  I even have Compiz Fusion turned on, so they even wobble like Jello real well.

---

### Post by roaldz on 2008-02-22
> **dasunst3r said:**
> That's funny, because my windows react almost instantly when I move them.  I even have Compiz Fusion turned on, so they even wobble like Jello real well.

Yeah, no one seems to notice this.. I think I´m going to make a video or something.

Little benchmark:

goto [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and resize your firefox. You´ll see!

Roald

EDIT: About that video: [http://www.hjbllanos.nl/temp/desktop.avi](http://www.hjbllanos.nl/temp/desktop.avi)

that´s what I mean. Resizing is slow.

---

### Post by roaldz on 2008-02-22
BumP´rt

---

### Post by dasunst3r on 2008-02-22
> **roaldz said:**
> Yeah, no one seems to notice this.. I think I´m going to make a video or something.

Little benchmark:

goto [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and resize your firefox. You´ll see!

Roald

EDIT: About that video: [http://www.hjbllanos.nl/temp/desktop.avi](http://www.hjbllanos.nl/temp/desktop.avi)

that´s what I mean. Resizing is slow.I see now.  I tried what you suggested, and the results varied.  While it is slow under normal resizing circumstances, it's a snap if I changed it to "rectangle" or "outline" because it only has to redraw once.

---

### Post by roaldz on 2008-02-22
> **dasunst3r said:**
> I see now.  I tried what you suggested, and the results varied.  While it is slow under normal resizing circumstances, it's a snap if I changed it to "rectangle" or "outline" because it only has to redraw once.

Yeah, but I´m sure my pc is fast enough to be able to redraw it fullspeed..:)

---

### Post by 3rdalbum on 2008-02-22
I don't think "my windows resize a bit more slowly" is a Linux-desktop-blocker :-)

---

### Post by RawMustard on 2008-02-23
I don't think it's xorg, it's Gnome, Gnome's a pig well, metacity is I guess.  Redraws are instant in fluxbox, faster than windows.  And you can't use Firefox to test window redraw, everyone knows Firefox is super slow.  :(

---

### Post by roaldz on 2008-02-23
> **RawMustard said:**
> I don't think it's xorg, it's Gnome, Gnome's a pig well, metacity is I guess.  Redraws are instant in fluxbox, faster than windows.  And you can't use Firefox to test window redraw, everyone knows Firefox is super slow.  :(

Yeah, that´t the point. Super slow, on X. Not on windows:) Have to make a movie about that too:)

Roald

---

### Post by roaldz on 2008-02-26
Made a new video.
Just installed WinXP in Virtualbox OSE edition, installed firefox and ran it in seamless mode.
Here´s the result:

[http://www.hjbllanos.nl/temp/desktop2.avi](http://www.hjbllanos.nl/temp/desktop2.avi)

The difference is CLEAR.

Roald

---

### Post by eldragon on 2008-02-26
i always got the same feeling to.
redrawing feels slow, or at least not instant. something on windows or mac you dont feel.

now that i got open source intel drivers on this new notebook, the feeling disappeared since i got compiz on the background.

i believe the problem is not speed (from them moment you ask it to do something till its done), but how its being done.

i think windows does everything on the background and then places the result onscreen (dont quote me on this) while gnome does it line by line, and thus, you get the feeling you see things being redrawn.

its odd you get the feeling with compiz, it always felt natural with it enabled.

---

### Post by Vadi on 2008-02-26
You have no idea what you're talking about.

Try using a different window manager - fluxbox for a start. That's geared towards low-end computers.

---

### Post by roaldz on 2008-02-26
> **Vadi said:**
> You have no idea what you're talking about.

Try using a different window manager - fluxbox for a start. That's geared towards low-end computers.

Who?

---

### Post by Vadi on 2008-02-26
You :s

---

### Post by roaldz on 2008-02-27
> **Vadi said:**
> You :s

Well.. Please correct me where I´m wrong. I´m open for new ways of seeing things. Please tell me, what did I say wrong?

Roald

---

### Post by Vadi on 2008-02-27
I did tell you, but I will again - the problem is the *window manager*. As the name implies, it's responsible for drawing windows, and since your problem is with resizing them, the WM is at fault here. Not xorg, or x11.

Try using a different window manager, like fluxbox, or compiz (if you have a relatively decent card).

---

### Post by kellemes on 2008-02-27
> **roaldz said:**
> Well.. Please correct me where I´m wrong. I´m open for new ways of seeing things. Please tell me, what did I say wrong?

Roald

Nothing at all..

I agree with you here that GNU/Linux hasn't been able to provide the best of graphics performance, at least compared to Windows. 
xorg has something to do with this since wm's do use it's framework to do there thing (including moving/resizing windows).

In the end though.. the only way to gain a large performance boost is to change and/or optimize your dm/wm. And obviously ditch compiz. Easy for me since I very much hate it. ;-)

By the way, XFCE with some shading and opacity is pretty damn cool.

---

### Post by roaldz on 2008-02-27
> **Vadi said:**
> I did tell you, but I will again - the problem is the *window manager*. As the name implies, it's responsible for drawing windows, and since your problem is with resizing them, the WM is at fault here. Not xorg, or x11.

Try using a different window manager, like fluxbox, or compiz (if you have a relatively decent card).

Compiz is much worse than metacity, while I have a decent card (Nvidia 7600). I´m already using compiz btw.

---

### Post by Vadi on 2008-02-27
Well, check your drivers then. I didn't have any issues on a radeon 7500 (which is waaay older than nvidia 7600). Or give fluxbox a try :)

---

### Post by roaldz on 2008-02-28
> **Vadi said:**
> Well, check your drivers then. I didn't have any issues on a radeon 7500 (which is waaay older than nvidia 7600). Or give fluxbox a try :)

My drivers are fine, really. I don´t want to switch to another window manager than compiz. If my window manager is GL accelerated and slow on fast hardware, something must be wrong, right? Drivers are installed correctly.
Have you seen the video´s?

Roald

---

### Post by djbsteart1 on 2008-02-28
i dont have any issues with a go 420 so i doubt its the card, gnome did always seem slow in the sense being discussed here, but kde was fine.

---

### Post by Vadi on 2008-02-28
-sigh- yeah, sure, Xorg is to blame here. It's unsuably slow and we should make a better video/input server.

Feel free to get started.

---

