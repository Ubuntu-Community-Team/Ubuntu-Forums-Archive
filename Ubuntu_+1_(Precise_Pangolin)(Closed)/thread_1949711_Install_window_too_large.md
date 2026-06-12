---
title: "Install window too large"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Skaperen on 2012-03-30
Xubuntu 12.04 Beta2 desktop i386.
ASUS S101 netbook with 1024x600 display.

The install window is just a bit too large for my netbook, and a little bit gets cut off at the bottom.  The "minimum size" setting needs to be smaller.  Then window content can be scrolled.  There's no scroll bar now.  I don't think there is anything lost, but others encountering this might wonder.

---

### Post by dcstar on 2012-03-31
> **Skaperen said:**
> Xubuntu 12.04 Beta2 desktop i386.
ASUS S101 netbook with 1024x600 display.

The install window is just a bit too large for my netbook, and a little bit gets cut off at the bottom.  The "minimum size" setting needs to be smaller.  Then window content can be scrolled.  There's no scroll bar now.  I don't think there is anything lost, but others encountering this might wonder.

So what's the bug report **you** have lodged?

---

### Post by Skaperen on 2012-03-31
Not a bug, per se.  Just a UX nit.

---

### Post by cariboo on 2012-03-31
> **Skaperen said:**
> Not a bug, per se.  Just a UX nit.

Actually it is a bug, since the demise of the netbook edition, they seem to have been forgotten. All graphical applications need to be running in full screen on a netbook/small screen device. Now you have to manually make applications run in full screen mode, previously it was done by default.

I plan on taking the problem to the unity-design mailing list after Precise is released, as it's to late to do anything now.

---

### Post by Skaperen on 2012-03-31
> **cariboo907 said:**
> Actually it is a bug, since the demise of the netbook edition, they seem to have been forgotten. All graphical applications need to be running in full screen on a netbook/small screen device. Now you have to manually make applications run in full screen mode, previously it was done by default.

I plan on taking the problem to the unity-design mailing list after Precise is released, as it's to late to do anything now.
Why not just make the windows tighten up a bit when the screen is small.  Of course, full screen mode can work, too.  But in either case, the wasted space inside the window needs to be tightened up.

I'm curious what part of code is deciding on the spacing inside the window.  The installer program?  Or a library somewhere?

---

### Post by wojox on 2012-03-31
My asus 900 I needed to press the Alt key while dragging them with the mouse. ;)

It's a work around for now.

---

### Post by cariboo on 2012-03-31
> **Skaperen said:**
> Why not just make the windows tighten up a bit when the screen is small.  Of course, full screen mode can work, too.  But in either case, the wasted space inside the window needs to be tightened up.

I'm curious what part of code is deciding on the spacing inside the window.  The installer program?  Or a library somewhere?

I'm not sure how the placing of elements is set, but in my small experience playing with gui creation software, in many cases if you want to keep a particular look, the placement of elements can be hard coded.

---

### Post by Skaperen on 2012-04-03
> **cariboo907 said:**
> I'm not sure how the placing of elements is set, but in my small experience playing with gui creation software, in many cases if you want to keep a particular look, the placement of elements can be hard coded.
I would rather do the GUI window layout in a way that, if the normal layout cannot be achieved, squishes an amount of dead space out until things can fit in the window size.  That dead space removal should be proportional to keep the basic appearance of the window.  The install windows have quite a bit of dead space.

---

### Post by jroa on 2012-04-03
> **wojox said:**
> My asus 900 I needed to press the Alt key while dragging them with the mouse. ;)

It's a work around for now.

Same here.  I can't remember the brand, but it was one of the ONE netbooks.  ALT + drag worked fine.

---

### Post by cariboo on 2012-04-03
One my Compaq Mini 1100, once an application is set to full screen, it opens that way all the time, I'd just prefer they be opened full screen by default.

---

### Post by jroa on 2012-04-03
I thought we were talking about a live install.

---

### Post by cariboo on 2012-04-03
> **jroa said:**
> I thought we were talking about a live install.

We are, but after installation the problem persists.

---

### Post by Skaperen on 2012-04-03
> **jroa said:**
> Same here.  I can't remember the brand, but it was one of the ONE netbooks.  ALT + drag worked fine.
Acer?

---

