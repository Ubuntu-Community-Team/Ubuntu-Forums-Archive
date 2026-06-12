---
title: "How to run virtualbox in hardy?"
date: 2008-05-11
forum: Virtualisation
---

### Post by lynxus on 2008-05-11
Hi guys,
I used synaptic to install virtualbox but it moaned about kernel files not being there.. So i uninstalled then went to their site and installed using the deb file.

Seemed to install ok, However i cant figure out how to actually run it.

Cant seem to find an icon for it nor does just typing the name in a terminal work.

Any ideas?

-G


---
lynxus@lynxus-desktop:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found
lynxus@lynxus-desktop:~$ virtualbox-ose
bash: virtualbox-ose: command not found
lynxus@lynxus-desktop:~$

---

### Post by lynxus on 2008-05-11
Ah ha, my bad.

Had problems with groups as well. so once i added myself to the vboxusers group i quickly logged out and in again and i had an icon :)

---

