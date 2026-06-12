---
title: "Galago's graphics performance issue after installing Intel video driver"
date: 2013-08-30
forum: System76 Support
---

### Post by javsalgar on 2013-08-30
Hello everyone,

In order to solve the problems reported in posts like this: [http://ubuntuforums.org/showthread.php?t=2168352](http://ubuntuforums.org/showthread.php?t=2168352) I installed Intel's video driver in my Galago. After installing it, the problem is solved indeed, but I experience that graphics performance is slower than before. I tested it in, for example, Team Fortress 2 and it works slower, and it also happens with Unity's User Interface. Has this happened to anyone else? How did you sort it out?

Thank you in advance

---

### Post by clarkaddison on 2013-08-30
I too have installed the 01 drivers, and also agree the graphics performance is not what I would expect.  The fade-in and fade-out of the Unity dash has a very noticeable lag most of the time.  

The repository only has Mesa 9.1 in it, and supposedly mesa 9.2 has a bunch of haswell performance improvements.  So I just chalk it up to these drivers still being a work in progress and was going to tough it out until next release.  If you're determined you want a fix now, perhaps you can figure out how to get 9.2 on Ubuntu, or maybe install 13.10 or something else a little more bleeding edge that would have it.  I haven't done these things yet though so I make no promises!  Has anyone else?

---

### Post by isantop on 2013-08-30
Our preliminary testing with Ubuntu Saucy is indicating a performance gain of around 2x compared to 13.04. We strongly recommend all Haswell users upgrade to 13.10 once it's been released.

---

### Post by makebelieve2 on 2013-08-31
Did you try a mix of intels latest drivers, mesa 9.2 and kernel 3.10.10(latest stable), perhaps try latest 3.11RC7 kernel also?

[http://linuxg.net/how-to-install-the-linux-kernel-3-10-10-on-ubuntu-linux-mint-elementary-os-debian-and-derivates/](http://linuxg.net/how-to-install-the-linux-kernel-3-10-10-on-ubuntu-linux-mint-elementary-os-debian-and-derivates/)

for mesa:
[COLOR=#000000][B][FONT=Arial]
[/FONT][COLOR=#222222][FONT=Ubuntu Mono]sudo add-apt-repository [/FONT][/COLOR][/B][/COLOR]ppa:xorg-edgers/ppa
sudo apt-get update && sudo apt-get upgrade

To see what Mesa version you have:

[COLOR=#000000][FONT=Arial]**glxinfo | grep "OpenGL version"**[/FONT][/COLOR]

---

### Post by javsalgar on 2013-08-31
Thank you all for the info. I think I will wait for the next release. Thank you!

---

### Post by treyhunner on 2013-09-10
I am also experiencing graphics performance issues after installing the Intel driver ([from this thread]("http://ubuntuforums.org/showthread.php?t=2168352")).

I removed the PPA and downgraded the packages to remove the new driver using ppa-purge:

```
sudo apt-get install ppa-purge
sudo ppa-purge -s download.01.org ppa:gfx/ubuntu
```

This seems to have fixed my performance issues.

---

### Post by mwinter-z on 2013-09-24
I downgraded as per the instructions and my computer is still acting very funky and slow. Also, strangely enough the webcam is still working with those other apps.

---

### Post by mwinter-z on 2013-09-24
just an update here: I forgot to mention that I was on the low-latency kernel. even after purge that was really, really slow/affected. I rebooted into the standard kernel and all seems fine (at least for the past hour - I will update if that changes). And in both cases, the webcam is still working with jitsi. So... the purge did not help the low latency kernel. Also, I realized that I had not tested the upgrade with the regular kernel. So I am tempted to reinstall the new intel driver and see if things are still ok with the regular kernel...

---

