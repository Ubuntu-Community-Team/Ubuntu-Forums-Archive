---
title: "Does anybody have a grub live-cd? [URGENT!!!]"
date: 2009-03-02
forum: The Cafe
---

### Post by dragos240 on 2009-03-02
To make a long story short(er), i installed arch on another partition and i overrided the ubuntu grub bootloader, it happened to be an older version of grub that didn't support the uuid command, does anybody have a grub livecd iso?

---

### Post by RATM_Owns on 2009-03-02
Why did you download a 10 year old CD then? :P

Run `pacman -Syu` in Arch. Then reinstall GRUB.

EDIT: Or you could reboot in the Arch CD, run `pacman -Sy grub` and reinstall it from there.

---

### Post by dragos240 on 2009-03-02
> **RATM_Owns said:**
> Why did you download a 10 year old CD then? :P

Run `pacman -Syu` in Arch. Then reinstall GRUB.

EDIT: Or you could reboot in the Arch CD, run `pacman -Sy grub` and reinstall it from there.

Problem though, it didn't come with wireless tools, and i can't connect to a network... :(

---

### Post by cardinals_fan on 2009-03-02
> **dragos240 said:**
> Problem though, it didn't come with wireless tools, and i can't connect to a network... :(
You needed to check wireless_tools during package installation.  Do it over ;)

---

### Post by dragos240 on 2009-03-03
> **cardinals_fan said:**
> You needed to check wireless_tools during package installation.  Do it over ;)

Hmm, they had that? I thought i checked everything, interesting...

---

### Post by FuturePilot on 2009-03-03
I think what you want is the [Super Grub Disk]("http://www.supergrubdisk.org/index.php?pid=5")

---

### Post by dragos240 on 2009-03-03
Fixed it, never mind, now i am in my own ubuntu /home sweet /home.

---

