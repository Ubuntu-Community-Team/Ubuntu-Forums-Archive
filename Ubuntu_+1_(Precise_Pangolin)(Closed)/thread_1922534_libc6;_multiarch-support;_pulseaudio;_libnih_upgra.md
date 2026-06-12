---
title: "libc6*; multiarch-support; pulseaudio*; libnih* upgrades"
date: 2012-02-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-02-09
Didn't seem to go too well on a i386 with nvidia install, ymmv

fixed with new libc

---

### Post by xyzzyman on 2012-02-09
Isn't multi-arch just for 64bit installs to run 32bit? It's been so long since I've run 32bit that I might be mistaken.

---

### Post by mc4man on 2012-02-09
> **xyzzyman said:**
> Isn't multi-arch just for 64bit installs to run 32bit? It's been so long since I've run 32bit that I might be mistaken.

Atm the package is hard to do without, if on a 32 bit install & your terminal can scroll 2000 lines or so run this to see
```
sudo apt-get -s purge multiarch-support
```

Anyway the result of the upgrades here is unity-3d produces a semi usable desktop, no unity. unity-2d fails to load at all, gnome fallback is usable, the nux support test crashes, nvidia-settings crashes ect.

---

### Post by bmbaker on 2012-02-09
anyone know if this is fixed yet?

---

### Post by mc4man on 2012-02-09
> **bmbaker said:**
> anyone know if this is fixed yet?
Not yet - 
If you did upgrade you have some options depending on what else you upgraded that that now depends on the new libc6, whether you get to a desktop or not or if you happen to have the gnome fallback session that works

If you can get to any desktop  then it's possible to open synaptic & firefox, acquire all the packages that need to be downgraded & install in bulk.

Otherwise it may just be easier to remove nvidia-current,  switch to nouveau & wait for a fix

The list here was fairly large 10 hrs ago , it could be a bit now as there where additional updated packages that depend on the new libc like cups, ect.

> ~/Desktop/libc$ ls
libc6_2.13-24ubuntu4_i386.deb         
libc6-dev_2.13-24ubuntu4_i386.deb     
libc-bin_2.13-24ubuntu4_i386.deb 
libc-dev-bin_2.13-24ubuntu4_i386.deb  
libpulse-mainloop-glib0_1.1-0ubuntu6_i386.deb     
pulseaudio_1.1-0ubuntu6_i386.deb
pulseaudio-esound-compat_1.1-0ubuntu6_i386.deb   
pulseaudio-module-gconf_1.1-0ubuntu6_i386.deb
pulseaudio-module-x11_1.1-0ubuntu6_i386.deb
libpulse0_1.1-0ubuntu6_i386.deb       
pulseaudio-utils_1.1-0ubuntu6_i386.deb
libpulsedsp_1.1-0ubuntu6_i386.deb
libnih1_1.0.3-4ubuntu5_i386.deb 
libnih-dbus1_1.0.3-4ubuntu5_i386.deb    



---

### Post by Seq on 2012-02-09
> **xyzzyman said:**
> Isn't multi-arch just for 64bit installs to run 32bit? It's been so long since I've run 32bit that I might be mistaken.

You're probably thinking of the old ia32-libs package. Multi-arch allows (or will) allow multiple archetectures to be installed together. There is an [Ubuntu spec]("https://wiki.ubuntu.com/MultiarchSpec") about it, and there is info on the Debian side as well.

The benefit being that ia32-libs was a amd64 package of many i386 builds of libraries. Which means the maintainer of that package had to track security updates and separately update ia32-libs. Annoying and non-optimal.

multiarch would allow you on a 64-bit system to say "Install the i386 version of gimp", and have it grab the proper packages, the same ones that an i386 user would be installing. This means no more 64-bit packages containing 32-bit libraries or files. Neat.

Another thing that is kinda cool is in theory, you can have more than just i386 and amd64. You could also have potentially arm, or ppc systems cohabiting the same filesystem. Would be really handy for nfs-mounted roots servicing differing systems (one place to manage updates).

Also, in the future newer platforms that support executing multiple arches (ex: a 64-bit arm platform?) could benefit from this pre-existing infrastructure.

Granted, as far as regular 32/64-bit desktop use goes, this would have been handier a few years ago. But hey, at least we're ready for the switch to 128-bit...

---

