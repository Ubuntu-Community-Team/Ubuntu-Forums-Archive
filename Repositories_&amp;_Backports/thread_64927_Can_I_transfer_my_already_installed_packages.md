---
title: "Can I transfer my already installed packages?"
date: 2005-09-12
forum: Repositories &amp; Backports
---

### Post by agm642 on 2005-09-12
I have installed Ubuntu on a computer to test it before I actually installed it in my own one. However, I have downloaded many updates and extra software on the other PC. Is there a way to transfer it to the other one and install it locally, in order to avoid having to download hundreds of megabytes again?

---

### Post by sethmahoney on 2005-09-12
Not that I know of.  But you can transfer all (or at least most of - some of them, like evolution, require a little more doing) your settings over to the new box by copying your /home folder.

---

### Post by jobezone on 2005-09-12
[QUOTE=agm642]I have installed Ubuntu on a computer to test it before I actually installed it in my own one. However, I have downloaded many updates and extra software on the other PC. Is there a way to transfer it to the other one and install it locally, in order to avoid having to download hundreds of megabytes again?[/QUOTE]
 They should be in **/var/cache/apt/archives**. As far as copying to another computer, compress them first to a rar file (or another format), because if you put them directly on a cd some of their names may be changed.

---

### Post by jobezone on 2005-09-12
You can then do ```
sudo dpkg -i *.deb
``` on the directory where you place all the deb's in your other computer.

Or place them in your other computer's **/var/cache/apt/archives** directory, change you repositories configuration to the same that you have in your first computer, do ```
sudo apt-get update
```, and instruct **apt-get** to install the upgrades and extra software like you did in your first computer: it will find that the packages it needs are on its cache, and will use them instead of downloading.

---

### Post by agm642 on 2005-09-12
All right,  I will give it a try. Thanks a lot! :cool:

---

