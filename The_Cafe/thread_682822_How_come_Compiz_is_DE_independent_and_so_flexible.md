---
title: "How come Compiz is DE independent and so flexible?"
date: 2008-01-30
forum: The Cafe
---

### Post by Ebuntor on 2008-01-30
Hi everyone,

As I understand it Compiz is desktop environment (DE) independent and  can function on just about every Unix-like OS. (that is what I have read so please correct me if I'm making wrong assumptions)

I was wondering how it is possible that Compiz is so flexible? Every DE is different yet somehow this isn't a problem for Compiz.  
I'll give and example, there's the "magic lamp" effect, for those who are not familiar with it it makes your windows get sucked to their position on the window list on the task bar when you minimize or close them. This works on Gnome, KDE, Xfce etc. (at least so I've heard)
How does Compiz "know" or "see" that that particular window belongs to that place on the taskbar? And how can it "figure out" this on different DE's?  

Heck I can even install a dock like AWN and Compiz will still "see" the windows on the dock and "know" which icon belongs to which window.

Unless I'm missing something Compiz seems like one amazing program.
Could someone explain how this works?

---

### Post by FuturePilot on 2008-01-30
In your example of the Magic Lamp effect I don't think it all has to do with Compiz. Part of it has to do with the standards. Kicker and Gnome Panel both comply with the [EWMH]("http://standards.freedesktop.org/wm-spec/wm-spec-1.3.html#id2456758") standard. So therefore the Compiz developers just have to know how to code Compiz to interact with that standard.

---

### Post by igknighted on 2008-01-30
Compiz actually replaces parts of the DE.  In gnome, metacity handles all the window manager tasks (and in KDE it's kwin), and Compiz simply replaces them.  Compiz-core really doesn't interact with any DE, it replaces it.

If you notice when you install, there is a compiz-gnome or compiz-kde package that includes all the files that do interact with the particular DE (like adding the compiz settings to gconf).

As for the icons, that is done at the application level i believe.  Think about it, if you open Gedit in KDE, there's still a gedit icon on the kde taskbar.  The application just knows where its icon is and reports it.

---

### Post by Ebuntor on 2008-01-30
> **igknighted said:**
> Compiz actually replaces parts of the DE.  In gnome, metacity handles all the window manager tasks (and in KDE it's kwin), and Compiz simply replaces them.  Compiz-core really doesn't interact with any DE, it replaces it.

If you notice when you install, there is a compiz-gnome or compiz-kde package that includes all the files that do interact with the particular DE (like adding the compiz settings to gconf).

As for the icons, that is done at the application level i believe.  Think about it, if you open Gedit in KDE, there's still a gedit icon on the kde taskbar.  The application just knows where its icon is and reports it.

Ah, I see, that explains a lot. I was under the impression that you could just install it on any DE but there have to be specific package for each DE.

Metacity handles all the window manager tasks? I though it's simply for the window decoration, like Emerald.

Thanks :)

---

### Post by macogw on 2008-01-31
Splitting up window managing and decorating into two separate apps is actually just a weird Compiz-ism, as far as I know.  Everything else puts the two together.  Definitely no way to separate it in Fluxbox.

---

