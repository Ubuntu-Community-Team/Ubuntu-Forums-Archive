---
title: "Ubuntu 12.10 Issue"
date: 2012-08-31
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by TheMixtureMedia on 2012-08-31
Hi there I am not sure were to ask but I updated to Ubuntu 12.10 and my top and left bars is gone. I have my Cairo Dock to use but I would like to fix any one can help?

---

### Post by Toz on 2012-08-31
Moved to U+1 for better visibility.

---

### Post by Quackers on 2012-08-31
duplicate post

---

### Post by grahammechanical on 2012-09-01
What you are seeing is what I call the Ubuntu August 2012 Mini Extinction Event.

For several days we have been seeing existing Quantal installs broken by an update. No top panel. No Launcher. That is no Unity.

To make it worse the daily ISO image was also broken requiring the selection to nomodeset to get to the Installation Welcome screen. Then the resulting installation was broken just like on the existing install.

To make it even more worse, Ubuntu 2D has been removed. I have taken to installing something like XFCE or LXDE just so that I can have an alternative desktop to load into when the Unity desktop is broken. This way I can run updates which should in time fix the problem.

An alternative is to select Recovery Mode from the Grub menu. Then run FailsafeX mode. That puts the file system into read/write mode. Now, back out and run Root - Drop to root shell prompt and run

```
sudo apt-get update
```

followed by

```
sudo apt-get install
```

And hope that fixes things. But do not bet on it. Not yet.

If you go straight into Root - Drop to root shell prompt you will find that the file system is in read only mode. Cannot update like that. Need read/write mode.

Regards.

---

