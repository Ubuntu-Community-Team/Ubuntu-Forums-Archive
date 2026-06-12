---
title: "new kernel image"
date: 2005-10-18
forum: Repositories &amp; Backports
---

### Post by Aurels on 2005-10-18
Hello.

The "updates notifier" gnome applet "says" me there is a new kernel image to install.

If I check and install it, will it my current (custom) kernel or will I have to edit my grub conf manually?

Thanks.

---

### Post by Emerzen on 2005-10-18
It will be added to GRUB automatically as your default kernel, though the other's will be there if you choose them.  One note, if you have a Windows partition in there, I would edit GRUB so that the lines referring to Windows are below the line about "debian automagic" in the conf file.  Otherwise, everytime you reconfigure GRUB (which will happen w/ new kernel) you'll have to readd the Windows parition.

---

### Post by Aurels on 2005-10-18
Ok thanks

---

