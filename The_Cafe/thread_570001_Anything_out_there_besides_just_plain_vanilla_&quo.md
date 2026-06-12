---
title: "Anything out there besides just plain vanilla &quot;Volume Control&quot;?"
date: 2007-10-07
forum: The Cafe
---

### Post by RAV TUX on 2007-10-07
Anything out there besides just plain vanilla "Volume Control"?

Looking for a seperate from players, system wide volume control, something other then Volume Control.

Anything?

---

### Post by p_quarles on 2007-10-07
> **RAV TUX said:**
> Anything out there besides just plain vanilla "Volume Control"?

Looking for a seperate from players, system wide volume control, something other then Volume Control.

Anything?
See attached. :)

In seriousness, though, whenever I want the noise, I hook up my sound card to my stereo's auxilliary ports.

---

### Post by itsbradman on 2007-10-07
you can use alsamixer.  what controls do you need?

---

### Post by RAV TUX on 2007-10-07
> **itsbradman said:**
> you can use alsamixer.  what controls do you need?Same as Volume Control just supped up.

---

### Post by RAV TUX on 2007-10-07
> **itsbradman said:**
> you can use alsamixer.  what controls do you need?


Ok I have installed this:

```
ravtux@CafeLinux:~$ sudo apt-get install alsa-utils alsamixergui gnome-alsamixer
Reading package lists... Done
Building dependency tree
Reading state information... Done
alsa-utils is already the newest version.
The following packages were automatically installed and are no longer required:
  libxtrap-dev libxmuu-dev libxv-dev x11proto-video-dev x11proto-trap-dev
  x11proto-record-dev x11proto-randr-dev libxpm-dev libxrandr-dev libxtst-dev
  x-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libfltk1.1
The following NEW packages will be installed:
  alsamixergui gnome-alsamixer libfltk1.1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 484kB of archives.
After unpacking 1688kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy/main libfltk1.1 1.1.7-4build1 [399kB]
Get:2 http://us.archive.ubuntu.com gutsy/universe alsamixergui 0.9.0rc2-1-9 [30.0kB]
Get:3 http://us.archive.ubuntu.com gutsy/universe gnome-alsamixer 0.9.7~cvs.20060916.ds.1-1 [55.6kB]
Fetched 484kB in 3s (140kB/s)
Selecting previously deselected package libfltk1.1.
(Reading database ... 165097 files and directories currently installed.)
Unpacking libfltk1.1 (from .../libfltk1.1_1.1.7-4build1_i386.deb) ...
Selecting previously deselected package alsamixergui.
Unpacking alsamixergui (from .../alsamixergui_0.9.0rc2-1-9_i386.deb) ...
Selecting previously deselected package gnome-alsamixer.
Unpacking gnome-alsamixer (from .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-1_i386.deb) ...
Setting up libfltk1.1 (1.1.7-4build1) ...

Setting up alsamixergui (0.9.0rc2-1-9) ...

Setting up gnome-alsamixer (0.9.7~cvs.20060916.ds.1-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

---

### Post by Bungo Pony on 2007-10-07
I don't really have a problem with the default volume control. Just point your mouse to the speaker icon and turn your mouse wheel. Nice and simple!

---

### Post by Kingsley on 2007-10-07
> **Bungo Pony said:**
> I don't really have a problem with the default volume control. Just point your mouse to the speaker icon and turn your mouse wheel. Nice and simple!
Sir, that's amazing advice. I'll never click on my volume icon AGAIN! (except if I want to quickly mute)

---

### Post by ryno519 on 2007-10-07
Compiz fusion + multimedia keyboard controls = excellent volume manager :)

---

### Post by RAV TUX on 2007-10-07
> **itsbradman said:**
> you can use alsamixer.  what controls do you need?

Hey Thanks the ALSA-Mixer is exactly what I was looking for, as anyone can see from the screenshot below it is much more feature rich then a plain vanilla "Volume Control", I have even added a shortcut to ALSA-Mixer on the iBar on my Shelf:

**ALSA Mixer in Xubuntu 7.10 (Smoke e17 Theme, Circuit background)**
[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_snapshot65.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?album=lastup&cat=0&pos=0")

---

### Post by RAV TUX on 2007-10-07
> **RAV TUX said:**
> Hey Thanks the ALSA-Mixer is exactly what I was looking for, as anyone can see from the screenshot below it is much more feature rich then a plain vanilla "Volume Control", I have even added a shortcut to ALSA-Mixer on the iBar on my Shelf:

**ALSA Mixer in Xubuntu 7.10 (Smoke e17 Theme, Circuit background)**
[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_snapshot65.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?album=lastup&cat=0&pos=0")


Here is another Screenshot of the ALSA-Mixer with the Songbird:

**                                                 Songbird 0.2.5.1, ALSA-Mixer in Xubuntu 7.10 (e17 Smoke Theme)**
[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_snapshot66.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?album=lastup&cat=0&pos=0")

---

