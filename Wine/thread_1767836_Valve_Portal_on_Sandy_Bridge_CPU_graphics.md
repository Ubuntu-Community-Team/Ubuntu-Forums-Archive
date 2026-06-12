---
title: "Valve Portal on Sandy Bridge CPU graphics"
date: 2011-05-26
forum: Wine
---

### Post by no.human.being on 2011-05-26
Hello Ubuntu forums,

I'm trying to run Valve's "Portal" (the original one, not "Portal 2") on a Lenovo Thinkpad T420 notebook with an Intel Core i3 2310m processor and Ubuntu 11.04 installed. The CPU features integrated processor graphics called Intel HD Graphics 3000. The "i915" kernel module seems to be used for the processor graphics. I'm running on a classic GNOME environment, no Unity, no Compiz.

I've installed the Steam client from Valve under wine-1.3.20 from the "http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu" repository. It's simulating a "Windows 2008 R2" environment.

Almost every game in my library is running fine. This includes all HL1-Engine based games, as well as "Half-Life 2: Lost Coast".

"Half-Life 2: Deathmatch" is running without too many glitches as well, but crashes every now and then.

However, I'm experiencing great problems running "Portal". I'm supplying the following parameters (if I don't supply them, X11 will completely lock up and I will have to shut the system down using magic SysRq sequence).

"-window -width 1024 -height 768"

This will let me run Portal, but there are serious graphical glitches in game, extreme black flicker on the screen and incorrect polygons everywhere. The entire desktop even flickers every now and then. Some objects (e. g. the light cone from the lamp in the opening chamber, some textures, etc.) are missing and after some minutes, the game just locks up.

If I disable hardware accelleration and let it run on the Mesa3D software renderer, there are no graphical glitches, so it seems to be a problem with the processor graphics driver, not with Wine compatibility. The game is running exceptionally slow when rendered by Mesa3D, so that's no real alternative. It was just used for demonstration purposes.

Just compare the following screenshots, which were both taken on the same computer with the same Wine version. One uses the Intel HD Graphics, the other uses the Mesa3D software renderer.

[Portal on Intel HD Graphics]("http://img109.imageshack.us/i/portalhdgraphics.png/")

[Portal on Mesa3D renderer]("http://img854.imageshack.us/i/portalmesa3d.png/")

Is there any way to get this running or it it just that the Intel HD Graphics drivers are still THAT bad and we'll just have to wait until they improve?

---

### Post by mips on 2011-05-27
You could try the latest driver from [http://intellinuxgraphics.org/2011Q1.html](http://intellinuxgraphics.org/2011Q1.html)
[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

---

### Post by no.human.being on 2011-05-27
Added the "xorg-edgers" repository and started a system update. Several packages were updated to the version of the "edgers" repo, but I don't notice any change in the behaviour of the system. I'm gonna remove the repository from the package sources and "downgrade" the packages back to their "original" versions.

---

