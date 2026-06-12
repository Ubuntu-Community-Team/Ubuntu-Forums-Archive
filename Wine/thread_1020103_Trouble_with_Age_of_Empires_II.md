---
title: "Trouble with Age of Empires II"
date: 2008-12-23
forum: Wine
---

### Post by oddparticle on 2008-12-23
Hi,
I've been trying to install Age of Empires II, using Wine 1.0.1 and Ubuntu 8.10. I've managed to get the installer to run, and supposedly successfully install it once. However, I couldn't then get the game to run - when I clicked on the icon for it then nothing happened. So, I uninstalled it and was going to try again with a full install. But now, whenever I get to the screen on the installer which asks which kind of install I want to do, then whichever option I choose, when I click continue then my computer freezes totally and has to be restarted. Any ideas?

---

### Post by pytheas22 on 2008-12-23
I'm afraid I can't give you a good answer, but I wanted to point out that Age of Kings installed and ran for me through wine on Ubuntu 7.10 a year ago, but I haven't tried it since then.  It was a little slow and some fonts were corrupted, but it was stable and generally playable (didn't try multiplayer).

However, because I was fed up with the slowness, I decided to try installing AOK in VirtualBox, where it worked wonderfully, including multiplayer through igzones.  So you may want to try that route, which should give you an easier and more reliable experience than wine.  Of course, you will need a copy of Windows to install into your virtual machine, but otherwise VirtualBox is free and easy to use use.  I'm happy to guide you through installing AOK in it if you need help.

If you really want to try it in wine, it may help to run these commands, which will completely wipe out your current wine installation (including any other programs you have installed through wine!) and give you a clean slate:
```

sudo apt-get remove --purge wine
rm -rf ~/.wine
sudo apt-get install wine
```

---

