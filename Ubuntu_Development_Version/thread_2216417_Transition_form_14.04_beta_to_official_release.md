---
title: "Transition form 14.04 beta to official release"
date: 2014-04-11
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2014-04-11
I've been testing Trusty for over a week on both my old laptop (it's only OS) and my desktop (Win 7 on SSD, Ubuntu 13.04, and 14.04 both on HDD). 
I'm quite happy with the results - no problems with drivers as everything worked '**out of the box'.**:)

Since both Trusty installations were of a fresh partition I'm wondering once Trusty is officially released what the next logical step might be? 

My preference is not to do another fresh install since these 2 installs are now configured as I like.I'm relatively familiar with apt-get commands. [INDENT]1-What should I do with software sources list?
2-Should I do apt-get dist-upgrade after final is released?
3-Anything I missed?
[/INDENT]

Thanks in advance!

---

### Post by sammiev on 2014-04-11
Just do a regular update at least once a week.

---

### Post by pfeiffep on 2014-04-11
Thanks for the quick reply @sammiev - so a regular update will adjust the software sources??

---

### Post by sammiev on 2014-04-11
No changes required. In about a week from now you will be running 14.04 LTS.

---

### Post by cariboo on 2014-04-11
I'd suggest doing regular updates daily, as the final versions of the trusty packages are coming almost hourly.

---

### Post by 3rdalbum on 2014-04-12
> **pfeiffep said:**
> Thanks for the quick reply @sammiev - so a regular update will adjust the software sources??

No, the software sources stay the same throughout. Or, to put it another way, the software sources changed a couple of days after 13.10 was released, and anyone who installs 14.04 after release will be using exactly the same software sources as you are currently using.

---

### Post by pfeiffep on 2014-04-12
Thanks all for the responses.

Today's experiences are somewhat perplexing to me.
1- apt-get update and upgrade went smoothly nothing was reported to be held back - I rebooted 
2- software updated installed a new kernel - this occurred immediately after #1
Since apt-get upgrade didn't install the new kernel what indications should I see notifying me to perform distupgrade?

```
pfeiffep@Pete-dell:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
pfeiffep@Pete-dell:~$ 
pfeiffep@Pete-dell:~$ uname -a
Linux Pete-dell 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

```

---

### Post by bapoumba on 2014-04-12
If you have linux-generic installed, just run:
```
sudo apt-get upgrade linux-generic
```
It will install the kernel and its dependencies.

---

