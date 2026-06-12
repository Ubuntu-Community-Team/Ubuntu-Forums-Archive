---
title: "karmic install of sun virtual box (not OSE)"
date: 2009-10-28
forum: Virtualisation
---

### Post by mr19 on 2009-10-28
Hi all.  Initially installed virtualbox from repository which gave me the OSE edition without USB support.  Found the CSE version from sun for Karmic & tried to install that (after removing the OSE edition) and I continually get a "Error: Breaks exisiting package 'virtualbox-ose' conflict: virtualbox-3.0 ( )' message from Package Installer.  

Any thoughts? 

TIA
Marc

---

### Post by drs305 on 2009-10-28
You might try removing ose again with this to make sure all the configuration files are also removed.
```

sudo apt-get purge virtualbox-ose

```

---

### Post by mr19 on 2009-10-28
Thank you very much.  That plus below did the trick (still had virtualbox-ose-source).

```

sudo apt-get autoremove virtualbox-ose

```

---

