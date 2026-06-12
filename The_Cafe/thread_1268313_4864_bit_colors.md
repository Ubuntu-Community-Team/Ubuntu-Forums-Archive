---
title: "48/64 bit colors"
date: 2009-09-16
forum: The Cafe
---

### Post by nerdopolis on 2009-09-16
I heard that some people actually have use for these higher color depths, and displays are being created that support finer colors. (and its implanted in Win 7)

Do the current Linux video drivers support 48/64 bit color? Or will it have to be implanted into the kernel to support higher color depths?

Or does the current X11 protocol only support 32 bit color? (I'm not bashing X when I ask this)

---

### Post by nerdopolis on 2009-09-17
no one knows?

---

### Post by tcoffeep on 2009-09-18
Apparently not.

---

### Post by coldReactive on 2009-09-18
> **tcoffeep said:**
> Apparently not.

Not that it matters since some people who try to set Ubuntu to have more than 24 bits of color (IE: 32) get an xorg issue and black screen welcomes them when they next boot.

Oh wait, that's me.

---

### Post by LowSky on 2009-09-18
the average human eye can only perceive about 10 million colors. and with 24bit (aka 32bit in windows) has over 16 million colors. I don't see the point to going to 40bit in color, sure some graphic cars supports it but the human eye cant see it. Most of these colors must fall out of spectrum we can see, like ultraviolet and infrared.

---

### Post by saulgoode on 2009-09-18
xlib supports 16-bits per color channel in the DirectColor and TrueColor modes.

---

### Post by moster on 2009-09-18
And we have to wait for windows 7 for that. Nobody else can pull that off but M$. I guess they worked on that incredibly hard :D

---

### Post by nmccrina on 2009-09-18
Aren't some of the excess bits used for alpha channels and stuff? I mean, instead of just defining colours we can't see, do the 32+ bit colour schemes store meta information about the display?

---

