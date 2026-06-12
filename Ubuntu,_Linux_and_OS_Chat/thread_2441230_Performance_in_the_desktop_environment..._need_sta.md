---
title: "Performance in the desktop environment... need stats..."
date: 2020-04-21
forum: Ubuntu, Linux and OS Chat
---

### Post by pelagatus on 2020-04-21
hey guys, I saw somewhere a chart with a graph showing the performance and resource usage of each desktop environment, unfortunately it was kinda dated and I lost the link in a reinstall... 

Anyone around know about the a place with such performance metrics and stats.... or at least a way to install desktop environments without the clutter that usually comes with them... I tried Cinnamon over Ubuntu gnome and I had to get rid of all the clutter that Cinnamon put into the computer...

Thanks...

---

### Post by wildmanne39 on 2020-04-21
Hello and welcome to the forum.

*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by Hwæt on 2020-04-21
I think that the best gauge of performance for your hardware is going to be to give it a quick install and test run in a far-flung partition on your system. What runs well on my system and what runs well on your system are going to be two totally different things benchmarks can't help you for. Especially when you get to the marginal category of the *boxes.

These days the popular pick is XFCE. I've heard things about MATE but I'm skeptical. Mainly because I remember the criticisms against the, then bloated GNOME 2, which MATE is a fork of.

I would expect cinnamon to be not so performant for the fact it derives from GNOME 3.

---

### Post by CatKiller on 2020-04-21
> **pelagatus said:**
> I tried Cinnamon over Ubuntu gnome and I had to get rid of all the clutter that Cinnamon put into the computer.

I think that you don't really understand what a desktop environment is. *Of course* a desktop environment comes with a file browser, a text editor, a terminal application, a media player, and so on. No, they aren't going to be the same ones that a different desktop environment uses. Conversely, if you install a new text editor, file browser, and so on, you'd want it to be available in your desktop environment. Having lots of different similar applications installed has absolutely no impact on resource usage, except that they're stored somewhere on your hard drive.

Which desktop environment you use makes no difference to performance unless you're ludicrously hardware-constrained. Differences in which websites you visit will completely dwarf any differences in which desktop environment you use. If you're doing the same things, you'll use the same resources. It just doesn't really matter if your window manager uses 300 MB vs 400 MB of RAM on any machine that's actually being used for stuff. 

Gnome 3 performed badly because of *bugs*, not "bloat." The same with the (long gone) KDE4.

If you want to compare performance in the different desktop environments the easiest way is to run the live images from USB. None of them will run as fast as if you installed them directly on your hardware because they'll be slowed down by the USB interface, but they'll all be slowed down by the same amount. Run your benchmarks and do your normal workflow and compare the results. They'll all perform about the same. Then install whichever one you like using most.

---

