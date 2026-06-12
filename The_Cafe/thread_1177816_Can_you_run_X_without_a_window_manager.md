---
title: "Can you run X without a window manager?"
date: 2009-06-03
forum: The Cafe
---

### Post by Warpnow on 2009-06-03
So, I have an Acer Aspire One, and an idea just hit me. I've been using gnome-do docky for a bit, and I think its all I need on it. Run docky in the bottom of the screen, and have ever launched application full screen, and then switch between them with the docky or alt+tab.

Anyone know the best way to do this?

---

### Post by CJ Master on 2009-06-03
> **Warpnow said:**
> So, I have an Acer Aspire One, and an idea just hit me. I've been using gnome-do docky for a bit, and I think its all I need on it. Run docky in the bottom of the screen, and have ever launched application full screen, and then switch between them with the docky or alt+tab.

Anyone know the best way to do this?

Fresh arch install, install X, run startx. Bam.

...but unfortunantly, GNOME-Do needs compositing.

---

### Post by iTrickU on 2009-06-03
So you want to do something like this:

[http://kde-look.org/content/show.php/Netbook+Plasma+Theme?content=92433](http://kde-look.org/content/show.php/Netbook+Plasma+Theme?content=92433)

---

### Post by CJ Master on 2009-06-03
> **iTrickU said:**
> So you want to do something like this:

[http://kde-look.org/content/show.php/Netbook+Plasma+Theme?content=92433](http://kde-look.org/content/show.php/Netbook+Plasma+Theme?content=92433)

> Can you run X **without a window manager?**

If he didn't care about windows manager, UNR would be perfect for him.

---

### Post by dragos240 on 2009-06-03
> **CJ Master said:**
> If he didn't care about windows manager, UNR would be perfect for him.

**U**buntu **N**etbook **R**emix

---

### Post by monsterstack on 2009-06-03
Openbox is good for this. It's an incredibly simple Windows Manager and almost RAMless when compared to the chunkier desktop environments. You can set options to control how much of the screen applications take up when maximised, so you can leave yourself enough room for panels and docks that don't automagically push everything around a bit.

---

### Post by Warpnow on 2009-06-03
> **CJ Master said:**
> If he didn't care about windows manager, UNR would be perfect for him.

The idea is to maximize real estate on a small screen. UNR seems to make this problem worse.

I was looking into launchbar + openbox, though not crunchbang, for some reason crunbang seems to give me FAR less battery life than a simple command line install with openbox. Roughly half.

The KDE theme is NICE, but also does not address the issue I'm trying to.

---

### Post by monsterstack on 2009-06-03
> **Warpnow said:**
> The idea is to maximize real estate on a small screen. UNR seems to make this problem worse.

I was looking into launchbar + openbox, though not crunchbang, for some reason crunbang seems to give me FAR less battery life than a simple command line install with openbox. Roughly half.

The KDE theme is NICE, but also does not address the issue I'm trying to.

Maybe compare the autostart.sh file in Crunchbang with your personal one in a basic Openbox install. Could be Crunchbang is trying to start some power-hungry processes you don't really need.

---

### Post by albinootje on 2009-06-03
> **Warpnow said:**
>  Anyone know the best way to do this?

You can start X with only an xterm starting or your preferred application. 
The easiest imho is to use "startx" instead of gdm, and then first create a file called ~/.xinitrc

For example :
```

# ~/.xinitrc example
xterm

```

The disadvantage about running no windowmanager is that your applications won't have borders and close-buttons etc. so.. you also can't move or resize them.

---

### Post by iTrickU on 2009-06-03
What is that minimalistic tiling window manager?

---

### Post by Sublime Porte on 2009-06-03
I doubt you want no Window manager. Perhaps a very light one, but it's still best to have some kind of Window manager.

[This site](http://xwinman.org/) lists most Window managers and their various features and advantages, there's some extremely small ones there, which take up almost no resources at all.

> ...but unfortunantly, GNOME-Do needs compositing.

It may work with xcompmgr, which is a very lightweight compositor.

---

### Post by monsterstack on 2009-06-03
> **iTrickU said:**
> What is that minimalistic tiling window manager?

You mean [Ratpoison]("http://www.nongnu.org/ratpoison/") [nongnu.org]? rather horrible in my experience. :P I've seen a few others around, too. A newer one is [qtile]("http://www.qtile.org/"). Extremely simplistic, and still in deep alpha.

---

### Post by monsterstack on 2009-06-03
> **Sublime Porte said:**
> It may work with xcompmgr, which is a very lightweight compositor.

Aye, it did for me on my laptop, and I didn't have any sort of 3d graphics enabled there.

---

### Post by Nythain on 2009-06-03
meh, if you're lookin to slim down that much... just run without X altother... framebuffer and screen is all a man really needs :P

---

### Post by Sublime Porte on 2009-06-03
Just did a little testing.

Gnome-do works without a compositor, but no themes/docky. But works fine with xcompmgr, which is extremely small and lightweight. Just run it with the -n switch from your .xinitrc

---

