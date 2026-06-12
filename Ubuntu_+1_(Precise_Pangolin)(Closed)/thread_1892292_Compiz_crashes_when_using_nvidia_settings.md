---
title: "Compiz crashes when using nvidia settings"
date: 2011-12-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wolfen69 on 2011-12-07
I'm trying to get Twinview working, but when I hit *Apply*, both screens become garbled and unusable. Anyone have any input?

---

### Post by cariboo on 2011-12-07
I have the same thing, but if I wait a bit, it clears up, and I can then save the new /etc/X11/xorg.conf. I'm running a 9400GT using nvidia-current from the repositories.

---

### Post by wolfen69 on 2011-12-07
Waiting doesn't help for me. It makes the desktop completely unusable, and I have to hard reboot. I'm using a 430GT.

---

### Post by ventrical on 2011-12-08
I had often rebooted stalled compiz  when all I had to do was wait. Sometimes the wait state actually emulates a crash or hang.. but with compiz (who knows) it seems to take a little extra time... and Precise (as well as it's predecessor) had a big problem recognizing legacy LCD screens (that may be a little older) with higher end nvidia and Ati radeon cards.

  Often all I had to do was switch monitors and volia'

For the most part Precise fares well  but there is still that nagging problem recognizing some monitors.

I'm not sure if it as a bug or a hardware compatibilty issue.

---

### Post by wolfen69 on 2011-12-08
I'll give it another try, but if I'm going to use 12.04 for bug reporting, I *need* 2 monitors. Btw, I did report it as a bug.

---

### Post by wolfen69 on 2011-12-09
I finally got twinview working and can get on with testing. I removed the current version updates drivers and installed the regular current version. Compiz kept crashing, but I see the devs are well aware of it, and it should be fixed soon.

---

### Post by ventrical on 2011-12-10
Thanks for the update wolfen.

---

