---
title: "Steam Box OS: Display Server?"
date: 2013-09-11
forum: Ubuntu, Linux and OS Chat
---

### Post by King Dude on 2013-09-11
There's a lot of talk over [display servers]("http://en.wikipedia.org/wiki/Display_server"), such as [Mir]("https://wiki.ubuntu.com/Mir"), [Wayland]("http://wayland.freedesktop.org/"), [X.org]("http://www.x.org/wiki/"), and some others. So I'd like to ask the question, what display server will Valve choose for their Steam Box Operating System?

Any opinions are welcome, but try to back your opinions with facts and references.

---

### Post by codingman on 2013-09-11
My guess is on Wayland, due to the fact that X.org is buggy, and there is no clue as to what Mir will be, the best choice would probably be Wayland, especially with Linux moving on from X.org.

---

### Post by King Dude on 2013-09-11
But Valve's favorite Linux distro is Ubuntu, so wouldn't they be more willing to use Mir?

---

### Post by codingman on 2013-09-11
It all really depends on what happens to Mir, but if it turns out to be good, well then, it's a no-brainer!

---

### Post by King Dude on 2013-09-11
I suppose. But if Valve does not choose Mir, wouldn't it be difficult to put the game on Ubuntu?

---

### Post by mastablasta on 2013-09-12
it will be difficult anyway if the AMD/nvidia won't support it. i mean you need descent hardware drivers first.

---

### Post by ZoiaGuyver on 2013-09-12
Hopefully the drivers will support both Wayland and Mir due to the use of OpenGL. The way the game engine works is also a big factor, aslong as Wayland and Mir can do as they are told by creating a window for the game the actual display manager shouldn't be a problem. The "desktop" for the Steambox / SteamOS whatever you wan't to call it is probably going to be the "Bigscreen" mode.

Mir can also be used as the compositor for Wayland providing someone writes the code for it to be used that way. A company like Valve definitely have the manpower and the tech experience to do that, maybe a Mir+Wayland Big Picture mode.

But I think the argument for AMD/Nvidia will not be whether to support Wayland or Mir, but how to get the most money out of it. 

At the end of the day we are still very early on, NV and AMD are not ones to act pre-emptively they always seem to act a long time after. 

Lets try to be optimistic that they will decide it is in their best interests to support both.

---

### Post by ssam on 2013-09-12
I imagine that they'll play it safe and stick with Xorg, at least to start with. X has easily done 100 million user years of work so it will be a while before anything else reaches that stability.

Will it even have a window manager, or will it load straight into stream and run everything full screen?

---

### Post by King Dude on 2013-09-12
I like the idea of Mir+Wayland. By the way, can anyone tell me what Weston is? I've heard it a few times alongside Wayland and have been wondering what it refers to.

---

### Post by Beren Camlost on 2013-09-12
Weston is a reference compositor for Wayland.

---

### Post by King Dude on 2013-09-12
What's a reference compositor and why is it needed?

---

### Post by ZoiaGuyver on 2013-09-12
What Beren Camlost says is correct, Weston is the reference implementation of Waylands Compositor. The compositor is basically the part that throws stuff on the screen. Its what places the windows and controls them. Wayland is like the engine for that, it tells the compositor how and where/when to put them there.

To put it a little easier, When Gnome and KDE get full Wayland support, they will in turn replace Weston i.e Gnome becomes the compositor for Wayland, KDE becomes the compositor for Wayland. 

The problem with the explanations of each of the "display managers" really has been lacking and have used way to many ifs/buts.

Mir is basically the Unity engine kind of thing, If they had not created Mir or created it differently, it would be the compositor for Unity on Wayland.

I hope that explains it a little more understandably. Both projects have a lot of similarity's but they do different things, while also doing the same, hence the whole "duplicating work" stuff.

---

### Post by codingman on 2013-09-12
That's a valid point ssam: If Valve is to put the games on other distributions, wouldn't it be sort of hard to have to downgrade?

I'm pretty sure Mir and Wayland have the ability to work with X, right? (Please correct me if i'm wrong!)

---

### Post by ZoiaGuyver on 2013-09-13
codingman Well they do and they dont, the way things work at the moment are totally different to the way Wayland and Mir work.

At the moment you have X.org Input > X.org display Server > Compositor >  Window > Compositor (if effects are in use) > Program > X.org display server > Screen

Thats kinda the problem (although its really simplified), everything is having to make a round trip back to the X.org server to be able to display. With Wayland and Mir, because they skip all of the X.org round trip they go as I posted before.

So In a sense, Mir "could" act as the compositor ontop of X.org (which is kinda what Xmir does but rather than run ontop it reverses it to Mir > Xmir/X.org > Screen), Wayland has the same (its compositor be in gnome or kde) could act as the compositor for X.org. 

What both projects aim for are around the same target, Wayland aims to remove all the cruft and give it a direct Server >< Client > Screen the client deals with any changes the "server" isn't really a server, its just a library. Mir does things almost the same way but slightly differently as the server basically doesn't hand off so in theory is something like Mir/Unity > Screen. 

Those are over simplifications. Both Wayland and Mir can and do work with X.org but in a different way. If you look at how I layed it out for X.org the current implementation of Wayland and Mir is Wayland/Mir >XWayland/XMir > Screen.

---

### Post by codingman on 2013-09-15
Thanks for clarifying that for me, ZoiaGuvyer.

---

