---
title: "Problem with updating/installing the System76 driver."
date: 2019-11-02
forum: System76 Support
---

### Post by michaelmcole on 2019-11-02
Getting the below error when I try to update the System76 driver, any help is appreciated!
Kudu laptop, Ubuntu 19.10

[IMG]https://ibb.co/4FC0KdG[/IMG]

[[IMG]https://i.ibb.co/qs0XMpV/package-dependencies.jpg[/IMG]]("https://ibb.co/Nj1Q6Kb")
[multiple images upload]("https://imgbb.com/")

---

### Post by shochatd on 2019-11-02
Same problem here. Occurred on both my Ratel Pro desktop and Galago Pro laptop, both recently updated to 19.10.

---

### Post by shochatd on 2019-11-04
I found a solution to this problem, although I don't know why it works: Just use the command line:
```
sudo apt update
sudo apt upgrade
```
The first should show at least 4 upgradable packages. The second will complete the process of upgrading them (including bringing in the kernel mentioned in the error message). If you then go back and click on the Software Updater, it will say only that a restart is needed. I have no idea why the Software Updater was unable to handle it. I have mentioned all this to the System76 folks, but no response so far.

---

### Post by shochatd on 2019-11-04
Well wouldn't you know it. No sooner had I posted that than I received a response from System76 Support which included the following:

[I]This is the full list of commands we usually run to resolve package manager issues:
[/I]
```
sudo apt clean
sudo apt update -m
sudo dpkg --configure -a
sudo apt install -f
sudo apt full-upgrade
sudo apt autoremove --purge
```
I have to add that although I'm very happy with the systems sold by System76, part of the value is the amazing support like this I continue to receive, even after the systems themselves are well out of warranty.

---

### Post by michaelmcole on 2019-11-04
Awesome, this fixed my problem, thank you and thank System76 support!

---

