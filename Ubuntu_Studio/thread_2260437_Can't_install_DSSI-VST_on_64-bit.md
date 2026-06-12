---
title: "Can't install DSSI-VST on 64-bit?"
date: 2015-01-12
forum: Ubuntu Studio
---

### Post by marseille2 on 2015-01-12
I can't install DSS-VST on Trusty without automatically uninstalling Ardour 3, and a bunch of other UbuntuStudio programs. Is there a solution to this?

---

### Post by jejeman on 2015-01-12
Compile it yourself.

---

### Post by bhilmers2 on 2015-01-12
> **jejeman said:**
> Compile it yourself.Please ignore this embarassingly unhelpful response from jejeman.

DSSI-VST is currently broken in the Ubuntu repositories. The package is now being maintained and developed by falkTX, the creator of the KXStudio audio distribution. [Here is the package on GitHub]("https://github.com/falkTX/dssi-vst"). Apparently there are some tricks for getting it to work, like you have to instally the bridge first then the host or something like that. I've tried to compile this myself and gave up after a couple hours of errors. Also, the best place for audio support in Ubuntu Studio is not these forums but [LinuxMusicians.com]("http://linuxmusicians.com"). Good luck!

---

### Post by marseille2 on 2015-01-12
Thank-you both! I did get to the point of compiling of it myself, but I didn't since my system won't install these dependencies (suggested at GitHub):
gcc-multilib and g++-multilib

Is this a common problem? BTW... I will look through LinuxMusicians some more, but feedback on those package conflicts is good.

---

