---
title: "[SOLVED] [UbuntuGnome] 16.04beta - no boot"
date: 2016-02-27
forum: Ubuntu Development Version
---

### Post by stupendos on 2016-02-27
Hallo, I was trying to test Ubuntu Gnome 16.04 beta. Starting the boot from the usb drive was impossible, but I'm not sure it's me or a bug. I have used unetbootin to prepare the usb stick with the beta iso, is that right?

---

### Post by kansasnoob on 2016-02-27
At what point in the process does booting the live USB stop? Or is it failing to boot any and all live USB's?

---

### Post by deadflowr on 2016-02-28
Moved to Ubuntu Development Version sub-forum

---

### Post by stupendos on 2016-02-28
Hello,
the process didn't start at all:

```
SYSLINUX 6.03 EDD 201508013 Copyright (C) 1994-2010 H. Peter Anvin et Al.
Boot Error
```

Sorry for having posted in the wrong place, this forum has hundreds of branches

---

### Post by stupendos on 2016-02-28
Startup disk creator worked well. I'm giving a try to Ubuntu Gnome 16.04 right now.
So the first bug is Unetbootin and not something in Ubuntu.

---

### Post by jimmy-frydkaer on 2016-02-29
Most likely there's nothing wrong with unetbootin. The process most likely didn't transfer all needed files to the stick.

fdisk the stick and create a FAT32 file system on it then try unetbootin again.

It takes som time for unetbootin to create the bootable stick so be patient.

---

