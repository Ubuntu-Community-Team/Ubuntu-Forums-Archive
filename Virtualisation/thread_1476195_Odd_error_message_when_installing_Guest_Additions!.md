---
title: "Odd error message when installing Guest Additions!"
date: 2010-05-07
forum: Virtualisation
---

### Post by GARoss on 2010-05-07
Mac Host OS X 10.6.3
Ubuntu 10.04 64bit LTS as guest
VirtualBox v 3.1.6 r59351

Never seen this one before. I need to install *build-essential* before installing Guest Additions for amd64 Linux. In doing so I get; 

```
Media change: please insert the disc labeled 'Ubuntu 10.04 LTS _Luciid Lynx_ - Release amd64 (20100429)' in the drive '/cdrom/' and press enter
```

What disc? I did select the Ubuntu 10.04 install iso in VirtualBox/Devices but still errors. What gives?

---

### Post by doas777 on 2010-05-07
are you configured for apt-on-cd? if so you may have to add an additional optical drive to your VM, so you have one for ubu, and one for the additions.iso.

---

### Post by GARoss on 2010-05-07
This is very weird. I typed *mount /cdrom/* in the terminal & it gave an error but proceeded to install build-essential without the disc. Very strange.

---

### Post by doas777 on 2010-05-07
> **GARoss said:**
> This is very weird. I typed *mount /cdrom/* in the terminal & it gave an error but proceeded to install build-essential without the disc. Very strange.
well it probably installed them from the internet repos, if you have networking configured.

---

