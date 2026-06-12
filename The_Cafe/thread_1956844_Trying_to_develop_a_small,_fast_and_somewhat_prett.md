---
title: "Trying to develop a small, fast and somewhat pretty DE."
date: 2012-04-11
forum: The Cafe
---

### Post by jjpcexpert on 2012-04-11
I'm calling the desktop Gammon after it's original components - GTK+/Gnome-settings-daemon, Avant Window Navigator, Mutter (now using Compiz for compositing, Metacity for non-compositing desktop), (and was hoping to compile on Debian correctly) Netbook Launcher EFL. Also, it almost got called Jade but I scrapped Jade. Decided to name the DE after a steak. The desktop experience project, which is all about making the Awn and Compiz settings reload into and out of those programs with bash and python scripts, and managing the session with the scripts, will need to set sane defaults for using Awn without any other dock, and for using Compiz with all of this. So basically I need help. If any developers want to volunteer (no pressure meant), you're more than welcome. I'm not on a pear run this time, but I'm seriously trying to:
 - Compile Netbook Launcher EFL on Debian Wheezy (Mutton DX)
 - Fork AWN
 - Fork Compiz (Mutton DX)
 - Fork Mutter and Metacity (Mutton DX)
 - Cobble all this together with some strong script string that won't explode any time soon
 - Optimize for 686 and later CPUs (netbooks, newer end of old computers, etc.)
0a1.00 is ready, however it is not to be released. I won't release until I get to 0rc1.00 as I need something stable for v0.00.

In a few minutes, hours or days, I'll be registering on Google Code exclusive-or Launchpad to get the generator up and running on this project, i.e. allow people to start test driving.

If I will not be able to compile netbook launcher, I must be able to simulate Gnome shell in widgets, or port Gnome shell Activities to widget windows.

---

### Post by Lucradia on 2012-04-12
The "last" netbook has been released by ASUS, who started this "Netbook" deal thing. Better start looking to tablets too.

---

### Post by jjpcexpert on 2012-04-12
> **Lucradia said:**
> The "last" netbook has been released by ASUS, who started this "Netbook" deal thing. Better start looking to tablets too.
Well lots of people have widescreen laptops, so this project counts for them. If you wish to contribute, team is gammon-devs.

---

