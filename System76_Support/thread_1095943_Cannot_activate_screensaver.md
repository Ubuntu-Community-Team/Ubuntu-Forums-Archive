---
title: "Cannot activate screensaver"
date: 2009-03-14
forum: System76 Support
---

### Post by betrunkenaffe on 2009-03-14
Thought I'd see if anyone has suggestions on how to fix this. My screensaver won't activate, I see the screen start to darken but as soon as it goes to load, it pushes back to the desktop. I have swapped between a few different screensavers to see if it was that but it's the same result every time. I don't remember doing any major changes however I also haven't used the screensaver since before I installed nVidia 180 gfx drivers (there has been numerous updates to the laptop since then).

I have the Pangolin Performance (purchased this last January).

I'm going to try backdating my drivers and see if that solves the problem.

---

### Post by betrunkenaffe on 2009-03-14
FYI, that had no effect...

I managed to get a work around going by having it lock the computer when it activates the screensaver.

---

### Post by khelben1979 on 2009-03-14
Have you tried [xscreensaver]("http://en.wikipedia.org/wiki/Xscreensaver")?

---

### Post by betrunkenaffe on 2009-03-14
Nope, just wanted to get the ones that came installed with Ubuntu to work. They used to. Just stopped working for some reason. I also had to disable the screen turn off functionality because the screen wouldn't come back on :)

---

### Post by thomasaaron on 2009-03-16
```
I managed to get a work around going by having it lock the computer when it activates the screensaver.
```

That sounds like it could be an xserver or an nVidia bug. I'll run some tests on it and see if I get the same problem.

---

### Post by betrunkenaffe on 2009-03-17
I thought it was an nVidia bug but I still had it when I back dated to 177 for driver. It's not a huge issue since screensavers are pointless these days without the account lock. The screen shut off is more of an annoyance to me now simply because it's a power saving feature that isn't available (granted, I'll probably suspend the comp when not doing things).

---

### Post by betrunkenaffe on 2009-03-24
thomas: how did your tests go?

---

### Post by thomasaaron on 2009-03-25
Sorry, I forgot to post back.

I'm getting the same thing, with or without compiz enabled.

I think it is this bug...

[https://bugs.launchpad.net/ubuntu/intrepid/+source/gnome-screensaver/+bug/278112](https://bugs.launchpad.net/ubuntu/intrepid/+source/gnome-screensaver/+bug/278112)

We're smack in the middle of Jaunty testing now. I'll report back on whether or not it is fixed there.

---

### Post by betrunkenaffe on 2009-03-26
Fantastic, that is exactly the bug. If it's fixed in Jaunty, yay, otherwise, oh well.

---

