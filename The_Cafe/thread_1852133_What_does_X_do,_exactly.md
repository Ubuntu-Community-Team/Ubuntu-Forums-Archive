---
title: "What does X do, exactly?"
date: 2011-09-29
forum: The Cafe
---

### Post by ninjaaron on 2011-09-29
As far as I can tell, X does everything and nothing.  It draws stuff, I guess.  I doesn't actually do windows or rendering or anything like that... thost are handled elsewhere, and then X draws them or something.

But then it's all tied up with input and keyboard mapping and dbus and whatever.  Your touchpad or touchscreen isn't going to be to be doing anything without X, that's for sure.

And it's, like, a dependency for everything except "ls" and whatever.

And when you try to configure stuff (espeically keyboard stuff, which I've done more of than I care to talk about) it's really complex and crufty.  One of the current heads at X.org was talking about how it looks like it was designed by someone on drugs.  X is like a some kind of insane micro-kernel unto itself.

So, what was X originally supposed to be,  What is X today,  and when do we get to dump this weird crufty system for Wayland or something that isn't terminally handycrapped by a legacy of feature creep?

---

### Post by TeoBigusGeekus on 2011-09-29
[This]("http://wayland.freedesktop.org/architecture.html") article could be of help.

---

### Post by el_koraco on 2011-09-29
It's one of those questions, like what is the full relationship of dpkg and apt, and aptitude, or what's the correct pronounciation of YHVH.

---

### Post by ninjaaron on 2011-09-29
Oh lord.  It's worse than I thought.

---

### Post by ninjaaron on 2011-09-29
> **el_koraco said:**
> It's one of those questions, like what is the full relationship of dpkg and apt, and aptitude, or what's the correct pronounciation of YHVH.

I can actually offer an informed and profession opinion on the last of those questions, as Hebrew and semitic linguistics is my area of specialization, if anyone is ready for a real humdinger.  A personal friend of mine is writing his PhD. on that very topic at the moment.

/facepalm @myself

---

### Post by Copper Bezel on 2011-09-29
Oh dear, someone mentioned Wayland again. Can someone reassure me that the world will not end in fire and client-side windecs?

---

### Post by KiwiNZ on 2011-09-29
Marks the spot :p

---

### Post by tgalati4 on 2011-09-29
In before the close.  X has been around a long time, since 1982 I believe.  It was supposed to be better than the "W" window system that eventually became Windows.  It ran on Unix workstations and it's core capabilities have not changed since them (such as the ability to share a mouse or run multiple mice and keyboards, run remote desktops, multi-user X-sessions--the list is quite extensive.  If you wanted buttons and graphical widgets, you used the Motif widget system.  That gave you open and close buttons and there were several window managers to choose from.  Most looked like simple versions of OpenBox.

So although I agree that it's probably time for a replacement, it would be hard to replace the quirky goodness that we call X.

---

### Post by nothingspecial on 2011-09-30
I don't know, but who needs it?

[ATTACH]203196[/ATTACH]

---

### Post by el_koraco on 2011-09-30
> **ninjaaron said:**
> I can actually offer an informed and profession opinion on the last of those questions, as Hebrew and semitic linguistics is my area of specialization, if anyone is ready for a real humdinger.  A personal friend of mine is writing his PhD. on that very topic at the moment.

/facepalm @myself

Yeah, but tell it to the Witnesses!

---

### Post by prodigy_ on 2011-09-30
> **ninjaaron said:**
> As far as I can tell, X does everything and nothing.  It draws stuff, I guess.  I doesn't actually do windows or rendering or anything like that... thost are handled elsewhere, and then X draws them or something.

I think you're confusing DE (desktop environment) with HAL (hardware abstraction layer). Gnome is a typical DE, X Window System is a part of HAL. X is actually quite remarkable because it uses the client-server model and has a network protocol. Which means, as you probably guessed, that you don't need a desktop sharing application to get a remote GUI for a system that runs X.

---

### Post by ninjaaron on 2011-09-30
> **nothingspecial said:**
> I don't know, but who needs it?

[ATTACH]203196[/ATTACH]

OH MY WORD

How, perchance, are you doing that?

---

### Post by Copper Bezel on 2011-09-30
> **prodigy_ said:**
> I think you're confusing DE (desktop environment) with HAL (hardware abstraction layer). Gnome is a typical DE, X Window System is a part of HAL. X is actually quite remarkable because it uses the client-server model and has a network protocol. Which means, as you probably guessed, that you don't need a desktop sharing application to get a remote GUI for a system that runs X.

Yeah, I think of it as the thing that it provides the layer of abstraction that makes *nix GUIs *nixy. But I guess Android gets along swimmingly enough without it.

---

### Post by nothingspecial on 2011-09-30
> **ninjaaron said:**
> OH MY WORD

How, perchance, are you doing that?

With the framebuffer :D

---

### Post by ninjaaron on 2011-09-30
> **nothingspecial said:**
> With the framebuffer :D

I need to do some reading.  About this and screen... and other wonderful things like that...

---

### Post by nothingspecial on 2011-10-01
Most applications that can use the framebuffer do not work with terminal multiplexers such as screen. Recent versions of mplayer do :).

But fbgrab which I used to take the screenshot do not.

---

### Post by jwbrase on 2011-10-01
> **nothingspecial said:**
> Most applications that can use the framebuffer do not work with terminal multiplexers such as screen. Recent versions of mplayer do :).

But fbgrab which I used to take the screenshot do not.

Also, Ubuntu (10.04) seems to have default settings that framebuffer programs can't deal with. I get a "can only handle packed pixel framebuffers" error when I try to run anything like fbi. And the results of cat-ing data to /dev/fb0 seem to indicate a monochrome 1 bpp framebuffer (catting a single character writes multiple pixels to the screen, and always in black and white), which would also seem to indicate that further configuration needs to be done. (Of course, I know next to nothing about the framebuffer, so my interpretation here may be totally messed up).

---

