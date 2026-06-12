---
title: "apt get dist-upgrade?"
date: 2008-10-04
forum: The Cafe
---

### Post by civillian on 2008-10-04
Just a question, I was looking into rolling distros (arch, gentoo, debian sid etc) and I was thinking about ubuntu...

obviously, having to download a new cd image every 6 months is a an irritating thing to have to do, but why do people shy away from dist-upgrade? obviously I can see problems with packages installed on the 'old' system that might be considered 'legacy' by the next release and possibly causing issues, but providing there isn't a hige change in the codebase, and core applications that were installed, why shouldn't dist-upgrade be just as painless as a pacman -Syu (or whatever)?

Feel free to enlighten me, and/or play devils advocate (whichever side of the fence you fall on).
And which would you suggest for me for the end of this month when we get the stable 8.10 release?

---

### Post by LaRoza on 2008-10-04
> **C!V!NT said:**
> 
obviously, having to download a new cd image every 6 months is a an irritating thing to have to do,
You don't have to. Ubuntu support is continued after releases and with Hardy Heron, one doesn't have to think about it for years if they don't want to.

> 
but why do people shy away from dist-upgrade? 
Do they?

> 
obviously I can see problems with packages installed on the 'old' system that might be considered 'legacy' by the next release and possibly causing issues, but providing there isn't a hige change in the codebase, and core applications that were installed, why shouldn't dist-upgrade be just as painless as a pacman -Syu (or whatever)?

Upgrading, anything, can cause breakages. This applies to any individual apps, or whole systems.

> 
Feel free to enlighten me, and/or play devils advocate (whichever side of the fence you fall on).
And which would you suggest for me for the end of this month when we get the stable 8.10 release?

Well, if you want to use 8.10, you can do anything you want.

You can try the live disk. You can do a fresh install. You can upgrade with the disk. You can do a network upgrade. You can wait a month or two and see what happens. It is all up to you.

---

### Post by hansdown on 2008-10-04
Hi C!V!NT.

I'd just like to add that 8.04 is a long term support version, meaning it will have alot of help for at least a year.

---

### Post by civillian on 2008-10-04
> 8.04 is a long term support version, meaning it will have alot of help for at least a year.

I know, but I enjoy having the latest version!

> Do they? advocates of arch etc often cite rolling releases over monloithic updates (a la ubuntu).

What are peoples opinions on both?

---

### Post by LaRoza on 2008-10-04
> **hansdown said:**
> I'd just like to add that 8.04 is a long term support version, meaning it will have alot of help for at least a year.

3 years.

> **C!V!NT said:**
> 
 advocates of arch etc often cite rolling releases over monloithic updates (a la ubuntu).

What are peoples opinions on both?

Of course the advocates of Arch prefer the arch way, otherwise they wouldn't use Arch.

It is just different. You can observe it when you do it.

---

### Post by civillian on 2008-10-04
has anyone had any experience of uisng dist-upgrade?

---

### Post by hansdown on 2008-10-04
Thanks for that LaRoza.

---

### Post by LaRoza on 2008-10-04
> **C!V!NT said:**
> has anyone had any experience of uisng dist-upgrade?

Yes, it works fine. Network wise, it takes about 30 minutes when I use it.

---

### Post by civillian on 2008-10-04
Any thoughts about leftover packages etc? or does it work smoothly? (The last time I really looked into it, ubuntu was at dapper drake release, and it was certainly buggy at the time...)

Half an hour seems reasonable for a system overhaul!

---

### Post by LaRoza on 2008-10-04
> **C!V!NT said:**
> Any thoughts about leftover packages etc? or does it work smoothly? (The last time I really looked into it, ubuntu was at dapper drake release, and it was certainly buggy at the time...)


Dapper is now considered quite solid by most people (it was my first taste of Linux and I felt it was good enough to wipe Vista after trying it out). There will be left over packages, but it isn't that bad. Many people (like me) have upgraded continuously over a couple releases without any problems.

> 
Half an hour seems reasonable for a system overhaul!
Well, that depends on network speeds. It can be much faster if you have a faster network. The system is usable during the time, but I usually prefer to leave it alone or use another computer. After downloading, it then sets it up (so if the network is interupted, there isn't a problem, and you can start where you left off later), and that can take 5 - 10 minutes (depending on hardware and settings. If you have a lot of other packages (like kde, gnome, etc instead of what it came with) it will also upgrade those and that will take more time.

---

### Post by jacksaff on 2008-10-04
Some early versions of ubuntu had quality control problems with dist-upgrades - they don't have anywhere near as many people testing as debian does, nor for as long. These days it seems well controlled though. Perhaps the dev community has gotten big enough.
 
I'd like to see a rolling release ubuntu. For desktop users there doesn't seem to be any need for releases. Something like sidux with it's scripts that let the community monitor tricky updates would be awesome. Maybe a testing repo with a one month delay to main so that people who can't fix their systems only ever get well tested updates. It would also be a good way for us non-technical users to get involved. By running 'ubuntu-sid' we could be usefully testing software without the big disruption that you need to test alpha ubuntu releases.

---

