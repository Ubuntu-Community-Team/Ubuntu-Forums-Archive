---
title: "(my) Open Source MPRIS Applet- control MPRIS capable players from panel"
date: 2011-09-10
forum: The Cafe
---

### Post by Tal500 on 2011-09-10
MPRIS Applet is a project I'm working on and I would appreciate to hear your reviews!

> MPRIS Applet is a project aims to provide desktop panel applet/plugin allow the user to control MPRIS capable players.

Unlike Panflute Music Applet or Ayatana Sound Menu, special plugin for each player isn't required in order to be compatible with this applet/plugin. Only MPRIS2 support is required from the player.

MPRIS Applet goal is to support Desktop Environments and isn't platform depended. Only UNIX style is required.
Currently supported Desktop Environments are GNOME and Xfce(also basic GTK2 window).It might will be kinda against Canonical because of how I reviewed Ayatana Sound Menu, but I really try to give support, not to make war.

Please tell me what you think!
[Project Home]("http://mprisapplet.sourceforge.net/")
[Ohloh page]("https://www.ohloh.net/p/mprisapplet")
^^ Instructions are there ^^

---

### Post by Quadunit404 on 2011-09-11
You sure you want to support GNOME2? It's EOL currently and the applet system as it exists right now is gonna be different in GNOME 3.2.

---

### Post by Tal500 on 2011-09-11
> **Quadunit404 said:**
> You sure you want to support GNOME2? It's EOL currently and the applet system as it exists right now is gonna be different in GNOME 3.2.
Thanks for your response.
First, I'm not gonna ditch GNOME2, especially meanwhile when part of the gnome users don't wanna ditch GNOME2, because the known reasons and big changes(WM, design, ...).
Isn't my decision is similar to what Canonical do in Unity?(drop GNOME3)
If you've noticed, this applet is built from base libraries so it will be very easy to port the applet for each desktop, no code related to MPRIS or even some GTK doesn't need to be done there.
However, as same as I don't ditch GNOME2 users, I'm whiling to support GNOME3 users. The problem is simple- I don't know how.
I haven't found a manual how to create a new applet(I've heard it's called "extension" in Shell) for Shell, so I'm stuck there... Also, it's wrote in Vala, and there's no binding yet for this.(It can be done in C, but I'm not a good C dev, and I don't know the API...)
I do plan to do support GTK3 after I'll fix some essential things.
If anyone there know how to build it for GNOME3 and want to help, please contact me(NOT VIA THIS FORUM!)
I think, by your comment, that you have GNOME3. Again, I'm sorry I can't help here,
**You can still test this applet in GNOME3 panel in "fallback mode".**

---

### Post by Oxwivi on 2011-09-11
No, Canonical/Ubuntu is not dropping GNOME 3, 11.10 is shipping GNOME 3. What they're dropping however is GNOME Shell, the interface. If you want to support both Unity and GNOME Shell, I suggest you look up Unity's appinidicator API, and whatever GNOME Shell's new architecture is called (I don't know).

---

### Post by Tal500 on 2011-09-12
> **Oxwivi said:**
> No, Canonical/Ubuntu is not dropping GNOME 3, 11.10 is shipping GNOME 3. What they're dropping however is GNOME Shell, the interface. If you want to support both Unity and GNOME Shell, I suggest you look up Unity's appinidicator API, and whatever GNOME Shell's new architecture is called (I don't know).

Just found I can install GNOME Shell without droping my GNOME2 in my Debian machine.
Thanks, I'll try port to gtk3 and understand GNOME3 extension, as soon as MPRIS Applet 0.0.2 would be released.

---

