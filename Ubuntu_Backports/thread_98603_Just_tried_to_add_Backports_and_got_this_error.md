---
title: "Just tried to add Backports and got this error:"
date: 2005-12-03
forum: Ubuntu Backports
---

### Post by Daminator on 2005-12-03
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

When I open Synaptic Package Manager.
Tried adding the lines from the sticky post, and also tried just uncommenting the backport sections that were already in the file, but get the sime kind of erroy with each, so I've returned the file to how it was until I figure out what's going on.

---

### Post by invalid on 2005-12-03
```
sudo apt-get update
```

Cheers,
Cb

---

### Post by Mustard on 2005-12-03
You will need to close synaptic too, before you do the above command or it will give you a lock file error.

---

### Post by Daminator on 2005-12-03
Great, thanks for that!

---

### Post by mvandeg on 2005-12-04
[QUOTE=invalid]```
sudo apt-get update
```

Cheers,
Cb[/QUOTE]

Hitting Reload from within Synaptic a second time, also works and is even easier.

---

