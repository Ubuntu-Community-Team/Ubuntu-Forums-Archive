---
title: "ubuntuone-client-applet not found"
date: 2010-10-04
forum: Ubuntu One (CLOSED)
---

### Post by DantePasquale on 2010-10-04
Hi, I'm running 9.10 and was using wicd instead of network-manager. So, I tried a few things to get u1 working under wicd and gave up.

For other reasons, I switched back to using network-manager instead of wicd. Now I can't get u1 to re-install or uninstall or something!

There is no ubuntuone-client-applet. I did tried installing:

```
ubuntuone-client-applet
The program 'ubuntuone-client-applet' is currently not installed.  You can install it by typing:
sudo apt-get install ubuntuone-client-gnome
```

and that goes fine, but there's still no client-applet!

Found some steps for completely removing and re-installing u1, but that didn't help. Any ideas?

Danté

---

### Post by duanedesign on 2010-10-06
Are you installing Ubuntu One from the PPA? or from the Karmic repository? In newer versions of Ubuntu One there is no ubuntuone-client-applet, it has been replaced with ubuntuone-preferences. What do you get when you run:

```
apt-cache policy ubuntuone-client
```

thank you,
duanedesign

---

### Post by gopher38 on 2010-10-06
I believe I have the same problem.  I tried installing on Jaunty and followed the installation instructions on the Ununtuone site, which start with clicking on the "Add PPA" link.  The installation instructions said that I should then receive and invitation to install ununtuone-client-gnome, but that never happened.  So I tried finding it in Synaptic, and there was only the line for ubuntuone-ppa-beta (I think that was it; did it a while ago).  Tried a few other things and then gave up.

---

