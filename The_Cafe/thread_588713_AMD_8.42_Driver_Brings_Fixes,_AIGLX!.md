---
title: "AMD 8.42 Driver Brings Fixes, AIGLX!"
date: 2007-10-23
forum: The Cafe
---

### Post by mysticmatrix on 2007-10-23
Ok I'm no ATI/Nvidia user but as far as my knowledge goes, Ubuntu freezes the driver version of Graphics card at whatever stable version is available at time of release.
Can this be an exception? This sure looks like important release to me.

[http://www.phoronix.com/scan.php?page=article&item=887&num=1](http://www.phoronix.com/scan.php?page=article&item=887&num=1)

---

### Post by zachtib on 2007-10-23
> **mysticmatrix said:**
> Ok I'm no ATI/Nvidia user but as far as my knowledge goes, Ubuntu freezes the driver version of Graphics card at whatever stable version is available at time of release.
Can this be an exception? This sure looks like important release to me.

[http://www.phoronix.com/scan.php?page=article&item=887&num=1](http://www.phoronix.com/scan.php?page=article&item=887&num=1)

i definately think this warrants an exception, at least an additional package, like fglrx-new.

---

### Post by igknighted on 2007-10-23
> **zachtib said:**
> i definately think this warrants an exception, at least an additional package, like fglrx-new.

ATI has a very nice graphical installer available for download for those who desire it... not sure this is worth breaking policy for.  In fact it can even generate distro-specific packages in order to be installed via dpkg.

---

### Post by cogadh on 2007-10-23
Ubuntu doesn't make exceptions when Nvidia or Intel release a new driver, why should the ATI driver be any different? Not to mention, there's nothing stopping someone like GetDeb.net from producing a .deb package for everyone to use.

---

### Post by Scruffynerf on 2007-10-23
I would hope to hell that they do.

One of the things that everyone decries about linux is the damn hardware support.

This is a major vendor actually listening to our (relatively) small community of linux users.

It's not just an update AFAIK, it's a release of brand new drivers for hardware that a lot of linux users complain about.

IMHO, not doing so would not only be rude, but also insulting. Why not show the vendors that there is support for what they are doing for our community by including it as part of the package releases?

---

### Post by yatt on 2007-10-24
Compiz still doesn't work.

---

### Post by pelle.k on 2007-10-24
I'm pretty sure fglrx modules is in the linux-restricted-modules package, so you can't really just produce a .deb for it (fglrx isn't really the package *with* the module, neither is nvidia-glx for nvidia).
[edit]or can you? i imagine you could override the default modules, and use another version somehow?[/edit]

I sometimes wish ubuntu didn't package certain modules this way, but had split packages in some cases like these. Another idea would be if some kernel modules could be inserted by using dkms.

---

### Post by yatt on 2007-10-24
> **pelle.k said:**
> I'm pretty sure fglrx modules is in the linux-restricted-modules package, so you can't really just produce a .deb for it (fglrx isn't really the package *with* the module, neither is nvidia-glx for nvidia).
[edit]or can you? i imagine you could override the default modules, and use another version somehow?[/edit]

I sometimes wish ubuntu didn't package certain modules this way, but had split packages in some cases like these. Another idea would be if some kernel modules could be inserted by using dkms.You can blacklist the modules that come with linux-restricted-modules. The file is in /etc and is called something like restricted-modules.

---

### Post by sloggerkhan on 2007-10-24
It is a pretty easy install. Compiz does work, but you need to use one of a number of workarounds to stop if from being blacklisted. Also, if you are moving from an old xorg.conf, you may need to change options that explicitly say no compositing or aiglx support. 

My experience so far is generally good. The new 'Screens and Graphics' admin CP didn't work with the ATI driver, the FGLRX driver shipping w/ gutsy, or the 8.42 FGLRX driver.  
But compiz-fusion runs fine, at an average of at least 2x the framerate of the ATI driver. Fullscreen games play while AIGLX effects are active, but they seem to have some frames blanking or dropping. GIMP palletes get created behind the top gnome-panel, not sure why, but no other windows do.

Don't much care for the CompizConfig settings manager. Takes too many click to get anywhere in some cases, and doesn't offer obvious options in others. I much prefered the previous beryl style control center thingy.

Hopefully with some tweaking things will be even more workable.
Haven't taken a look at video yet.

---

### Post by mysticmatrix on 2007-10-24
> **cogadh said:**
> Ubuntu doesn't make exceptions when Nvidia or Intel release a new driver, why should the ATI driver be any different? Not to mention, there's nothing stopping someone like GetDeb.net from producing a .deb package for everyone to use.

Point is Nvidia and Intel drivers already work. I'm not so sure about ATI which is already having suspend problems, no AIGLX, crap frame rates, and so on. You get the point.

Moreover, a video driver is more integrated in Ubuntu system(kernal module) than a .deb package. It's better if distro supports it.

---

### Post by cogadh on 2007-10-24
> **mysticmatrix said:**
> Point is Nvidia and Intel drivers already work. I'm not so sure about ATI which is already having suspend problems, no AIGLX, crap frame rates, and so on. You get the point.

Moreover, a video driver is more integrated in Ubuntu system(kernal module) than a .deb package. It's better if distro supports it.
Well the Nvidia drivers work, but I think you might find a few Intel users who would disagree with you when it comes to their drivers, it depends on how you define "work". 

Usually when a new version of a piece of software comes out after an Ubuntu release, the package will get included in the next release and if there is enough demand for it in the current release, they will make the package available as a backport. I'm not sure if they have ever done that with a driver though. 

Even if they don't package it or backport it, and you really need this new driver (I'm sure most ATI users do), you can still install it using ATI's install script. You'll probably end up having to re-install the driver every time there is a kernel update, as happens with Nvidia users who decide to use the latest and greatest driver from the Nvidia website, but at least you will have the functionality you want/need.

---

### Post by mysticmatrix on 2007-10-24
> **cogadh said:**
> Well the Nvidia drivers work, but I think you might find a few Intel users who would disagree with you when it comes to their drivers, it depends on how you define "work". 

Usually when a new version of a piece of software comes out after an Ubuntu release, the package will get included in the next release and if there is enough demand for it in the current release, they will make the package available as a backport. I'm not sure if they have ever done that with a driver though. 

Even if they don't package it or backport it, and you really need this new driver (I'm sure most ATI users do), you can still install it using ATI's install script. You'll probably end up having to re-install the driver every time there is a kernel update, as happens with Nvidia users who decide to use the latest and greatest driver from the Nvidia website, but at least you will have the functionality you want/need.

Quite right. But you'll notice that Compiz Fusion, for example, has blacklisted certain ATI card, purely due to request by Ubuntu developers.( At least this is what they mention on their webpage).
So ubuntu is a driving force in industry to how much hardware is supported, one way or other,

As for intel, they work perfectly till it comes to wine, which is fixed now in Gutsy(For me atkeast). By work, they work well with suspend, hibernate and most native games, like UT, serious Sam 2.

---

### Post by master_kernel on 2007-10-24
This should be fglrx-new... but still no support for the new API in the 2.6.23 kernel -- this makes developing KernelCheck slow down majorly because of the new API. There are some patches out there but I like to distribute "clean" programs.

---

### Post by yatt on 2007-10-25
> **mysticmatrix said:**
> Point is Nvidia and Intel drivers already work. I'm not so sure about ATI which is already having suspend problems, no AIGLX, crap frame rates, and so on. You get the point.

Moreover, a video driver is more integrated in Ubuntu system(kernal module) than a .deb package. It's better if distro supports it.The Ubuntu devs write scripts that ship with the fglrx installer that are used to create the packages. The installer is going to produce the same debs whether it is run by someone from getdeb, the Ubuntu team, or some other member of the community. The only real difference is an official Ubuntu deb wouldn't require you to backlist the fglrx module provided by linux-restricted-modules.

---

### Post by bluefightingcat on 2007-10-25
Hi,

It's seems in the end this quite a crap release. :( See this bugtracker at launchpad:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-driver/+bug/156325](https://bugs.launchpad.net/ubuntu/+source/fglrx-driver/+bug/156325)

BFC

---

### Post by sloggerkhan on 2007-10-25
Doesn't seem any worse than other fglrx drivers versions I've used. Far better than most, for me, actually.

---

