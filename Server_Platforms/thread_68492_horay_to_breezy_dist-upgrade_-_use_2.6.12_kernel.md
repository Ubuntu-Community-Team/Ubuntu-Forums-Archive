---
title: "horay to breezy dist-upgrade - use 2.6.12 kernel"
date: 2005-09-23
forum: Server Platforms
---

### Post by dabux on 2005-09-23
i have a headless server that was running horay. i dist-upgraded about a month ago to breezy.  However when i uname it says its still using the 2.6.10 kernel.

How i get the server to boot using the 2.6.12 kernel?

From the latest dist-upgrade error message below it appears there is something wrong with how grub is setup.

```
Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.12-9-386.
(Reading database ... 22866 files and directories currently installed.)
Unpacking linux-image-2.6.12-9-386 (from .../linux-image-2.6.12-9-386_2.6.12-9.14_i386.deb) ...
Preparing to replace linux-image-386 2.6.12.14 (using .../linux-image-386_2.6.12.15_i386.deb) ...
Unpacking replacement linux-image-386 ...
Selecting previously deselected package linux-restricted-modules-2.6.12-9-386.
Unpacking linux-restricted-modules-2.6.12-9-386 (from .../linux-restricted-modules-2.6.12-9-386_2.6.12.4-5_i386.deb) ...
Preparing to replace linux-restricted-modules-386 2.6.12.14 (using .../linux-restricted-modules-386_2.6.12.15_i386.deb) ...
Unpacking replacement linux-restricted-modules-386 ...
Setting up linux-image-2.6.12-9-386 (2.6.12-9.14) ...
Searching for GRUB installation directory ...
No GRUB directory found.
 To create a template run 'mkdir /boot/grub' first.
 To install grub, install it manually or try the 'grub-install' command.
 ### Warning, grub-install is used to change your MBR. ###

User hook script /sbin/update-grub failed at /var/lib/dpkg/info/linux-image-2.6.12-9-386.postinst line 967.
``` 

Is it as easy as doing that it says, "mkdir /boot/grub"?

If this is a headless server how do i choose the kernel to boot?

---

