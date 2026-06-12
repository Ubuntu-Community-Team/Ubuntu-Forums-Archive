---
title: "Noob XEN build question?"
date: 2013-07-08
forum: Virtualisation
---

### Post by KillerKelvUK on 2013-07-08
Hi, I'm building Xen 4.2.2 for my 12.04.2 server.  Have it working kinda and have debugged a ./configure parameter to override the make process looking to put some files into a none existent /usr/lib64 directory.

I use EFI boot at present and I've read around including the manual here [http://xenbits.xen.org/docs/4.2-testing/misc/efi.html](http://xenbits.xen.org/docs/4.2-testing/misc/efi.html) where it says to build a xen.efi file to use in replace of /boot/efi/EFI/ubuntu/grubx64.efi.  From my reading this is so that Xen can handle EFI systems, it being the first thing that needs to load.

I need to pass in a EFI_VENDOR parameter so that the build process knows where to put the resulting xen.efi file but I can't fathom where to specify this properly.  I've found this thread [https://aur.archlinux.org/packages/xen-git/?setlang=pl&comments=all](https://aur.archlinux.org/packages/xen-git/?setlang=pl&comments=all) and a few others that note about this parameter but nothing that describes the intended build steps needed.  

Do I just edit the makefile and define this variable at the top?  Would appreciate any pointers.

Thanks,

K

---

