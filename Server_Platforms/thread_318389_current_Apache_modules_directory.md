---
title: "current Apache modules directory"
date: 2006-12-13
forum: Server Platforms
---

### Post by computec on 2006-12-13
Hello all,  
     I'm looking to find out where the current Apache modules directory should be located.
I'm running the fp_install.sh and it ask for a lot of file location that I'm unfamiliar with.
Does anyone know where I can find the default location, and does it matter where it is?

I am struggling to win this battle with Frontpage.... (you know the old M$ thing)...  

Thanks,

Alan
(Real Linux Newbie)  :-D

---

### Post by computec on 2006-12-13
I have looked all through the file system and I'm still now even sure what I'm looking for, but I can't find a folder that looks like it might be the Apache modules directory.
Can anyone point me in the right direction?

Thanks,

Alan

---

### Post by MJN on 2006-12-14
**/etc/apache2/mods-available/** and these, in turn, are enabled using **a2enmod <module name>** (disabled with **a2dismod <module name>**) which effectively[1] puts symlinks in /etc/apache2/mods-enabled/).
 
Mathew
 
[1] At the time of writing. Don't be tempted to create the symlinks yourself as this habit could become a cropper if the a2enmod/a2dismod scripts evolve in time in order to do more than simply create/remove symlinks.

---

### Post by computec on 2006-12-14
Since I have uninstalled Apache2 and installed Apache 1.3.34 does it still use the same dir for the modules or does it have a different one?

---

