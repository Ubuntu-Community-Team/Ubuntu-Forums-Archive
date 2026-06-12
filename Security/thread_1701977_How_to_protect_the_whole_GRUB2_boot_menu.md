---
title: "How to protect the whole GRUB2 boot menu?"
date: 2011-03-07
forum: Security
---

### Post by uqbar on 2011-03-07
Hi all.
I've already read and tested the various guides for pasword portecting the menu items.
What I need is a little bit different.
I need to protect the whole boot menu so normal users cannot select any entry at all and only let the default entry boot.
Any idea?

---

### Post by mikewhatever on 2011-03-07
Disable showing the menu altogether. Since the selection is made long before the user is identified, there is no way to tell if the user is normal or not.

---

### Post by themanfromdelmonte on 2011-03-09
The answer is grub customizer. Its fantastic.

Its a bit of pain to install. Instructions here  [http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by skraps on 2011-03-09
You want to modify these settings to -1 or 0 then use grub-mkconfig

These lines are located in /etc/grub.d/00_header
```

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi

```

---

### Post by skraps on 2011-03-09
Another solution is to use micheal gorvens luks patches. Then encrypt the boot partition so grub requires a password before being able to load the grub.cfg

---

