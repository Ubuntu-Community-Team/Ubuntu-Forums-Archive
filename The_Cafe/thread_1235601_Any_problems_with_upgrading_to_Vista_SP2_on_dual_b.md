---
title: "Any problems with upgrading to Vista SP2 on dual boot laptop?"
date: 2009-08-09
forum: The Cafe
---

### Post by I-75 on 2009-08-09
Any problems with upgrading to Vista SP2 on dual boot laptop?

I have a Compaq 762 NR laptop with Vista SP1 Home Premium and Ubuntu 9.04. If I upgrade to Vista SP2...will it cause any problems with booting or will it hose either OS? 

 

 


Thanks.........

---

### Post by bobbob1016 on 2009-08-09
That depends on whether you have BitLocker or whatever it's called installed.  And if you did a full install or a Wubi install.

It *should* be fine though.  The worst you'd have to do is reinstall grub [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Upgrading service packs can be dangerous to Vista though, so your Vista could be hosed, but I haven't had any issues upgrading other people's Vistas to SP1 or SP2, same with XP.

---

### Post by Joeb454 on 2009-08-09
I upgraded to Vista SP2 RC a while back on my laptop, and it was fine.

If I remember rightly, I did have to reinstall GRUB though, but the guide is incredibly easy to follow, and painless (you'll be pleased to know).

---

### Post by I-75 on 2009-08-09
Thank you for your replies, I originally shrunk the Vista partition using Vista's partition shrinker and then installed Ubuntu on the freed partition. 

 Windows often restarts while doing upgrades or critical updates, since after a restart, instead of going  back to Vista it goes to grub...I wasn't sure if that would be a problem if I was going to upgrade to SP2.

 I don't have a Vista DVD, so if something got messed up..I couldn't repair it. If I have any issues, I'll ask for help..thanks again for your answers.

---

