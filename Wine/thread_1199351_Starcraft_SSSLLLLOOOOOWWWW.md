---
title: "Starcraft SSSLLLLOOOOOWWWW"
date: 2009-06-28
forum: Wine
---

### Post by masonstanley on 2009-06-28
Hi guys I am running Ubuntu 9.04 and I have been playing Starcraft on Windows OSes for quite some time. When I go to install Starcraft It will install with no problems but playing it is slow as hell can anyone help me?

---

### Post by Sef on 2009-06-29
Moved to WINE.

---

### Post by Th3_uN1Qu3 on 2009-07-02
Starcraft is old enough to be played without hitches in a virtual machine. Better try that. Install VirtualBox and XP inside it, and have fun. Worms Armageddon works very well like this, and i couldn't get it to run in Wine.

---

### Post by snakt on 2009-07-02
This page may give you a hint to whats wrong [http://appdb.winehq.org/objectManager.php?sClass=application&iId=72]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=72")

Otherwise running via a VirtualBox sounds like a good idea.

---

### Post by Th3_uN1Qu3 on 2009-07-02
Well the reviews say they haven't tested the missions, which pretty much says by itself that it wasn't tested at all. :lol: The Wine AppDB is rarely any help.

---

### Post by del_diablo on 2009-07-02
I dunno, but Starcraft works great for me.
Movies play, missions work, but there are several minimal bugs(killing it in fullscreen freaks out your screen resolution, which is only fixable by reboot. In windowed the killer bug is that sometimes when using the mouse to change your view instead of the keyboard it starts automoving itself, which is fixed by a reload(save & load).
Have not tested battle.net however.

---

### Post by elitenoobboy on 2009-07-04
> **del_diablo said:**
> (killing it in fullscreen freaks out your screen resolution, which is only fixable by reboot. In windowed the killer bug is that sometimes when using the mouse to change your view instead of the keyboard it starts automoving itself, which is fixed by a reload(save & load).

If you use nvidia, you can go to system>administration>nvidia server settings and reset your resolutions there. Otherwise restart your graphical x session, so you won't have to reboot and lose everything.
And for windowed, I consider the killer bug to be that the window is too small to use. It takes up less than a fifth of the screen space on my monitor.


As for original poster, I would follow snakt's advice and go to the wine appdb starcraft page. Then go to the broodwar 1.x page. There you will find instruction about 2 keys that will need to be added to wine's registry. That fixed the slowness for me.

---

### Post by dimoftheyard on 2009-07-25
Which graphics driver are you using? With the default driver for my nvidia card (which is nv) starcraft was terribly slow. But using the closed source nvidia driver everything works. Even correctly scaled fullscreen, which was another issue before.

---

### Post by NightMKoder on 2009-07-25
> **Th3_uN1Qu3 said:**
> Well the reviews say they haven't tested the missions, which pretty much says by itself that it wasn't tested at all. :lol: The Wine AppDB is rarely any help.

Um, actually that usually means that they tested battle.net. Appdb is actually full of useful information, and it would be great to see people read it more often.

For example, if you read the comments on the starcraft page, you will find that slowness is usually due to bug 421.

---

### Post by thekronisk on 2010-01-14
Hi guys.

I was very pleased earlier today, when I discovered a fix for the slow starcraft. It's not one of those small fixes like change something in the regedit and gain ~5fps more.. Nope, it's a whole other thing..

You need a very old version of wine to get StarCraft to play as smooth as on XP. I use wine 0.9.14 and it's 99% of what I remember it being from XP. I found, that the easiest way to go about having a very very old wine version and a new one (for newer applications than sc), you'll need the program PlayOnLinux (google, GO)

With PlayOnLinux you can add a wineversion in a matter of seconds, and then create a launcher (in bash) that uses this old wine version compiled and installed by PlayOnLinux in less than a minute. For instance my loader for Brood War looks like this:

```

#!/bin/bash

/home/kronisk/.PlayOnLinux/WineVersions/0.9.13/usr/bin/wine c:/games/bw/StarCraft.exe

```

Anyways, this is the fix I've been searching for in ages -- Try it out and please spread the message!

Cheers!


thekronisk

---

