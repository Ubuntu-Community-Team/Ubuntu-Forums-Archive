---
title: "Why are panel shadows often left out of distros?"
date: 2012-10-08
forum: The Cafe
---

### Post by eggsbenedict on 2012-10-08
Greetings all,

I am an ubuntu 12.04 LTS unity 2d user.  Unfortunately, my computer cannot completely handle the requirements for 3d.  Oh well.  Anyway, I've managed to make 2d completely usable and comfortable for me (and even though I'm on the fence about unity, I've managed to work around it).  But anyway, when I began using 2d I was often disappointed by the small details that make 3d ubuntu look so much better than 2d.

One of the big gripes I had with 2d (and I noticed with other distros like xubuntu), is that the panel shadow is almost always not present.  Sure, there are window and menu shadows you can enable with gconf and whatnot, but these don't help create a panel shadow.  

I found a way to get around this: I simply logged into 3d and took a screenshot of the desktop.  I then logged back into 2d, make that screenshot my desktop background and voila! panel shadow in 2d.  It is a small detail that I had always wanted in 2d.  To me, it actually makes the desktop look a LOT better.  To each their own, I guess.

But, I wonder, why are panel shadows always omitted in lower specc'd distros?  I mean, my solution was pretty non-technical and simple.  I'm sure the explanation as to why is much more complicated, but surely, someone smarter than I could write a small code to put something on the desktop background image for a panel shadow feel?

---

### Post by Frogs Hair on 2012-10-08
Xfce has compositing and transparency but again it depends on the hardware. 12.10 no longer has Unity 2D by default but it can be installed . Eye candy usually requires 3D graphics and I think upgrading the graphics is one way to do that and it doesn't have to be an expensive card either. You may be able to find a theme that gives the illusion of drop shadows also.

---

### Post by eggsbenedict on 2012-10-10
I get that having better effects relies on having more advanced hardware.  However, I am wondering specifically why panel shadows are omitted in distros that offer window/menu shadows when your hardware can handle it.  

I am really curious, but I'm worried I'm not asking the question the correct way.  Xfce does have compositing and transparency, just like unity 2d.  What I'm wondering though, is why when you do have the hardware capacity for compositing and transparency even in these distros, panel shadows are not included when window shadows and menu shadows are.

---

### Post by wheeze on 2012-10-11
MATE has a panel shadow when you enable Marco's compositing mode. Just like it's parent GNOME 2 did.

---

### Post by BrokenKingpin on 2012-10-11
If the panel supports shadows then just turn them on. If the panel does not, such as the unity 2D panel, it is probably because compositing is required for the shadows (which is why you only get them in Unity 3D).

Personally I don't think the shadows add all that much.

---

