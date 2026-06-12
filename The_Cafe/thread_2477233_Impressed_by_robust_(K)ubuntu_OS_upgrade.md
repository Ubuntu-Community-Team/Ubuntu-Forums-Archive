---
title: "Impressed by robust (K)ubuntu OS upgrade"
date: 2022-07-19
forum: The Cafe
---

### Post by blackbird34 on 2022-07-19
My laptop battery actually died during the upgrade from 21.10 to 22.04 LTS. I thought I had really borked everything when I booted and got to a screen full of low level errors. 

But then I tried again and booted from a different kernel in the GRUB menu and everything was fine! All that was needed was a little ```
sudo dpkg --configure -a
``` to clear everything up. I can use my laptop for work. However there are still issues and error messages due to the transition from grub to grub-efi...

---

