---
title: "im designing my own ubuntu based linux distro.  can you help me for"
date: 2012-04-09
forum: The Cafe
---

### Post by chanentert on 2012-04-09
im designing my own ubuntu based linux distro.  \\:D/
[B]
1. how can i change the name of Ubuntu grub. [/B]
ex : when start the computer we can display 
ubuntu with linux kernal xxx 
ubuntu with linux kernal xxx (recover mood) 
windows 7 etc....  

i want to change ](*,)
MyLinuxName with linux kernal xxx 
MyLinuxName with linux kernal xxx (recover mood)
 windows 7 

**2. how can i change the image and logo. **
i want to change all ubuntu logos and images, like ubuntu boot logo, dash menu logo etc.  please help me

---

### Post by MG&amp;TL on 2012-04-12
1. Look at this thread: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275"), especially point 6. I'm not entirely sure how you would accomplish that, but it should be fairly simple. 

2. For the icons, I am afraid you will just have to find where the icon is coming from everytime you see an ubuntu logo, then change it.

---

### Post by JOHNNYG713 on 2012-04-12
Without knowing what release you are going to use, may I suggest,

Grub customizer [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

Change login screen
Simple lightdm manager [http://www.ubuntugeek.com/simple-lightdm-manager.html](http://www.ubuntugeek.com/simple-lightdm-manager.html)

Change start menu logo and other tweaks
Ubuntu tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
Ailurus [http://code.google.com/p/ailurus/](http://code.google.com/p/ailurus/)

Best of luck ! keep us updated ! ):P

---

### Post by roelforg on 2012-04-12
Research debootstrap, seems like it will work for you.

---

### Post by sffvba[e0rt on 2012-04-12
*Thread moved to **The Community Cafe**.*


404

So many new distro's coming soon it seems... will have to postpone installing 12.04...

---

### Post by Fragadelic on 2012-04-13
If you want to change what name shows up in grub, you have to change the lsb-release info.

/etc/lsb-release

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"

```

But be warned, if you change this then you have to setup your distribution info in /usr/share/python-apt/templates.  You'll have to setup a YourCustomDistro.info and YourCustomDistro.mirrors and the YourCustomDistro must match the Distrib_ID=YourCustomDistro in the /etc/lsb-release file.

---

### Post by Bandit on 2012-04-13
> **chanentert said:**
> im designing my own ubuntu based linux distro.  \\:D/
[B]
1. how can i change the name of Ubuntu grub. [/B]
ex : when start the computer we can display 
ubuntu with linux kernal xxx 
ubuntu with linux kernal xxx (recover mood) 
windows 7 etc....  

i want to change ](*,)
MyLinuxName with linux kernal xxx 
MyLinuxName with linux kernal xxx (recover mood)
 windows 7 

**2. how can i change the image and logo. **
i want to change all ubuntu logos and images, like ubuntu boot logo, dash menu logo etc.  please help me

As much as I admire you enthusiasm, building your own distro or moding one to that extent takes some learning. Depending on your ability to pick up and learn this can be a small learning curve or a large one. I do however suggest you start with something more simple as customizing existing GTK and Metacity themes then work your way up. Themeing is the best way to learn were all the icons and other graphics are located. 

I once built my own linux distro from scratch. Did rather well building everything from scratch up to the point where I tried to compile Gnome2 from source code and ran into dependency's requiring other dependency that required the first one. Its like A requiring B, B requiring C, but C still requiring A. Vicious cycle and for that I am glad Gnome2 is gone and Gnome shell is reworked. But anyway the point is I wasted 2 weeks of my life. Great experience but hell to do on a 2Ghz AthlonXP with 1GB of ram..

---

