---
title: "Gnome 2.10 window shadows? what?"
date: 2005-06-11
forum: The Cafe
---

### Post by GTKpower on 2005-06-11
What's with all the window and menu-shadowing in various reviews of GNOME 2.10?

For example:

- The Gnome 2.10 release notes section at Gnome.org

-and here as well:  [http://www.gnomejournal.org/article/17/gnome-210-desktop-and-development-platform](http://www.gnomejournal.org/article/17/gnome-210-desktop-and-development-platform)

Is this some deliberate Photoshop/GIMP effect?  I know there is a way to enable such shadows in Gnome 2.10, but from what I've been reading, it's a pain to get it going, and might be brutally slow anyway.

Any thoughts?

---

### Post by tread on 2005-06-11
As far as I know, gnome doesn't have menu shadows yet .. the only way to do that is using xcompmgr, which does require a fair bit of perf. I can use it with opengl enabled on xorg, but even then its a bit slow.

---

### Post by GTKpower on 2005-06-11
Hmmm . . .   I've got Xorg running.

I've got an ATI Radeon 8500 128mb.

CPU is an Athlon 3000+.

Not sure what the support for ATI is like, but will my desktop be able to handle shadows?

---

### Post by Poul on 2005-06-12
it  should be

---

### Post by Rickie on 2005-06-12
Might sound like a bit of a noob here, but why is shadows on Gnome so taxing on the system? There are app's on windows that add shadows everywhere (WindowFX 2, for example) Without noticably slow down the system (IMO), and these app's aren't even native - why are they so much trouble on Linux? :(

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=Rickie]Might sound like a bit of a noob here, but why is shadows on Gnome so taxing on the system? [/QUOTE]

Because its the brand newest stuff. Xcompmgr is nice (I like fading more than drop shawdows) but its very crashy. With a Nvidia FX card or better (on the Nvidia side) its actually really smooth because Nvidia cares about it working.

---

### Post by mike998 on 2005-06-13
I've got a video card that isn't really top of the line and am hoping that when these features get released, I can turn them off.

Gnome is so lightweight, I don't really like XFCE, but if these whizz-bang features keep on getting added, I may have to go to XFCE...

---

### Post by drummer on 2005-06-13
Enlightenment17 has window shadows as default, no opengl drivers or xcompmgr required. How does it do that and could that be done in gnome? (E17 isn't really usable/stable enough yet for me).

It looks like it's much less taxing on the system and would be great if it or something similar could be integrated into gnome.. ati drivers have proved to difficult for me to set up and so I can't use xcompmgr :(

---

### Post by Stormy Eyes on 2005-06-13
[QUOTE=drummer]Enlightenment17 has window shadows as default, no opengl drivers or xcompmgr required. How does it do that and could that be done in gnome? (E17 isn't really usable/stable enough yet for me).[/QUOTE]

It can't be done in GNOME unless GNOME starts using Rasterman's *Enlightenment Foundation Libraries* for development, which won't happen because GNOME has Cairo and Glitz, whatever they are.

---

### Post by tread on 2005-06-13
Yep, EFL has implemented something similar to Macromedia Flash, but its for desktop purposes. Its pretty nice, but horribly under development .. and cvs builds sometimes don't compile. I hope Cairo develops fast and gets integrated into Gnome faster :) .. drop shadows are so pleasing to the eye. I would rather have them than any other bling!

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=drummer]
It looks like it's much less taxing on the system and would be great if it or something similar could be integrated into gnome.. ati drivers have proved to difficult for me to set up and so I can't use xcompmgr :([/QUOTE]


The ATI drivers don't accerate xcompmgr. 

Soon Gnome will have its own composition manager, so xcompmgr isn't really a "Gnome" feature.

---

### Post by TravisNewman on 2005-06-13
and it should be better than running xcompmgr. KDE has tried to include their own compositing manager-- I say tried because it brings my system to a CRAWL. The one built into XFCE works great, xcompmgr works great for a while (still quirky), but kde needs to work on theirs.

---

