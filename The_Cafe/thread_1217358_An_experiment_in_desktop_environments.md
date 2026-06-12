---
title: "An experiment in desktop environments"
date: 2009-07-19
forum: The Cafe
---

### Post by decoherence on 2009-07-19
I've always been a fan of hodge-podge desktops of simple panels and window managers and menu programs thrown together.

My latest effort is to put together a functional system using, as much as possible, only Qt4-native graphical programs. Specifically, I do not want any KDE loaded. In fact, I will prefer gtk2 over KDE (and GNOME is also right out) in situations where there is no Qt4 native app available. It's currently based on a Jaunty install with GNOME ripped out but I figure the reference oughta be a Karmic server install with the desktop kernel (and no servers.) Since I'm still just playing around and karmic isn't even stable yet, I'll just update this system to Karmic rather than do a fresh Karmic server install.

The list of components/potential components --

current--
desktop: [Antico]("http://www.qt-apps.org/content/show.php?content=93778")
web browser: [Arora]("http://code.google.com/p/arora/")
connection manager: wicd

potential--
maybe replace antico with [Antico-Deluxe]("http://www.qt-apps.org/content/show.php/Antico+Deluxe?content=95422")
replace wicd with [NUT]("http://redmine.stbuehler.de/projects/show/nut")  (provided i386 .deb package requires later Qt than what is in Jaunty -- UPDATE: NUT is seriously lacking in documentation. Sticking with wicd for now.)

method-- go through the top rated programs at qt-apps.org, ask "does this have a counterpart in the default ubuntu desktop?" if so, download or make a .deb and see if the program doesn't suck!

Arora is a nice WebKit-based browser. It's not a Firefox killer, but it is solid and has some modern features like privacy mode. One funny thing about libqt4-webkit, though, is that it depends on libgtk-2.0.

Antico is potentially a really nice desktop... however the main developer seems to have given up on it and it currently has some issues with window focus that make is a bit annoying to use. I'm going to test out antico-deluxe next.

One compromise I currently have to make is to run the (gtk2-based) wicd network manager, but seeing as libqt4-webkit already brings in gtk2, I'm not too fussed about that yet. NUT is a potential alternate that can eliminate the gtk2 dep, provided the webkit library stops relying on it (i think this has to do with gstreamer?)

Anyway, I'll continue to add Qt4 programs and test alternatives and update this post. If I come up with something usable, I'll do up a PPA (since none of this stuff is in the repo.)

If anyone knows of a similar project, please let me know!

UPDATE: I found [http://code.google.com/p/qtdesktop]("http://code.google.com/p/qtdesktop/"), let's give that a try!

---

