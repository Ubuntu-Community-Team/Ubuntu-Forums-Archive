---
title: "ran Upgrade last night now I am stuck at splash"
date: 2011-10-20
forum: Virtualisation
---

### Post by mrhobbeys on 2011-10-20
I am really sorry I don't know which version I upgraded from but I use Ubuntu 64x for development inside of virtualbox. Last night I upgraded to 11.10 everything seemed fine until the reboot, where I became stuck at the splash screen. I tried loading a live CD freshly downloaded and ran fsck which found errors but I get the same results on startup. I then tried running fsck from another terminal it didn't find any errors.

Last I tried booting recovery mode and ran a repair. It seemed to be doing something but nothing ever got downloaded so I am not sure what happened.

---

### Post by mrhobbeys on 2011-10-20
After trying tons of things the one that finally worked was to rm /etc/X11/xorg.conf

Go figure, easy.

---

