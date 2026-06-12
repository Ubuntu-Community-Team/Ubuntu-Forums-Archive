---
title: "GRUB boot settings"
date: 2013-04-12
forum: Ubuntu Development Version
---

### Post by bird1500 on 2013-04-12
Hi,
When booting the Raring live iso I specified in grub2 additional boot settings: "noapic nolapic edd=on nodmraid" otherwise the installer would not install.
These additional settings have also been automatically applied to the installed OS's grub bootloader, but I wanna get rid of them since with these additional settings the OS only sees one core of my CPU.
The installed OS always adds back these settings after each grub-update to /boot/grub/grub.cfg (so I have to delete them from this file after each grub update), where are these "custom default" settings stored to delete them forever?

---

### Post by JMB74 on 2013-04-12
/etc/default/grub

is likely.

---

### Post by bird1500 on 2013-04-12
Thanks a bunch, indeed, there's a line (I'll comment out):
GRUB_CMDLINE_LINUX="noapic nolapic edd=on nodmraid"

Problem solved.

Apparently one can't mark the thread as solved anymore.

---

### Post by JMB74 on 2013-04-12
For ref:[https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

---

### Post by pfeiffep on 2013-04-12
> [COLOR=#000000]Apparently one can't mark the thread as solved anymore.[/COLOR]

Edit your original post ... there you should find a selection to apply "SOLVED"

---

### Post by philinux on 2013-04-12
> **pfeiffep said:**
> Edit your original post ... there you should find a selection to apply "SOLVED"

Then click go advanced and change the thread prefix. This is the work around for now.

---

### Post by bird1500 on 2013-04-12
Thanks, done, hopefully soon a new forum update will fix this inconvenience.

---

### Post by cariboo on 2013-04-12
> **bird1500 said:**
> Thanks, done, hopefully soon a new forum update will fix this inconvenience.

Some of the add-ons we requested, have already been approved, the Mark thread Solved being one of them, I'm not sure yet when we'll see them enabled though.

---

