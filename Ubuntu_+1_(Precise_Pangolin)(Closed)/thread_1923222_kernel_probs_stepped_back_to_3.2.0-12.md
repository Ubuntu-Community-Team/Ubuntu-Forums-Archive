---
title: "kernel probs/ stepped back to 3.2.0-12"
date: 2012-02-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-02-10
Getting these pop-ups...

---

### Post by dino99 on 2012-02-10
checkmate :) might be a ram issue into the game

---

### Post by ventrical on 2012-02-10
> **dino99 said:**
> checkmate :) might be a ram issue into the game


Sorry.. I forgot to mention that I wasn't even playing Brutal Chess. (hasn't worked on this Dell since install).

  It just popped up out of nowhere.

I am running:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

the above adapter card.

 Could this be the problem? (because it worked ok with other distros). Hardware jockey will not detect it .. so perhaps I have the wrong driver. I tried the fglrx install/purge .. but no work.

Any ideas.

?

---

### Post by prusswan on 2012-02-10
hmm is this a desktop? ur problems are much worse compared to my physical install

---

### Post by dino99 on 2012-02-10
> **ventrical said:**
> Sorry.. I forgot to mention that I wasn't even playing Brutal Chess. (hasn't worked on this Dell since install).

  It just popped up out of nowhere.

I am running:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

the above adapter card.

 Could this be the problem? (because it worked ok with other distros). Hardware jockey will not detect it .. so perhaps I have the wrong driver. I tried the fglrx install/purge .. but no work.

Any ideas.

?

Are you sure that the chess process was not active ? check with system monitor or htop. About your graphic driver, is dkms installed ?

---

### Post by ventrical on 2012-02-10
> **dino99 said:**
> Are you sure that the chess process was not active ? check with system monitor or htop. About your graphic driver, is dkms installed ?

The chess process is not active.

  I just installed dkms:

```
ventrical@ventrical-OptiPlex-GX270:~$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnettle4 libx264-116 libx264-118 libaiksaurusgtk-1.2-0c2a
  libaiksaurus-1.2-0c2a libaccess-bridge-java-jni libgnutls28
  libaccess-bridge-java libgdata1.8-cil libmusicbrainz4c2a librhythmbox-core4
  libaiksaurus-1.2-data libept1 openoffice.org-common libvpx0 libhogweed2
  libmcs1 libreoffice-l10n-common flashplugin-downloader
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fakeroot patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  dkms fakeroot patch
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 247 kB of archives.
After this operation, 889 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main patch i386 2.6.1-3 [86.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main dkms all 2.2.0.3-1 [73.0 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main fakeroot i386 1.18.2-1 [87.9 kB]
Fetched 247 kB in 1s (159 kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75, <> line 3.)
debconf: falling back to frontend: Readline
Selecting previously unselected package patch.
(Reading database ... 397229 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-3_i386.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_i386.deb) ...
Processing triggers for man-db ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75.)
debconf: falling back to frontend: Readline
Setting up patch (2.6.1-3) ...
Setting up dkms (2.2.0.3-1) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
ventrical@ventrical-OptiPlex-GX270:~$ 
```

---

### Post by ventrical on 2012-02-10
I went to update on my other tower and these  (3.2.0-15) were held back.

 wow

 thanks..

camel2@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gstreamer0.10-plugins-bad libavcodec53 libavformat53 linux linux-generic
  linux-headers-generic linux-headers-generic-pae linux-image
  linux-image-generic linux-image-generic-pae

---

