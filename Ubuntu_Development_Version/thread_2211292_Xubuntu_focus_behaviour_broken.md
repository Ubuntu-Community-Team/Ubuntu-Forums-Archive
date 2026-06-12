---
title: "Xubuntu focus behaviour broken?"
date: 2014-03-15
forum: Ubuntu Development Version
---

### Post by The Cog on 2014-03-15
Either they've broken the focus behaviour, or I've lost a setting somewhere. 
For years, I have been set up so that although clicking a window (anywhere in the window) gives it focus and raises it, using the scrollwheel scrolls whichever window it's over without giving it focus. I installed 14.10 and don't seem to be able to configure this behaviour any more. If I select "Raise on click" in the settings , then the scrollwheel also focuses and raises the window. I want "raise on click" but not "raise on scroll".

Have they changed the way XFCE works, or am I missing a setting somewhere? Can anyone point me to where I can configure this, please.

---

### Post by ajgreeny on 2014-03-15
I wonder if that is a function in xfce-4.10.  I am using Xubuntu 12.04 but use the ppa for xfce-4.10, and my system does what yours is doing, ie scrolling in a background window also focuses the window.

I can't remember what xfce-4.8 used to do.

---

### Post by Toz on 2014-03-15
Try unchecking the "Raise windows when any mouse button is pressed" setting in Window Manager Tweaks -> Accessibility.

---

### Post by The Cog on 2014-03-15
> **Toz said:**
> Try unchecking the "Raise windows when any mouse button is pressed" setting in Window Manager Tweaks -> Accessibility.

Aaah! Thank you so much, Toz. That was it.
It feels so much more comfortable now - like an old shoe.

---

### Post by Elfy on 2014-03-15
Not sure I'm following - but does unchecking Raise on Focus in Window Manager do what you want. I can scroll hexchat/firefox underneath settings manager with that disabled.

ninja'd by the cog

---

### Post by The Cog on 2014-03-15
No, raise on focus seems to be something different though I'm not sure what.
Scrolling a large reference doc (e.g. a maximised web page) behind a smaller window where I'm trying things out is indeed the way I like to work.

---

### Post by ajgreeny on 2014-03-15
I did not even realise how useful it could be to scroll a background document and keep, for example, a dialogue box focused in the foreground.

Thanks for the tweak.

---

### Post by sammiev on 2014-03-16
> **ajgreeny said:**
> I did not even realise how useful it could be to scroll a background document and keep, for example, a dialogue box focused in the foreground.

Thanks for the tweak.

+1 and Thanks

---

### Post by sffvba[e0rt on 2014-03-16
This "feature" is one of the things I always miss when I have to use Windows...

---

