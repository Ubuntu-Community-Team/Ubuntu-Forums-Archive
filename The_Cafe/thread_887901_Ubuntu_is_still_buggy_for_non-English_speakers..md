---
title: "Ubuntu is still buggy for non-English speakers."
date: 2008-08-12
forum: The Cafe
---

### Post by Masoris on 2008-08-12
It is true that Ubuntu is buggy enough for non-English speakers. I continuously found critical bug on launchpad on every Ubuntu release.

Here is some crazy bugs.

**In Ubuntu 7.10:**
1. [https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104)
In fresh install, if you use SCIM to input non-European language, you can type nothing on firefox, and some softwares. If you tried to type something the software freeze. (This bug fixed on March 2008 )

2. [https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/173861](https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/173861)
If you installed a Microsoft East Asian font, and you are use that font as default, after security upgrading, you can't boot on GNOME. This bug gave panic for many Korean and Chinese Ubuntu users. (This bug fixed two month later after bug reporting)

**In Ubuntu 8.04**
3. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277)
If you use auto login, you'll lost keyboard setting every reboot. Or you can't change keyboard layout. (This bug is still not fixed)

Because of these, I can't recommend Ubnutu to other people. :(

---

### Post by Catharina on 2008-08-12
So I am curious. What bug free OS are you advising now to people?

---

### Post by Mr. Picklesworth on 2008-08-12
I imagine programs like Firefox and OpenOffice cause issues with SCIM. Have you tried Epiphany for your web browsing? It may give better results. If not the one in Ubuntu's repositories, the Webkit version of Epiphany is floating around in some Launchpad PPAs like [this one]("https://edge.launchpad.net/~michelinux/+archive"). It is not finished yet, but it could be worth knowing whether it works!

---

### Post by init1 on 2008-08-12
> **Catharina said:**
> So I am curious. What bug free OS are you advising now to people?
No OS is bug free, but Ubuntu has a LOT more bugs than Debian.

---

### Post by FuturePilot on 2008-08-12
According to the third bug you listed there with the keyboard settings issue, it appears it affects multiple distros, so I fail to see your argument that it's just Ubuntu that is buggy for non-English speakers.

---

### Post by Neurotripsick on 2008-08-12
I tried the spanish version of xubuntu a week or 2 ago (Im from Chile) and I must say that it was considerably more buggy than the regular english one. Lots of programs didnt work the way they were supposed to, and overall it felt slower and different. So today Im back to your everyday english speaking xubuntu.

---

### Post by Dremora on 2008-08-12
> **init1 said:**
> No OS is bug free, but Ubuntu has a LOT more bugs than Debian.

And Fedora is guaranteed to have more bugs than Ubuntu....

I would hope that after backporting bugfixes to a kernel thats outdated by 2 years, that Debian is pretty stable.

---

