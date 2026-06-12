---
title: "Does removing ubuntu-desktop create security risk?"
date: 2009-04-27
forum: Security
---

### Post by kansasnoob on 2009-04-27
OK, I've seen this debated nearly ad nauseam, but if I make modifications to my Ubuntu and removing a certain app (in this case notify-osd) requires removing the meta-package "ubuntu-desktop" will that actually prevent proper updating (especially on the security level)?

If you look at the ubuntu-desktop package in synaptic it clearly says:

> It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

Then again I've built a few machines using ubuntu-minimal with various window managers and I seem to get regular updates:confused:

I'm still using Hardy for production, but I've been playing with Jaunty since alpha 5 and I love the speed, the pulseaudio improvements, and many of the package upgrades!

Basically Jaunty rocks, but with my visual impairment the new notifications just don't work at this point. So I found a happy solution with the gnome-stracciatella-session for a while, but then I ran into sound problems. I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/357833](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/357833)

Anyway I love the way my desktop is working right now after removing the gnome-stracciatella-session, restoring gdm to boot gnome, and removing notify-osd ............. but doing so removes the ubuntu-desktop meta-package.

Is that going to pose a risk?

If so what level of risk?

---

### Post by benny bronx on 2009-04-27
Ubuntu-desktop is needed for distro upgrades, not regular updates.  I believe I removed it when on 7.10 and did not have any problems with updates.  Since I do fresh installs, I do not know what problems will occur during an upgrade if the ubuntu-desktop package is removed.

---

### Post by kansasnoob on 2009-04-27
> **benny bronx said:**
> Ubuntu-desktop is needed for distro upgrades, not regular updates.  I believe I removed it when on 7.10 and did not have any problems with updates.  Since I do fresh installs, I do not know what problems will occur during an upgrade if the ubuntu-desktop package is removed.

If that's the case I have no worries! If I were to attempt a distro upgrade I could always reinstall ubuntu-desktop before proceeding.

I seldom do distro upgrades anyway other than for testing purposes.

I should also have added that I don't mean to poo-poo the new notifications! It's simply that it doesn't work for me at this point. It's something new and I'm sure they'll make it more easily configurable to facilitate everyone!

---

