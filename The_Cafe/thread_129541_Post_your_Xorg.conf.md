---
title: "Post your Xorg.conf"
date: 2006-02-14
forum: The Cafe
---

### Post by poofyhairguy on 2006-02-14
Xorg.conf is one of the hardest parts of Linux. You have to hack it just right to get it to work....and that takes some time. Often the only way I get it to work is to look at others who got it to work then copy parts of theirs. All the guides in the world don't always help.

So if you have a xorg.conf that you have gotten to do something special, post it here.

I'll go first. Mine is for Nvidia cards. It allows for two monitors (using Twinview) that share a single desktop of the same resolution. Composite is also enabled and working.

---

### Post by mstlyevil on 2006-02-14
Here mine goes. The only modifications I made to it were the ones you posted in your how-to on installing kwin. The rest were generate upon install and by Nvidias utility when I compiled the latest Nvidia drivers.

[ATTACH]6128[/ATTACH]

---

### Post by Iandefor on 2006-02-14
Here ya go.

Enabled composite, NVIDIA official drivers. Probably done some other stuff.

---

### Post by fuscia on 2006-02-14
what is it?

---

### Post by bonzodog on 2006-02-14
xorg.conf, for the uninformed is the bit that controls the X desktop. It's the central configuration file, and it is quite long and complicated. Knowing how to hack the file and customise it without crashing X is classed as somewhat of an achievement, and once you learn it, you can consider yourself on the next stage up. I learnt about the intracacies of X through having used Slackware.

---

### Post by fuscia on 2006-02-14
[QUOTE=bonzodog]xorg.conf, for the uninformed is the bit that controls the X desktop. It's the central configuration file, and it is quite long and complicated. Knowing how to hack the file and customise it without crashing X is classed as somewhat of an achievement, and once you learn it, you can consider yourself on the next stage up. I learnt about the intracacies of X through having used Slackware.[/QUOTE]

hm! guess i'll stick to switching wms with reckless abandon. thanks for the explanation. you folks enjoy the rest of the thread now.

---

### Post by Virogenesis on 2006-02-14
heres mine now i'm using the nvidia drivers.
I've disabled that nvidia screen i like it but its unneeded.
I got composite enabled, my main monitor is on the right hand and my slave is on my left.

I've got 3 different sizes i can use they are 2560 x 1024 (dual mon), 1280 x 1024, 1024 x 768.

Done a few more mods aswell to it

---

### Post by kleeman on 2006-02-14
Here's mine.
It got corrupted today after I installed some new fonts using kcontrol.
Always keep a backup!!!!

---

### Post by TechSonic on 2006-02-14
HA! Mine PWNS all your resolutions.

Only changes I've made to mine was changing my colors to 16bit and added other resolution ranges.

---

### Post by Almighty on 2006-02-14
Ok, After much tweaking after a X crash I finally not only got X desktop back but it also has a second monitor in the mix. All the goodies are here including composite and twinview.

---

### Post by poofyhairguy on 2006-02-14
[QUOTE=bonzodog]xorg.conf, for the uninformed is the bit that controls the X desktop. It's the central configuration file, and it is quite long and complicated. Knowing how to hack the file and customise it without crashing X is classed as somewhat of an achievement, and once you learn it, you can consider yourself on the next stage up.[/QUOTE]

Great answer.

---

### Post by CompShrink on 2006-02-15
Geez, everyone so far with 2 monitors uses twinview? Someone's got to some love for dual-card dual-monitor setups.

If only mine wasn't half a world away. (quite litterally, actually...)

I also took the hard drive with the MBR, and grub, and put it in an external HDD case and brought it with me. So, I don't have the xorg conf, but that comp doesn't boot now, and I'm not on the other side of earth.

I might be able to bug a friend to pop a live cd in and grab it... probably not for several days, if at all...

---

