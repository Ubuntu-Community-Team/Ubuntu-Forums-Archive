---
title: "Gthumb will not stay maximized"
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by x-shaney-x on 2012-03-17
In my efforts to find a decent gnome based photo manager I'm trying Gthumb.

Already hit a snag in that every time I launch it, I have to maximize before I start.
All other apps start up in the state I closed them.
If I close a maximized app it always opens maximized but not Gthumb.

<EDIT>

Also noticed that it never shows as running in the launcher.  The icon pulsates and the window opens but no pips to indicate it is running.

---

### Post by mc4man on 2012-03-17
If you added to launcher by running, then locking, or dragging from Dash -  try dragging instead from either /usr/share/applications or if that doesn't work the cp the gthumb.desktop to ~/.local/share/applications & drag from there

*i'd remove from launcher, log out/in, then do the DnD

Doesn't seem to like opening maxed but you could resize to almost maxed, then it would remember
(whether a fix there don't know

---

### Post by x-shaney-x on 2012-03-17
The launcher problem is gone, turned out there was an instance running (or hadn't closed properly).  Working normally now.

If I resize the window to almost maximized then it does re-open to that size but still will not open maximized.
It turns out it does it in Oneiric so this isn't a Precise issue after all.

Not good enough really and wasting space.
Not only that, when viewing photos it has "SAMSUNG DIGITAL CAMERA" in front of all tags on any photos taken with that camera and can't find a way to remove it.

Gthumb is off the menu.  Keep looking...

---

### Post by Gregory Lee on 2012-03-17
I'd consider DigiKam a candidate, along with Gthumb and Shotwell.  I've tried these 3 out, only briefly so far.  I used DigiKam on my last system (Fedora 6) and liked it.  Here on 12.04, my one attempt to upload pics from my Nikon using DigiKam crashed Ubuntu, but I saw that DigiKam was updated, so I can hope that this has been fixed.

---

### Post by x-shaney-x on 2012-03-17
I have been using Digikam for a long time in KDE/Kubuntu.
It's good but has some bugs and issues and I want to move away fro it really.
Plus, I am switching over to ubuntu and want a gnome-based organizer.
I could just use digikam in ubuntu but it looks out of place so I have to install KDE system settings to alter the fonts and theme/icons and I have found it a bit dodgy importing in gnome.

Shotwell is ok but forces the user to work IT'S way.
It cannot maintain a folder based album structure.

---

### Post by x-shaney-x on 2012-03-17
Hmm, turns out Gthumb is actually pretty decent in a lot of ways.
I finally worked out to get rid of the "SAMSUNG" label and I have discovered it DOES maximize normally in Unity 2D, just not in 3D.

---

