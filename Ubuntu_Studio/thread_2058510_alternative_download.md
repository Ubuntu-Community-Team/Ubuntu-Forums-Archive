---
title: "alternative download?"
date: 2012-09-15
forum: Ubuntu Studio
---

### Post by And6ate9 on 2012-09-15
Is the somewhere I can get and alternative installation  of Ubuntu Studio? My computer seems to hate the graphic installer.

---

### Post by jerrrys on 2012-09-15
Not seeing the option

[http://cdimage.ubuntu.com/ubuntustudio/releases/12.04/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/12.04/release/)

---

### Post by tienlbhoc on 2012-09-15
> **And6ate9 said:**
> Is the somewhere I can get and alternative installation  of Ubuntu Studio? My computer seems to hate the graphic installer.

if your computer hate graphic, maybe, after install gui have problem

---

### Post by smartboyhw on 2012-09-16
1. There is no Ubuntu Studio alternate images in any means. :)

2. Why don't you go and download the minimal ISO in  [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) ? It is text-based, and after installation type ```
sudo tasksel
``` to install Ubuntu Studio:)

---

### Post by jejeman on 2012-09-16
What is the trouble with installer?

---

### Post by sgx on 2012-09-18
> **smartboyhw said:**
> 1. There is no Ubuntu Studio alternate images in any means. :)

2. Why don't you go and download the minimal ISO in  [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) ? It is text-based, and after installation type ```
sudo tasksel
``` to install Ubuntu Studio:)
Hi, does the installed 'base system' include a working synaptic
and/or dpkg?

the how-to page says

"After the base system is installed, log in, and type "sudo tasksel" to select the system to install."

Cheers

---

### Post by jejeman on 2012-09-19
No synaptic in "base system", because there is no DE (X) in it.
Dpkg is of course there, Apt too.

---

### Post by sgx on 2012-09-19
I may have a tinker, and try some E17, openbox, and
Windowmaker .debs with dpkg-i,
then prepare to descend into the abyss of dependency hell.
Worth a couple hours being led around by the nose
by error messages
:wink:

---

