---
title: "Can't suspend PC"
date: 2015-03-03
forum: Ubuntu/Debian BASED
---

### Post by lorenzo16 on 2015-03-03
Hi, I recentely installed Elementary OS on my PC, but I'm having a problem with the suspension and hibernation, especially when I try to suspend the computer the screen remains on but all black and the computer stays on. I installed all AMD drivers by going to Settings -> Additional Drivers. My video card is an Asus HD Radeon 7950.

 Sorry for my bad english and thanks to all.

---

### Post by lorenzo16 on 2015-03-09
I resolved by adding ' Option "VBERestore" "true" ' to xorg conf file:

```

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        [COLOR=#ff0000]Option "VBERestore" "true"[/COLOR]
EndSection

```

and editing the grub_cmdline_linux in the grub config file (/etc/default/grub):

```
GRUB_CMDLINE_LINUX="acpi_sleep=old_ordering ec_intr=0"
```

---

