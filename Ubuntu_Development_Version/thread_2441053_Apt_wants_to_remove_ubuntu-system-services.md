---
title: "Apt wants to remove ubuntu-system-services"
date: 2020-04-18
forum: Ubuntu Development Version
---

### Post by hoxaen on 2020-04-18
I've been riding the Focal Fossa train for a few days now: from Beta to RC. Every morning when I turn on my computer, I do the regular apt-get update, apt-get upgrade. If I notice that some packages were being held back, I will do an apt-get --with-new-pkgs upgrade to pull everything in. However, a day or two ago, I noticed that after everything has been upgraded / installed, apt wants to remove a few packages, namely "ubuntu-system-service x11proto-composite-dev x11proto-damage-dev x11proto-fixes-dev." Normally I  would just apt autoremove without much thought, but seeing ubuntu-system-services in the list gave me some pause. I have yet to figure out why that package is selected as no longer being used, and searching google hasn't brought me any closer to an answer.

I suppose my question is if I should remove the package, or is there something I can do to fix apt from wanting to remove it? The package seems to be an important part of the Ubuntu system, and I do not want to remove it arbitrarily.

---

### Post by corradoventu on 2020-04-18
I have Ubuntu 20.04 fresh installed from recent ISO and ubuntu-system-services does not exist, may be comes from your old install
```
corrado@corrado-x5-ff-0409:~$ dpkg -l | grep  ubuntu-system-services
corrado@corrado-x5-ff-0409:~$
```

---

### Post by pablosquared on 2020-04-18
Not present on my 20.04 system either.

```

ablo@Ubuntu:~$ dpkg -l | grep  ubuntu-system-services
pablo@Ubuntu:~$ 

```

---

### Post by hoxaen on 2020-04-18
Interesting! I suppose it must have been on the Beta ISO but at some point was removed. Thanks for checking on your systems, I feel more at east at removing the package now.

---

### Post by tokyobadger on 2020-04-18
```
tokyobadger@box1:~$ dpkg -l | grep  ubuntu-system-services
tokyobadger@box1:~$
```
Confirming that on the current 20.04 Beta, that package does not exist.

The original install was 13.10 Saucy Salamander. Upgraded regularly.

**Edited** for typos

---

