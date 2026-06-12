---
title: "Dual boot Ubuntu 14.04/Win7 references /efi not /EFI"
date: 2015-03-06
forum: Windows
---

### Post by chris_smith3 on 2015-03-06
I think this should be in the grub section but don't know how to move it. Sorry ...

A system which is set up for dual boot of Ubuntu 14.04 & Win7 fails to boot Win7 because the menu item in grub.cfg refers to /efi whereas the actual Win7 directory is /EFI (set up by Win7 installer).

Manually editing grub.cfg gets round this problem but any kernel updates or running update-grub cancels this edit and we're back to square 1.

It appears /etc/grub.d/30_os-prober separates the EFIPATH and the DEVICE but I can't see why it changes the case of the path.

Any help would be much appreciated.

---

