---
title: "Ryzen 6000 hardware noise coil cpu spykes"
date: 2022-03-14
forum: Ubuntu Development Version
---

### Post by florindobre on 2022-03-14
Hello community.

Have been running latest Ubuntu 22.04 daily-live on my Ryzen 6000 series and have the following issues:

1. hardware noise coil whine, CPU spykes, when i move mouse cursor everytime.  6980HX
2. wifi drivers were not installed, i think due to kernel? (kernel 5.13.0.35 does install new wifi drivers) - MediaTek Wi-Fi 6E MT7922 160Mhz 
3. cannot create/see files on desktop.

Has anyone encountered this problem before?

Thank you,
Florin.

---

### Post by Claus7 on 2022-03-15
Hello and welcome,

I'm not an expert on the issues you mention yet,

1) no experience, does this happen if you try another ubuntu flavour?
2) when you install your system ubuntu finds out which drivers are best for your system. How did you verify that the drivers were not installed? Check this out [https://askubuntu.com/questions/333424/how-can-i-check-the-information-of-currently-installed-wifi-drivers](https://askubuntu.com/questions/333424/how-can-i-check-the-information-of-currently-installed-wifi-drivers) in order to verify which driver you are using. Also, if additional drivers are available you can do so looking here: [https://itsfoss.com/install-additional-drivers-ubuntu/](https://itsfoss.com/install-additional-drivers-ubuntu/)
3) you should be able to see desktop files by using the extension gnome-shell-extension-desktop-icons-ng

Regards!

---

