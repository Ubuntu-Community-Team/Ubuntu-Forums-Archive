---
title: "DeVeDe error"
date: 2009-10-21
forum: Ubuntu Studio
---

### Post by Byrd740 on 2009-10-21
I have installed DeVeDe on many other distros without problem. So I decide to install it on my HP desktop with Ubuntu 9.10, and it shows an error saying that it can't find mencoder and mplayer. I have both installed and can't figure out what the problem is. I tried reinstalling all three and it didn't do any good.

---

### Post by Byrd740 on 2009-10-21
I fixed it!  It turns out OpenShot was the problem.  Why, I don't know.  But, I uninstalled it and reinstalled DeVeDe and it works!   VLC was also affected, as in it wouldn't play any avi file.   But, why would OpenShot do that?

---

### Post by BenAshton24 on 2009-10-21
Strange... I have OpenShot installed and just installed DeVeDe and both work perfectly :P

---

### Post by Byrd740 on 2009-10-21
Dang, I reinstalled OpenShot, and now can't get devede back working.  ugggghhh

---

### Post by howefield on 2009-10-21
> **Byrd740 said:**
> Dang, I reinstalled OpenShot, and now can't get devede back working.  ugggghhh

Is this devede from the repository you are trying ?

If you are using the .deb file from the devede website, as I usually did because it was a newer version than was in the repository, just to let you know that Karmic has the newest version.

[http://www.rastersoft.com/programas/devede.html#download_section](http://www.rastersoft.com/programas/devede.html#download_section)

---

### Post by Byrd740 on 2009-10-21
Alright, what I had to do is install ffmpeg with aptitude.   This fixes it.  But, if I try to install OpenShot, OS wants to remove ffmpeg.  So, I tried installing OpenShot then ffmpeg, but ffmpeg wants OpenShot removed.  I guess Open shot is the problem.

Edit:  I searched the openshot website and saw this.  I guess that explains it.  I guess I can call this solved.

---

### Post by lazy_hoor on 2009-10-31
I don't appear to have OpenShot but I can't get Devede installed.  I keep getting the 'You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.' Where is bzip2recover?

---

### Post by Byrd740 on 2009-11-04
> **lazy_hoor said:**
> I don't appear to have OpenShot but I can't get Devede installed.  I keep getting the 'You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.' Where is bzip2recover?
It sounds like you tried to install the source code?  I would recommend using the repository if you didn't.

Just out of curiosity try:
```
sudo dpkg --configure -a
```P.S.  I know I am shooting in the dark here.

---

