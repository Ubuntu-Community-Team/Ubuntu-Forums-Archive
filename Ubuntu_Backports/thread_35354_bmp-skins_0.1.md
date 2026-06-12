---
title: "bmp-skins 0.1"
date: 2005-05-18
forum: Ubuntu Backports
---

### Post by Technoviking on 2005-05-18
I have made a package for bmp-skins based off of xmms-skins. It has all the basic xmms-skins, plus some nice Ubuntu based skins for beep-media-player. 

Enjoy,
Mike

---

### Post by psoleko on 2005-05-19
Very nice, thanks.

---

### Post by bored2k on 2005-05-19
You guys need to tell Chua from ubuntuguide to change his backport url to a mirror !
Nice compilation thanks :D

P.S. - How could you not include [http://www.gnomelook.org/content/show.php?content=14870](http://www.gnomelook.org/content/show.php?content=14870) ? :?

---

### Post by Technoviking on 2005-05-20
[QUOTE=bored2k]
P.S. - How could you not include [http://www.gnomelook.org/content/show.php?content=14870](http://www.gnomelook.org/content/show.php?content=14870) ? :?[/QUOTE]
Never seen it before:), mostly use the Human skins. I'm make a new version later.

Mike

---

### Post by sexcopter on 2005-08-30
Hi, I'm trying to get this bmp-skins package, but can't find it! I think I have all the most common repositories. My sources.list file reads:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free


(I removed hashed lines as I assume they're of no relevance.)
Any ideas? Thanks in advance!

James

---

### Post by AndyAWS on 2005-08-30
For Backports you need to add the following to your sources.list

New Official repo:
```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```

I also keep the old repos because not all packages were moved:
```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted 
```

---

