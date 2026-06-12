---
title: "Triple Boot, XP, 7, Ubuntu, redundancy"
date: 2014-10-28
forum: Windows
---

### Post by Andrew_Basti on 2014-10-28
Ideally I would love to just use Grub, Either pick Ubuntu, Windows 7, or Windows XP from Grub, and then it just boots the selected OS.

Instead what I have is the first step being Grub, then if I select either version of Windows it then loads the windows boot manager. I've installed EasyBCD under windows xp and windows 7 to try and tweak some settings, and the best I've been able to accomplish is when I choose to boot to XP from Grub, the only option is XP and I told it to skip the boot screen so when I select windows xp it boots straight to XP without showing the extra boot manager screen. The issue now is on the windows 7 side. When I choose to boot to windows 7 from Grub, it shows the boot manager, with XP the default selection, I have to arrow up to pick windows 7 and then it will boot to 7. When I view EasyBCD on the windows 7 side though it shows the only entry for the boot manager to be XP, so I'm not sure what I'm doing here. I'd love to just get rid of the Windows Boot Manager altogether and have Grub be the first and last step to booting.

---

### Post by CantankRus on 2014-10-29
Once you choose to boot to windows from grub, the windows boot.ini takes over which displays your Windows installs.
I don't have Windows7 but imagine it's the same.(I have 2 XP installs)
 
Log into windows and run msconfig and go to the boot.ini tab.
You'll see something like
```
[boot loader]
redirect=usebiossettings
redirectbaudrate=
timeout=3
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
**[operating systems]**
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="SOF2" /noexecute=optin /fastdetect /usepmtimer
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP" /noexecute=optin /fastdetect /usepmtimer
```

You can highlight an install under "**[operating systems]**" and move it to the top 
and hit the default button to set it as the default OS to boot into.
Here I also set a 3 sec timeout so it's not sitting there for 12 secs or until you hit enter
but allows enough time to select the other OS if wanted.

You can also use **grub-reboot** from ubuntu to set the default boot entry for GRUB, for the next boot only.
ie If I am in Ubuntu and want to boot to my Windows boot.ini, I set my windows entry to boot using grub-reboot,
go make a coffee and when I come back I'm booted into my default Windows install.

This script will run grub-reboot.
Save as **reboot-to-windows.sh** and make executable.
```
#!/bin/bash

## grub-reboot sets the default boot entry for GRUB, for the next boot only
## To enable grub-reboot to be edited by any user run
## sudo chmod +s /usr/bin/grub-editenv

## To find the grub menu entry you want run
## grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d'

# This will grab a windows grub menu item
grubentry=$(grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d' | grep -i windows)

grub-reboot "$grubentry"  # preface with gksudo if you didn't run the chmod command  
gnome-session-quit --reboot
```

Run this command so you can run the script without admin privileges...
```
sudo chmod +s /usr/bin/grub-editenv
```

When you run this script from Ubuntu it will prompt to restart, where upon reboot your Windows grub menu will be highlighted.
Upon next reboot, the grub menu will return to the Ubuntu menu item.

---

### Post by maxmuoto on 2014-12-04
Why would you need windows xp and 7 doesn't windows 7 have a windows xp mode?

---

