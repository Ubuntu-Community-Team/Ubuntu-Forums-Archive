---
title: "debian + ubuntu repositories"
date: 2007-11-13
forum: Repositories &amp; Backports
---

### Post by -grubby on 2007-11-13
how do I add the Ubuntu repositories to Debian?Don't ask me why. I need it for some drivers that I can't find elsewhere and this would just be the easiest way

---

### Post by llamakc on 2007-11-13
You edit the /etc/apt/sources.list file just like you normally do in Debian.

---

### Post by -grubby on 2007-11-13
> **llamakc said:**
> You edit the /etc/apt/sources.list file just like you normally do in Debian.

yes but what lines do I add?

---

### Post by -grubby on 2007-11-13
*bump*

---

### Post by llamakc on 2007-11-13
I don't understand your question. You're going to have to be more specific about the driver you need.

Anybody using Debian should already be knowledgeable on how to edit the sources.list file. What do you want to add? You add what you want to.

Unless you've seen a specific page on the net that recommends what you're doing, I foresee breakage.

Oh, and do NOT bump threads unless a day has passed. This isn't IRC.

---

### Post by kerry_s on 2007-11-13
i don't get it either, have you turned on all the repo's?
add " contrib non-free" to the end?

i run lenny/sid, my sources.list->

```

deb http://www.debian-multimedia.org sid main
deb http://ftp.debian.org/debian/ lenny main non-free contrib 
deb http://ftp.debian.org/debian/ sid main non-free contrib 
deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 


```

---

### Post by smartboyathome on 2007-11-13
He wants the Ubuntu repositories on debian. And that isn't a good idea, since Ubuntu and Debian don't mix well.

---

### Post by kerry_s on 2007-11-13
> **smartboyathome said:**
> He wants the Ubuntu repositories on debian. And that isn't a good idea, since Ubuntu and Debian don't mix well.

i got that much, i meant i can't understand why he would need to add another distro's repo to find a driver that is most likely in the debian repos. :confused:

---

### Post by -grubby on 2007-11-13
> **kerry_s said:**
> i got that much, i meant i can't understand why he would need to add another distro's repo to find a driver that is most likely in the debian repos. :confused:

by the way, it's not in the debian repos. I just wanted 3d acceleration for my NVIDIA 6200, which installs via the ubuntu restricted drivers manager. If I look in the Ubuntu repositories I can also find it. The one from the official NVIDIA site does not work. I think its the NVIDIA-GLX-new or something like that. I knew the exact name earlier but I still couldn't find anything via a google search?

---

### Post by kerry_s on 2007-11-14
yeah, damn nvidia has always been shacky in debian. i been using the stock nv since i'm running a lenny/sid install, less chance of updates taking out my X.

anyways they are there, see pic->

---

### Post by -grubby on 2007-11-14
would I just use NVIDIA-GLX than?

---

