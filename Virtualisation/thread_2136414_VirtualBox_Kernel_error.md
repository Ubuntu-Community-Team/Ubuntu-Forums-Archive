---
title: "VirtualBox Kernel error"
date: 2013-04-17
forum: Virtualisation
---

### Post by blanka32 on 2013-04-17
So im trying to run federa in VB but when I do I get this error right here:

```
 NS_ERROR_FAILURE (0x80004005)


```

i've been told to run this code by VB and some tech support forums. 

```
 [COLOR=#0000ff]/etc/init.d/vboxdrv setup[/COLOR]


```

however, when I do, I get:

```
bash: /etc/init.d/vboxdrv: No such file or directory
```

I've been told to install dkms as well, but the result of that ends up being:

```
 apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
The following packages were automatically installed and are no longer required:
  calligra-l10n-engb kdevelop-l10n kdevelop-php-docs-l10n kdevelop-php-l10n
  language-pack-kde-en
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
```

Help me out here, this has not happened with VB on any of my previous ubuntu machines. I'm a little clueless as to whats going on. I removed and reinstalled it from software center but the problem persists. 

Regards,

---

### Post by wildmanne39 on 2013-04-17
Hi, the command needs to be ran like this:
```
sudo /etc/init.d/vboxdrv setup
```
Thanks

---

### Post by wildmanne39 on 2013-04-17
*Thread moved to **Virtualisation**.*

---

### Post by Ennead on 2013-04-17
I am having the same problem with Virtualbox in 12.10. Not to be contrary, but I tried the sudo command, without success. Tried uninstalling and reinstalling 3 times, no luck. Also tried using "sudo ~/etc/..." just for fun. No dice.

---

### Post by wildmanne39 on 2013-04-17
After you run the command that it says to run this > bash: /etc/init.d/vboxdrv: No such file or directoryis a normal message but if you have gcc, buid essentials and your kernel headers installed it should then rebuild the modules needed.

---

