---
title: "Do Updates Add or Replace Files?"
date: 2010-03-06
forum: Ubuntu One (CLOSED)
---

### Post by emagine on 2010-03-06
Hello everyone,

I just have a quick question.  When you install updates from the update manager, some of those file size can add up to over 200 MB of files just from one set of updates.  Now, does this mean that it will take up 200 MB on my hard drive or what?  The reason i ask is because it seems these updates could take up a lot of space on a hard drive.  When ubuntu is updated, are these updates I am installing being added or are they replacing out of date files? This goes for updating software as well, are things being added, or just replaced?

---

### Post by 2hot6ft2 on 2010-03-06
> **emagine said:**
> Hello everyone,

I just have a quick question.  When you install updates from the update manager, some of those file size can add up to over 200 MB of files just from one set of updates.  Now, does this mean that it will take up 200 MB on my hard drive or what?  The reason i ask is because it seems these updates could take up a lot of space on a hard drive.  When ubuntu is updated, are these updates I am installing being added or are they replacing out of date files? This goes for updating software as well, are things being added, or just replaced?
That means it has to download 200MB once they're installed it will take more space. Yes they replace files that are already installed.
Sometimes a newer version of an app may require something new, just remember that in ubuntu everything gets updated apps and the OS not just the OS like windows.
You can remove the downloaded packages once they are installed using
```
sudo apt-get autoremove
```
in a terminal
Applications > Accessories > Terminal
or
```
sudo aptitude autoclean
```
I kinda prefer the aptitude command because it will also remove packages which are no longer needed as well as those that are left over from upgrades.

---

### Post by emagine on 2010-03-06
> **2hot6ft2 said:**
> That means it has to download 200MB once they're installed it will take more space. Yes they replace files that are already installed.
Sometimes a newer version of an app may require something new, just remember that in ubuntu everything gets updated apps and the OS not just the OS like windows.
You can remove the downloaded packages once they are installed using
```
sudo apt-get autoremove
```
in a terminal
Applications > Accessories > Terminal
or
```
sudo aptitude autoclean
```
I kinda prefer the aptitude command because it will also remove packages which are no longer needed as well as those that are left over from upgrades.
Thanks for your help!

---

### Post by 2hot6ft2 on 2010-03-06
You're welcome and enjoy.

---

