---
title: "Synaptic: Generate Package download script"
date: 2009-01-17
forum: The Cafe
---

### Post by BGFG on 2009-01-17
Can this feature be used or tweaked to mass package install a freshly installed system ? I had hoped that i could generate a script of all my installed packages, save it to may home partition, upgrade my filesystem  partition(to Jaunty), then just execute the script and re-install all my apps en-masse.

---

### Post by Grant A. on 2009-01-17
```

# Mass APT package download script
# Licensed under the BSD License
# The authors of this script, and the script's contributors disclaim all liability and warranties.
# Use at your own risk
# Requires: Internet, APT, dpkg, and Ubuntu

sudo aptitude install program1 program2 program3

```

Copy and paste into a text editor, replace program1, program2, etc. with the packages of your choice, save as new-packages.sh to your home directory, and make it executable by running this command:

```

chmod u+x new-packages.sh

```

Then put it on a CD or untouched partition by Jaunty when you install Jaunty, and you're good to go.

BTW, in Jaunty you can run it by typing:

```

./new-packages.sh

```

---

### Post by BGFG on 2009-01-18
Simple.Thanks a lot man. I'll try it :)

---

