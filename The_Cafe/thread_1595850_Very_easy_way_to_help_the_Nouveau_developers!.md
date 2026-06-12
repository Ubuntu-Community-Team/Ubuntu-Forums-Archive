---
title: "Very easy way to help the Nouveau developers!"
date: 2010-10-13
forum: The Cafe
---

### Post by MaxIBoy on 2010-10-13
Even if you do NOT use Nouveau, you can help out the nVidia developers and it will take at most twenty minutes. If you have an nVidia GPU using an NV40 core or newer, they would like you to download some of their BIOS dumping tools with Git, compile and run them, and email the results to them.

News story:
[http://www.phoronix.com/scan.php?page=news_item&px=ODY2Nw](http://www.phoronix.com/scan.php?page=news_item&px=ODY2Nw)
Instructions:
[http://github.com/pathscale/pscnv/wiki/TestingTimings](http://github.com/pathscale/pscnv/wiki/TestingTimings)

The wiki page doesn't doesn't give compile instructions or list the dependencies, but it's very easy and I figured it out without too much trouble. Just [git clone]("http://linux.die.net/man/1/git-clone") the pgtest repository (git://0x04.net/pgtest) and the vbtracetool repository (git://anongit.freedesktop.org/~stuart/vbtracetool), and to compile each one, cd to the directory and just type "make." You need to install libpci-dev and libpciacces-dev for it to work. Once you've got them compiled, the instructions I linked to above are very easy to follow.

This presents NO RISK to your graphics card. It reads from your GPU's BIOS and registers but DOES NOT MODIFY THEM! The worst that could happen is your X server hanging, and that didn't happen for me.

The Nouveau devs already have this info from 68 different computers (including mine,) but could probably use more. Please, if you want to further this open-source nVidia driver, now is your chance to help!

(NOTE: I'm not a Nouveau developer, I'm just posting this on my own initiative.)

---

### Post by Robstarusa on 2010-11-04
Done!

---

### Post by 3Miro on 2010-11-04
Will do that tonight. I just hope it is legal.

---

### Post by lykeion on 2010-11-04
Also done here

Some notes: it's libpciaccess-dev (with two s)

To also do the optional nvbios help:
Reqs (may be some more pkgs than these)
```
libxml2-dev cmake bison flex
```
Envytools git: git://github.com/pathscale/envytools.git
Compile:
```
cmake .
make
```

---

### Post by Helkaluin on 2010-11-04
Done! Hope it helps them.

---

