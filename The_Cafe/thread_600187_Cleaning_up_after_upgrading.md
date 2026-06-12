---
title: "Cleaning up after upgrading"
date: 2007-11-02
forum: The Cafe
---

### Post by nickburns on 2007-11-02
I recently looked at my raid storage box that has been running faithfully in the corner, and to my surprise it was running Dapper on it.  So I took some time today and upgraded it.

Dapper --> Edgy --> Feisty --> Gusty

Everything went smooth as can be, except:

My Hard drive space on / went from 831 mb to 1.9 gigs.  How to I clean this back up?

---

### Post by FuturePilot on 2007-11-02
```
sudo apt-get clean
```
That clears out your apt archive where your probably have tons of packages from the upgrade.

---

### Post by Tundro Walker on 2007-11-03
The upgrades also tend to "reset" you to the default Ubuntu load-out.  So, if you previously took the time to uninstall some stuff, it may have been loaded back on (or more stuff may have been added).

(Well, that's the case with the desktop distro...if you're using the server distro, it might not be the case, but worth checking out.)

---

### Post by Gremlinzzz on 2007-11-03
I use this command
sudo apt-get autoremove

---

### Post by nickburns on 2007-11-03
autoclean took of about 400 megs (down to 1.5 gig)

clean took another 200 megs(down to 1.3 gigs)

Not quite the 800 megs I started with. But close enough... I guess.

---

