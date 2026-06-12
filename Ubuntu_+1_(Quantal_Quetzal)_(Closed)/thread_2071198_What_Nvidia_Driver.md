---
title: "What Nvidia Driver ?"
date: 2012-10-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Frogs Hair on 2012-10-14
Of the four driver selections offered in additional drives the open source Nouveau and the Nivdia Experimental drivers work the best for me.  The tested Nvidia current which is recommended has the most problems . The  boot is very choppy and I see text when logging out or shutting down. The    same is true with  the current version that receives updates.

The Nivida Experimental works great for me but the go to Nvidia current is troublesome for the first time in my Ubuntu experience going back to 9.10. What are others using?

---

### Post by VinDSL on 2012-10-14
> **Frogs Hair said:**
> What are others using?
I haven't tried the experimental drivers yet, but this is working fine for me...

```
vindsl@Zuul:~$ apt-cache policy nvidia-current
nvidia-current:
  [COLOR="DarkRed"]**Installed: 304.51-0ubuntu1~xedgers~quantal1**[/COLOR]
  Candidate: 304.51.really.304.43-0ubuntu1

vindsl@Zuul:~$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  [COLOR="DarkRed"]**Installed: 2:1.13.0+git20120920.70e57668-0ubuntu0ricotz**[/COLOR]
  Candidate: 2:1.13.0+git20120920.70e57668-0ubuntu0ricotz
```

---

### Post by Frogs Hair on 2012-10-14
Looks like the PPA. My driver has the same number but is not the xedgers.  The rest is different . ```
xserver-xorg-core:
  Installed: 2:1.13.0-0ubuntu6
  Candidate: 2:1.13.0-0ubuntu6
  Version table:
 *** 2:1.13.0-0ubuntu6 0
```

---

### Post by cariboo on 2012-10-14
I using the nvidia-current-updates driver from the repositories. It has a know problem, where the launcher won't unhide without creating the following /etc/X11/xorg.conf:

```
 cat /etc/X11/xorg.conf
Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option     "ConstrainCursor" "no"  
EndSection

```

---

### Post by Harry33 on 2012-10-15
Just a reminder for people installing Nvidia proprietary drivers (like nvidia-current).
Ubuntu doesn't generally need any /etc/X11/xorg.conf files even with proprietary drivers.
Instead, errors in the file, if it exits, may lead to X failure.

---

### Post by Frogs Hair on 2012-10-15
Thanks Harry 33 , I am seeing this message.```
cat: /etc/X11/xorg.conf: No such file or directory  
```The following command displays a different driver version than the Nvidia Xserver Settings. ```
apt-cache policy nvidia-current
```

I'm  happy to have found a proprietary driver that works well for me,  although I was surprised it was not Nvidia Current.

---

