---
title: "No boot ubuntu 18.04 beta1 amd64 on UEFI 32bit devices."
date: 2018-03-11
forum: Ubuntu Development Version
---

### Post by kapper1224-w on 2018-03-11
Hello.

I tested Kubuntu 18.04 beta1 amd 64 on UEFI 64bit and 32bit on Atom.


&#12539;UEFI 64bit: No problem
&#12539;UEFI 32bit: No reconized bootloader and HDD partitons.
 &#8658; No bootia32.efi and diskspaces,
 I copied bootia32.efi on USB FAT32, boot UEFI and grub2,
 But No rootfs on grub2.

1.(hd0,msdos1)
 &#8658;EFI partations boot~.EFI only.
2.(hd0,apple1)
3.(hd0,apple2)
 &#8658;No rootfs partations.

In &#12316;17.10, can read rootfs on (hd0,msdos1)/~.
Please tell me to change boot sections from 17.10 to 18.04?

Thank you.

---

### Post by oldfred on 2018-03-11
I do not know 32 bit UEFI. But those that may be able to help could use more info.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by kapper1224-w on 2018-03-11
I know everything on the link.
I want to talk about &#12300;Change from Ubuntu 17.10 to 18.04&#12301;&#12289;
and how to boot UEFi32bit and bootloader.

If you don't know UEFI 32bit , Please see my slideshare.
[https://www.slideshare.net/kapper1224/presentations](https://www.slideshare.net/kapper1224/presentations)

Thank you.

---

### Post by cariboo on 2018-03-20
Moved to the correct sub-forum.

---

### Post by davegod75 on 2018-06-03
> **kapper1224-w said:**
> I know everything on the link.
I want to talk about &#12300;Change from Ubuntu 17.10 to 18.04&#12301;&#12289;
and how to boot UEFi32bit and bootloader.

If you don't know UEFI 32bit , Please see my slideshare.
[https://www.slideshare.net/kapper1224/presentations](https://www.slideshare.net/kapper1224/presentations)

Thank you.

I'm also wondering what changed because upgrading to 18.04 from 17.10 broke my macbook 2,1  (32bit efi)

---

### Post by wildmanne39 on 2018-06-03
18.04 is no longer in development. Thread closed!

---

