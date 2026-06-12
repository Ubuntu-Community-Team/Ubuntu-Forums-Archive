---
title: "Upgrading from 8.04 to 10.10 Server Edition"
date: 2011-02-08
forum: Server Platforms
---

### Post by mjetpax on 2011-02-08
Hi,

I need to upgrade my hobby server from 8.04 to 10.10. I tried to use the "Network upgrade for Ubuntu servers." Unfortunately, while trying this technique, I skipped clean over version 9. This left my server in a sorry state and it would not launch Ubuntu. It had something to do with Grub skipping a vital version upgrade.

Luckily for me, I had a full back up to fall back on. But, I still want to upgrade. I think I need to upgrade to version 9 first and then to version 10. If someone could help point me in the right direction, I promise I will keep things up to date at all times in the future. :)

Thanks a bunch!

---

### Post by matt_symes on 2011-02-08
Hi 

8.04 used Grub (legacy grub) and 10.10 uses Grub 2. Have a read of this.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Kind regards

---

### Post by mjetpax on 2011-02-09
Hi,

So, according to the GRUB 2 page, I can upgrade from GRUB to GRUB 2 while I am still running 8.04.

"...Releases such as Ubuntu 9.04 Jaunty Jackalope which are upgraded to 9.10 will retain GRUB unless the user elects to upgrade to GRUB 2. Previous releases of Ubuntu can be upgraded to GRUB 2 if the user desires..."

Then I would be able to upgrade to 10.10 without fear of boot failure. Does this sound correct?

Thanks again.

---

### Post by matt_symes on 2011-02-09
Hi

I think the answer is generally yes with some provisos. Having legacy grub files kicking around can cause problems with grub2. However the fix is generally quite easy if you do have problems. Just make sure you have a LiveCD/USB handy in case there are problems.

I generally prefer a fresh install when upgrading anyway as there can be other problems. For some it goes well but others have problems with an non fresh upgrade.

Kind regards

---

