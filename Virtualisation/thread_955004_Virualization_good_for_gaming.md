---
title: "Virualization good for gaming?"
date: 2008-10-21
forum: Virtualisation
---

### Post by Valok on 2008-10-21
I've been reading up a little bit more on gaming in virtualbox and VMware and from what I've been able to find, the gaming experience is much lower than if you simply booted into Windows on a dual boot system.  I've heard that games run slower, with lower FPS, and just don't look as good.  

Do these have any credit or basis?  Or did I just hear from a few bad apples?

I'm a gamer first and foremost on my computer, so getting the best experience out of them is trump.

---

### Post by tuxxy on 2008-10-21
You heard correctim afraid,  gaming in a virtual environment should be kept to simple games, high spec 3D games will not perform as they should if they do function at all.

Your best with WINE for the more modern games but even then not all are compatible, check WineHQ for a compatibility list.

---

### Post by BloGTK on 2008-10-21
Virtualization doesn't emulate graphics hardware, so most games that need hardware rendering won't run. Older games like StarCraft run just fine, but also run just as well with Wine. Virtualization is not meant for gaming, unless you're into retro gaming.

Your best bet for gaming with Ubuntu is currently Wine rather than virtualization.

---

### Post by Valok on 2008-10-21
Awesome, thanks for the replies everyone.  Gonna head back off and keep on trucking with WINE.  

Dunno if this is the right place to ask, but when a big new game comes out (Starcraft 2 and Diablo 3) how long does it usually take for WINE to be updated to run that game?

---

### Post by tuxxy on 2008-10-21
It varies but they do often get updated rather quickly, only they may not be at a Gold level for a while after, just dont expect 100% functionality too early.

---

### Post by carmstrong on 2008-10-21
Virtual machines are awful with graphics intensive apps (ex. gaming).  Virtualbox seems to be better because you can allocate video resources when setting up the VM, but it will never match the resources of the host machine

---

