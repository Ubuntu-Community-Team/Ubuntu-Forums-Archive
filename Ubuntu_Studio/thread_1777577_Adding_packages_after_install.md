---
title: "Adding packages after install"
date: 2011-06-07
forum: Ubuntu Studio
---

### Post by RunForIt222 on 2011-06-07
I installed Ubuntu Studio to a virtual machine early, and when it came time to pick the packages I wanted, I accidentily didn't pick any. How can I got back after install to add in packages (such as the graphics package, audio drivers package, etc)?

Thanks for any help.
~Jake

---

### Post by jejeman on 2011-06-08
If you know which applications you want you can install them one by one. Or if you want the meta packages, like shown in instaler, then install the:
ubuntustudio-audio-plugins
ubuntustudio-video
ubuntustudio-audio
ubuntustudio-font-meta

This is the list for 10.04. In 11.04 packages are little diffrent, but they are easy to find because they all start with "ubuntustudio-".

---

### Post by sgx on 2011-06-08
> **RunForIt222 said:**
> I installed Ubuntu Studio to a virtual machine early, and when it came time to pick the packages I wanted, I accidentily didn't pick any. How can I got back after install to add in packages (such as the graphics package, audio drivers package, etc)?

Thanks for any help.
~Jake
use the package manager

sudo synaptic

then find the meta-packages mentioned above, or individual favorites.

Sometimes a single app (name-of-app.deb )won't be in the repository, and can be downloaded elsewhere, and installed by

sudo dpkg -i name-of-app.deb

If it depends on yet another app, dpkg will tell you
which one(s) to get. Generally, system apps should not be handled this way, but a simple audio app like timemachine, will usually just work.

Cheers

---

### Post by jejeman on 2011-06-08
> use the package manager

sudo synaptic
Never use sudo with graphical (GUI) programs, just for CLI programs. For GUI programs always use gksudo
```
gksudo synaptic
```

---

### Post by RunForIt222 on 2011-06-08
Awesome, thanks.

@jejeman,

Whats the difference between sudo and gksudo?

**Nevermind I googled it :P**

---

