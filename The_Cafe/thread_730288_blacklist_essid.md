---
title: "blacklist essid"
date: 2008-03-20
forum: The Cafe
---

### Post by zadig on 2008-03-20
I usually leave my laptop up at nights to run amule and stuff, but my laptop connects to my neighbors wireless network (changes the essid to his network essid and tries to connect there)  and ends up downloading nothing. Is there a way to block my laptop to connect to that a specific essid (belkin54g) ?

---

### Post by zadig on 2008-04-03
bump

---

### Post by kutjara on 2008-04-03
> **zadig said:**
> I usually leave my laptop up at nights to run amule and stuff, but my laptop connects to my neighbors wireless network (changes the essid to his network essid and tries to connect there)  and ends up downloading nothing. Is there a way to block my laptop to connect to that a specific essid (belkin54g) ?

You can use "Manual Configuration" from the network manager applet dropdown menu to turn off roaming for your wireless network. Then you can enter the details of your home network, so your computer will only connect to it, and no other.

It's an inelegant solution, though, because you'll have to fiddle around with turning roaming back on if you want to connect to networks at hotspots, and then reenter your password whenever you want to reenable home network exclusivity.

What's badly needed is a "preferred network" capability like in Windows and OS X.

---

### Post by kutjara on 2008-04-03
I just learned in another thread that wicd is many people's preferred alternative to gnome network manager. wicd allows you to specify a preferred network, among other things. You can get it here:

wicd.sourceforge.net

I'm trying it out at the moment and find it a bit flakey under Hardy, but it apparently works great under Gutsy.

It does uninstall gnome-nm during the installation process, so if you decide you don't like wicd, you'll have to reinstall nm.

---

