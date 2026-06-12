---
title: "VM ware type program"
date: 2007-07-09
forum: The Cafe
---

### Post by tcpip4lyfe on 2007-07-09
Can someone recommend a virtual OS emulator like VM ware? What are your favorites?  I kind of want to a linux from scratch project.

---

### Post by dreadlord_chris on 2007-07-09
Virtualbox - it works, it's [FLOSS]("http://en.wikipedia.org/wiki/FOSS"), and it's on the repositories....

---

### Post by smoker on 2007-07-09
i agree with dreadlord, virtualbox, easy to setup and use.

---

### Post by jkeyes0 on 2007-07-09
Also, if you're wanting something like VMware, you could always run VMware. I'm not sure if it's in the universe repository, but I know VMware Player exists out there, and VMware Server is in the Canonical Commercial repository (a quick search of the forum will yield installation instructions)

---

### Post by starcraft.man on 2007-07-09
> **dreadlord_chris said:**
> Virtualbox - it works, it's [FLOSS]("http://en.wikipedia.org/wiki/FOSS"), and it's on the repositories....

Uh, no..... Virtual Box isn't in any of the main repos (nor in universe/multi), at least not yet. [Here]("http://www.virtualbox.org/wiki/Downloads") is the download page, my preferred method is to add the feisty repo to your sources list and then install it from your favourite method. The binary works equally well, its just a lot easier over long term to maintain it as a package.

> **jkeyes0 said:**
> Also, if you're wanting something like VMware, you could always run VMware. I'm not sure if it's in the universe repository, but I know VMware Player exists out there, and VMware Server is in the Canonical Commercial repository (a quick search of the forum will yield installation instructions)

Yup, you need to enable the multiverse in your sources list to get VMware, I just checked where the packages are located.

I also recommend VBox, great program. Have fun :).

---

### Post by ceelo on 2007-07-09
Go with VirtualBox, it's great IMO. I just tried out VMWare and VirtualBox for the first time over the last few days, and could not get VMWare working properly. I got XP and Debian up and running with VirtualBox very easily.

---

