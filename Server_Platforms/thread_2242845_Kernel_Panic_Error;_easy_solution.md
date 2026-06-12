---
title: "Kernel Panic Error; easy solution?"
date: 2014-09-04
forum: Server Platforms
---

### Post by mike196 on 2014-09-04
Hello all,


I'm running Ubuntu Server 14.04.


Yesterday I ran sudo apt-get update && sudo apt-get upgrade.  It required a reboot after. Upon reboot, it was no longer booting.  I would come to the GRUB screen where I could choose Ubuntu, Advanced options for Ubuntu, and System setup.


If I choose Ubuntu, I go to a black screen.  There is no blinking cursor or anything.


If I choose Advanced Options for Ubuntu, I get a screen with Ubuntu withmany different versions, some with (recovery mode).


```

Ubuntu, with Linux 3.13.0-35-generic
Ubuntu, with Linux 2.13.0-35-generic (recovery mode)
.
.
.

```


If I choose one without recovery mode, I get the aforementioned black screen.


If I choose one with recovery mode, it acts as if it's loading, but then I get the following:


```

VFS: Cannot open root device "mapper/server--vg-root" or unknown-block(0,0): error-6
Please append a correct"root=" boot option; here are the avalable paritions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
CPU: 0 PID: 1 Comm: swapper/0 Not tainted 3.13.0-35-generic #62-Ubuntu
Hardware name: MSI MS-7721/A78m-E35 (MS-7721), BIOS V30.2 02/21/2014

```


There are more lines of random letters and numbers (I can attach a pic if necessary).


Is there an easy way for me to fix this?  Or do I just have to reinstall Ubuntu?


If I have to reinstall Ubuntu: I created logical volumes for my media using [this guide](http://linuxhomeserverguide.com/server-config/LVM.php).  Should I be able to reinstall without losing all of my media?

---

### Post by slickymaster on 2014-09-04
*Moved to the ***Server Platforms*** sub-forum.*

---

