---
title: "Theme Hospital on Ubuntu Netbook Edition 10.04"
date: 2010-09-13
forum: Wine
---

### Post by scratman on 2010-09-13
I have a netbook running UNE, and an original CD-ROM copy of Theme Hospital which I would like to play on my netbook.Things are complicated by the fact that I have no optical drive, and no option to install one.  I have installed Wine, and it is allegedly possible for me to run Theme Hospital on my machine through Wine.  I know how to rip my existing CD to an .iso image, but not how to get my .iso file to appear as a CD, and then load the game through Wine.  I'm sure it's quite straightforward, but I'm a touch baffled currently.  I managed to achieve it on this machine with Windows XP using daemon tools, but believe that they would be useless for my purposes on Ubuntu.  Any suggestions?

---

### Post by Joe of loath on 2010-09-13
Enter a terminal window, and type in:

```
mount -o loop *iso location* *mount point*
```

The iso image will mount as a CD drive.

HTH
Joe

---

### Post by cajuuh on 2011-09-13
thanks i was trying to mount a iso image for a long time ago and does'nt know how.:)

---

