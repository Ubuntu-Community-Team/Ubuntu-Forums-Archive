---
title: "[IDEA] better hotkey consistency"
date: 2008-02-02
forum: Ubuntu Brainstorm
---

### Post by pytheas22 on 2008-02-02
In most cases, pressing control-q in an Ubuntu application will terminate it, and control-w will close the active window of an application.  There are some important exceptions, however; for example:

1. Firefox does not close with control-q, only alt-f4.  Control-w will also close it if only one tab is open.

2. The tracker search window can only be closed with escape; other hotkeys do nothing.

3. Nautilus windows can be closed with control-w, but not control-q.

This can be frustrating, because thinking about which hotkey to use to close a certain application requires an additional cognitive step.  It's minimal, but it adds up.

I think that Ubuntu could become more user-friendly if the rules for hotkeys were made more consistent: control-q should ALWAYS terminate an application, and control-w should ALWAYS close the active window of an application.  Furthermore, if there's only one active window and closing it would mean terminating the application, then that should happen...e.g. when I only have one document open in OpenOffice and I press control-w, the application should close entirely, not remain open without any active documents.  Same with gedit.  Or I guess this could go the other way, too, as long as the behavior is consistent between applications.

Better consistency with hotkeys for other functions would be useful as well.  Control-t vs. control-n, for instance, is another source of cognitive waste: in gedit control-n gives me a new tab, but in Firefox or OO I get a new window.

I imagine that hotkey policies are set in the code of an application itself, not by the desktop environment.  But it shouldn't be too hard to have Gnome (or KDE, although I can't speak for it because I haven't used it in years) override application-specific policies, should it?  Users can already customize hotkeys extensively with the "keyboard shortcuts" applet.  Couldn't this be extended to provide better consistency throughout Ubuntu?

---

