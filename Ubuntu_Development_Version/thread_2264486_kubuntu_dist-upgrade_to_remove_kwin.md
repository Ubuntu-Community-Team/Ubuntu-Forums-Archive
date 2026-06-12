---
title: "kubuntu dist-upgrade to remove kwin"
date: 2015-02-07
forum: Ubuntu Development Version
---

### Post by buzzmandt on 2015-02-07
my current dist-upgrade wants to remove kwin, and I don't see a viable kwin alternate wanting to be installed. So, for now I will just upgrade.

anyone?

> The following packages will be REMOVED:
  kwin libkwin4-effect-builtins1 libkwinglutils5
The following NEW packages will be installed:
  gcc-5-base gcc-5-base:i386 libabw-0.1-1 libcmis-0.5-5 libe-book-0.1-1 libeot0 libfreehand-0.1-1 libicu52:i386 libkwinglutils6 libllvm3.6 libllvm3.6:i386 libndp0
  libopenimageio1.4 linux-headers-3.18.0-12 linux-headers-3.18.0-12-generic linux-image-3.18.0-12-generic linux-image-extra-3.18.0-12-generic
The following packages will be upgraded:
  blender blender-data cpp-4.9 g++-4.9 gcc-4.9 gcc-4.9-base gcc-4.9-base:i386 kwin-data lib32gcc1 lib32stdc++6 libasan1 libatomic1 libcilkrts5 libegl1-mesa libgbm1
  libgcc-4.9-dev libgcc1 libgcc1:i386 libgfortran3 libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-dri-dbg libgomp1 libitm1 liblsan0 libquadmath0 libreoffice
  libreoffice-base libreoffice-base-core libreoffice-base-drivers libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-impress libreoffice-kde
  libreoffice-math libreoffice-style-oxygen libreoffice-writer libstdc++-4.9-dev libstdc++6 libstdc++6:i386 libtsan0 libubsan0 libwayland-egl1-mesa libxatracker2 libxml2
  libxml2:i386 linux-generic linux-headers-generic linux-image-generic network-manager network-manager-pptp ppp python3-uno
55 upgraded, 17 newly installed, 3 to remove and 0 not upgraded.
Need to get 280 MB of archives.
After this operation, 380 MB of additional disk space will be used.
Do you want to continue? [Y/n] n 


---

### Post by grahammechanical on 2015-02-07
As I understand things, dist-upgrade will pull in packages that are being held back. And it may be that they are being held back because the needed replacement packages are not yet in the archive.

I once ran dist-upgrade and lost ubuntu-desktop. So, I rarely use dist-upgrade. I did use it a couple of weeks ago because I was impatient to get the Linux 3.18 kernel. I got the kernel alright and I did not lose the desktop but I did get system error messages as the desktop loaded. They have only just cleared up.

Regards.

---

### Post by zika on 2015-02-08
Dist-upgrade, simply put, just enables You to (re)solve situation when there are new packages that other packages are dependent of that should be installed. Of course, due to dependencies set in packages there are situations that generate removal of packages that are needed because those dependencies are not yet met. Proposed repository is a great remedy for that since all the packages are waiting there until all there dependencies are met. Even though, You do need dist-upgrade but the danger of using it is diminished with introduction of proposed repository. So, again, dist-upgrade is not a villain it is a tool. Even for (us) impatient ones... ;) Aptitude's dist-upgrade is a bit more informative and I do use it in cases when I do not clearly see what is the reason for unwanted removal.

---

### Post by buzzmandt on 2015-02-08
agreed zika, I NEED dist-upgrade sometimes to pull in the new stuff. But I've been doing this long enough to know to watch what gets removed. Like in this case kwin to be removed. RED FLAG!! No kwin replacement installing DOUBLE RED FLAG!! lol. However, when somethingLIB1.2 is going to be removed but somethingLIB1.3 will be installed you're ok. Just for the record I'm a long time dev user and long time dist-upgrader

As to the OP, I was just wondering if anyone else on kubuntu what getting this sticky spot. I hate waiting LOL

---

### Post by xc3RnbFO8P on 2015-02-08
Say no, 
if I try to remove libkwin4 effect, it wants to remove Kubuntu Desktop.
I got libkwin4 effect and libkw.in6 effect installed, version 4:5.2.0.1-=ubuntu3.
It is normal if nothings works :)

---

### Post by zika on 2015-02-08
> **buzzmandt said:**
> agreed zika, I NEED dist-upgrade sometimes to pull in the new stuff. But [SIZE=4]I've been doing this long enough to know to watch what gets removed[/SIZE]. Like in this case kwin to be removed. RED FLAG!! No kwin replacement installing DOUBLE RED FLAG!! lol. However, when somethingLIB1.2 is going to be removed but somethingLIB1.3 will be installed you're ok. Just for the record I'm a long time dev user and long time dist-upgrader[img]http://www.sherv.net/cm/emoticons/hand-gestures/thumbs-up-hand-gesture-smiley-emoticon.gif[/img]
> **buzzmandt said:**
> As to the OP, I was just wondering if anyone else on kubuntu what getting this sticky spot. I hate waiting LOLAren't You OP? ;)

---

### Post by buzzmandt on 2015-02-08
just saying as to the 'original post'

---

