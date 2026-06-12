---
title: "apt-get fully dead/broken"
date: 2004-12-05
forum: Repositories &amp; Backports
---

### Post by Quest-Master on 2004-12-05
I tried to install mplayer today thinking Totem couldn't play videos encoded with w32codecs.

Seems I was wrong and Totem works perfectly fine.

However, whenever I try to install/remove or do ANYTHING with apt-get, it returns the same error continuously:

> You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libswt-pocketpc3-java: Depends: libswt-pocketpc3-jni (= 3.0-2) but it is not going to be installed
  mplayer-586: Depends: liblame0 (>= 3.96-sarge1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

However, when I try to install liblame0, so I can get apt-get working again, I get

> Unpacking liblame0 (from .../liblame0_3.96.1-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmp3lame.so.0.0.0', which is also in package libmp3lame0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


MPlayer has been installed, however it doesn't work, so it's useless. I just want to get rid of it now and get apt-get working again. I feel really handicapped without it.

---

### Post by az on 2004-12-05
You have buggered dependancies.  One package is from an unofficial repository so these things happen.  You need to do 
sudo apt-get -f install

For it to fix itself.  Try finding a different version (or repository) for the package that it gets rid of...
One that will work.

---

### Post by jdong on 2004-12-07
[QUOTE=Quest-Master]I tried to install mplayer today thinking Totem couldn't play videos encoded with w32codecs.

Seems I was wrong and Totem works perfectly fine.

However, whenever I try to install/remove or do ANYTHING with apt-get, it returns the same error continuously:



However, when I try to install liblame0, so I can get apt-get working again, I get



MPlayer has been installed, however it doesn't work, so it's useless. I just want to get rid of it now and get apt-get working again. I feel really handicapped without it.[/QUOTE]

Do this:

**dpkg --force-all -i /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb**

**apt-get -f install**

---

