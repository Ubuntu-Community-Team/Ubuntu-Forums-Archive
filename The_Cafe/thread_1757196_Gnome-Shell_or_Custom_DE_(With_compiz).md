---
title: "Gnome-Shell or Custom DE (With compiz)"
date: 2011-05-13
forum: The Cafe
---

### Post by Vapourstreak on 2011-05-13
I'm torn between installing Gnome Shell on the Arch linux, or just creating my own custom one using Compiz as a WM.  I've done the compiz thing a few months ago, and it worked well enough for me to use, but I would like to try Gnome Shell.  The only thing stopping me is, is there a lot of bloat?  I'm installing Arch on a 16GB usb stick, so which one would be a better choice?

Also, do I need to install X for Gnome Shell too?  And is it themeable?

Thanks,
Vapour

---

### Post by 3Miro on 2011-05-13
All graphics require X (Gnome, KDE, ...)

For Gnome-shell you need to install Gnome3. It will be more than just a compiz standalone DE.

You should try to install Gnome-shell somewhere to just try it. It is very different and some people like it, while some people don't.

---

### Post by Vapourstreak on 2011-05-13
Wait so Shell would be a lot bigger on the disk?  How big by your estimation?

---

### Post by 3Miro on 2011-05-13
> **Vapourstreak said:**
> Wait so Shell would be a lot bigger on the disk?  How big by your estimation?

Installing Gnome-shell is equivalent to installing full Gnome3. I don't think GS can run without Gnome (i.e. it is not a standalone WM). I haven't played much with Gnome3, but it will be no smaller than Gnome2 (which is much bigger than XFCE or LXDE, which a bigger than standalone WM).

A guesstimate is minimum 300MB of HDD space for Gnome-shell. I don't know much about standalone compiz and what else you want to install with it, but my guess would be 100MB for that.

---

### Post by Vapourstreak on 2011-05-14
Would the 300mb include gnome and gnome shell together?  How about all the applications that come with gnome?

---

### Post by LarsKongo on 2011-05-14
I installed Gnome 3 on Arch in a virtual machine yesterday. When you 'pacman -S gnome' you'll get a couple of choices that you can install. For the best experience it's recommended to select all. However, I didn't select gnome-backgrounds, epiphany and 1 or 2 other things which I don't remember what it was called. Everything landed on around 500-800MB. About 1GB if you install more apps I suppose.

The end result however was fallback mode because VirtualBox doesn't support gnome-shell yet. Customizing Gnome 3 is hard but not that hard if you know what to look for. ALT+F2 and run dconf-editor to get a nice selection of things to customize. It's still a bit limited though. (Managed to remove one fallback panel and move some applets to the bottom one for example.)

---

### Post by NormanFLinux on 2011-05-14
Ubuntu distros will have to remake GNOME 3 into a 2D version so it can run on all hardware.

I don't being told I must buy an accelerated graphics card to get the most use of my OS.

Let's hope every one else is listening!

---

### Post by Vapourstreak on 2011-05-14
Oh okay, just wondering, how do you skip installing packages in pacman?

---

