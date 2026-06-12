---
title: "Init=bootarg no init found / semi fixed?"
date: 2018-01-14
forum: Ubuntu/Debian BASED
---

### Post by aresthegod6789 on 2018-01-14
Now first off, I am using kali linux but I discovered another post on this forum about the init=bootarg error, but re-installing the OS did not work for me. I tried over 5 times. 

HOW I FIXED:
When loading kali it gives an option to press 'e' over what you want to do to edit the boot commands or something like that, so I pressed E. Somewhere in there I saw my sdb1 drive. I changed it to sda1, and it booted perfectly fine and still saved my data.

FURTHER QUESTION:
I'm wondering if there is a way to have it automatically boot with sda1 because every time I restart, I have to reset it to sdb1.

---

### Post by howefield on 2018-01-14
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by aresthegod6789 on 2018-01-14
Sorry, This forum is quite confusing.

---

### Post by cruzer001 on 2018-01-14
You can change boot flags

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual#gparted-manage-partition-flags](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual#gparted-manage-partition-flags)

EFI may be different

---

