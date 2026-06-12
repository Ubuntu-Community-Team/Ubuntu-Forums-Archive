---
title: "can not boot 16.04"
date: 2016-04-05
forum: Ubuntu Development Version
---

### Post by erkanea on 2016-04-05
Hello,
My laptop won't boot 16.04, while trying to get into live desktop just after, all 5 white dots turns to orange, computer hangs, num lock won't even work. environment is :

16.04 latest beta (dated 1st april)
msi gl62
hm170 chipset
i7 6700hq cpu
nvidia 940mx discret gpu
intel 3165 wi-fi adapter

any help is appriciated

---

### Post by dino99 on 2016-04-05
The first thing i'm proposing, is to set the bios setting to use only the intel gpu; then you should be able to boot. The 940m chipset has recently been added to the 4.5 kernel (explaining your problem as 16.04 only has 4.4 kernel).

---

### Post by erkanea on 2016-04-05
> **dino99 said:**
> The first thing i'm proposing, is to set the bios setting to use only the intel gpu; then you should be able to boot. The 940m chipset has recently been added to the 4.5 kernel (explaining your problem as 16.04 only has 4.4 kernel).

i wish there was such an option in my bios but there isn't. by the way, older kernel versions are able to boot but without wifi detected. i know that intel 3165 support has been added in kernel 4.1

---

### Post by mc4man on 2016-04-05
Does that laptop have optimus enabled? (most laptops with nvidia do but not all.
If so then nvidia isn't a factor as it would be using the intel graphics for live & initial install.

My skylake i7 with a 940m works fine with 16.04, at least when using the IGP, as far as nvidia drivers different story, only the 358 drivers work, earlier & later are a no go.

---

### Post by Bucky Ball on 2016-04-05
When you boot from the install disk/USB, you get to the purple screen with the icon at the bottom, hit a key. This should take you to an options screen. Hit F6 and you should see a pop-up menu. Choose 'nomodeset' and continue with 'Try Ubuntu'. Any luck?

---

### Post by erkanea on 2016-04-06
> **Bucky Ball said:**
> When you boot from the install disk/USB, you get to the purple screen with the icon at the bottom, hit a key. This should take you to an options screen. Hit F6 and you should see a pop-up menu. Choose 'nomodeset' and continue with 'Try Ubuntu'. Any luck?

thanks for the information. indeed nomodeset helped to boot in to live media but now i get a compiz error which is flashing very fast, reading the error was another challenge. even after closing error message, there is just nothing on the screen.

I think I will try mint 17.3, only problem I noticed with it was wifi not being detected, I will install Mint 17.3 and try to upgrade kernel 4.5. At least I have an image backup of current windows, although I get really pissed of with windows, it works at least.

I will report after trying kernel 4.5

---

### Post by Bucky Ball on 2016-04-06
Remember this is a Ubuntu forum on a thread regarding Ubuntu Xenial 16.04 LTS. Adventures down the Mint road best posted on the Mint forums or in the Mint sub-fora here. ;)

---

### Post by erkanea on 2016-04-06
> **Bucky Ball said:**
> Remember this is a Ubuntu forum on a thread regarding Ubuntu Xenial 16.04 LTS. Adventures down the Mint road best posted on the Mint forums or in the Mint sub-fora here. ;)

thank you, I tried a few different distros and I couldn't succeed with any. I will wait for official release of xenial.

---

### Post by grahammechanical on 2016-04-06
With a 26 week release schedule Ubuntu gets the latest kernels & drivers with every new release. When running the development version we get advance contact with the newer hardware stack. I do not think the same can be said about distributions that are built on Ubuntu released versions.

Regards

---

