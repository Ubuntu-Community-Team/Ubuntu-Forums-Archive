---
title: "Packages &quot;kept back&quot;"
date: 2008-05-30
forum: Server Platforms
---

### Post by popie on 2008-05-30
I'm running v8.04 server, and I did an apt-get update, and apt-get upgrade (a couple days ago, and again today with same results). It seems that some packages aren't updating:

```
The following packages have been kept back:
  linux-image-server linux-server openssh-client openssh-server
```

Can someone tell me why this is happening, and what I should do when I see this? Thanks.

---

### Post by bmathis on 2008-05-30
those are kernal and system software updates. You'll need to do a 

> sudo aptitude dist-upgrade or sudo aptitude safe-upgrade

to install them. The kernal updates will require a reboot.

---

### Post by popie on 2008-05-30
Thanks. dist-upgrade did the trick.

I rebooted after the kernal update, but there was no prompt about having to do that, as with the gnome updater. I guess the command line apt-get doesn't have that feature. Thanks for the reminder though. Cheers.

---

### Post by energycore on 2008-09-29
:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  bovo juk katomic kbattleship kblackbox kblocks kbounce kbreakout kcron
  kde-window-manager kdeadmin kdebase-workspace kdebase-workspace-bin
  kdebase-workspace-data kdebase-workspace-libs4+5 kdegames kdemultimedia
  kdemultimedia-kio-plugins kdewebdev-kde4 kdiamond kdm kfilereplace-kde4
  kfourinline kgoldrunner kimagemapeditor-kde4 kiriki kjumpingcube klines
  klinkstatus-kde4 klipper kmag kmahjongg kmines kmix kmousetool kmouth
  knetwalk knetworkconf kolf kollision konquest kpat kreversi ksame kscd
  kshisen ksirk kspaceduel ksquares ksudoku ksysguard ksystemlog kttsd
  ktuberling kubrick kuser libkcddb4 libkdecorations4 libkdegames4
  libkwineffects1 libplasma2 lskat systemsettings
0 upgraded, 0 newly installed, 0 to remove and 63 not upgraded.


I'm have about the same question, except that it didn't help when using dist-upgrade..

---

