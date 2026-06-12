---
title: "Updated Wine+WinePulse"
date: 2010-10-03
forum: Wine
---

### Post by CFet on 2010-10-03
Greetings,
Looking for an updated _integrated_ package of Wine+Winepulse. Preferably Wine1.2 or later. I'm horrible at patching, hence the integrated part.
Cheers.

---

### Post by beastrace91 on 2010-10-04
PPA for Wine 1.2 with pulse audio support - 

```
sudo add-apt-repository ppa:c-korn/ppa
sudo apt-get update && sudo apt-get upgrade
```

~Jeff

---

### Post by runesvend on 2011-01-25
I have the newest version (as per January 25 2010) of wine1.3 with the WinePulse patches up in my PPA:
[https://launchpad.net/~runeks/+archive/winepulse/](https://launchpad.net/~runeks/+archive/winepulse/)

```
sudo add-apt-repository ppa:runeks/winepulse
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install wine1.3
```

Please notice that I have no plans to update this package as the packages in the ubuntu-wine PPA are updated.t

---

