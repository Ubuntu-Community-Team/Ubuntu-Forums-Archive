---
title: "Removing Boot Up OS Entries"
date: 2008-11-09
forum: Windows
---

### Post by veloci1992f on 2008-11-09
I used Wubi to try out Ubuntu and Kubuntu.  After that I got tired of seeing the dual-boot up so I decided to uninstall Ubuntu and Kubuntu.  When I go to restart, I see the dual-boot option menu...  Again.  *Boot OS:  Vista, Ubuntu, Kubuntu, Ubuntu (Tried to reinstall again and uninstall, no luck).

It's basically:  I uninstalled the Ubuntu OS since I installed with Wubi but it still presents me the dual-boot menu with the false OS entries where I can't even boot any other OS except Vista.

How can I fix this?  I'm using a 64 bit version of Vista if that helps.  

Yes, I've also took a look at the FixMBR technique but it didn't work for me.  :/  Last resort is to reformat...

---

### Post by smoker on 2008-11-09
you may have to edit the 'boot.ini' file, which is a hidden file in the root of the C:\ drive (if windows is installed in C). make a back up first, then edit the file and remove any lines for booting any os but windows.

ignore this, see below please!

---

### Post by fiddledd on 2008-11-09
Assuming that Wubi just added items to Vista's boot menu you can edit it with [this](http://www.vistabootpro.org/)

Remember to use the backup option before you make any changes.

---

### Post by fiddledd on 2008-11-09
> **smoker said:**
> you may have to edit the 'boot.ini' file, which is a hidden file in the root of the C:\ drive (if windows is installed in C). make a back up first, then edit the file and remove any lines for booting any os but windows.

Vista doesn't use a boot.ini file, it uses a new boot loader.

---

### Post by smoker on 2008-11-09
> **fiddledd said:**
> Vista doesn't use a boot.ini file, it uses a new boot loader.

thanks for that info, will have to have a closer look and educate myself next time i get the chance :)

---

### Post by fiddledd on 2008-11-09
> **smoker said:**
> thanks for that info, will have to have a closer look and educate myself next time i get the chance :)

You are welcome :)

BTW, [VistaBootPro](http://www.vistabootpro.org/) or [EasyBCD](http://neosmart.net/dl.php?id=1) are useful freeware to edit the Vista Boot otions.

---

