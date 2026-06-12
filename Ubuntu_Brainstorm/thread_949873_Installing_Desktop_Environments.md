---
title: "Installing Desktop Environments"
date: 2008-10-16
forum: Ubuntu Brainstorm
---

### Post by crisspybeers on 2008-10-16
I don't know if it has been brought up before (couldn't find anything when I searched this forum) but I was thinking, I have played around with a lot of different Window managers/GUIs and it can be a real pain to find all the right files and such to make them work good and look pretty.  Is there any way to have in the Add/Remove Programs or the repositories the window manager, file manager, toolbars, etc for a specific GUI in one group.  For example, if I wanted to try Openbox, then I could go Add/Remove Programs, scroll down to GUIs or search for Openbox and instead of just getting Openbox, it would have a default group of items to get the full experience up and running (say Thunar, AWN, Tint, etc).  Don't know how hard it would be but it would be cool.  Just a thought.

---

### Post by aysiu on 2008-10-16
I think what you're asking for a metapackage.

Such metapackages already exist for desktop environments (*ubuntu-desktop* for Gnome, *kubuntu-desktop* for KDE, and *xubuntu-desktop* for Xfce).

I suspect they don't exist for window managers (Openbox, Fluxbox, IceWM, Sawfish, Enlightenment) for this reason: most people who use window managers want something lightweight and customized. There is no standard for window managers. Some people will run Openbox with Thunar. Others might run it with Rox-Filer... or even Nautilus... or no graphical file manager at all.

In Gnome, Xfce, and KDE, there are default applications that go with the desktop environments. In window managers, there are no default applications that go with them.

---

### Post by Anzan on 2008-10-16
A search in Synaptic for Openbox or Fluxbox will pull up packages which are associated with either. As for file manager and other tools one needs to read around the web (or this forum).

---

