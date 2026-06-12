---
title: "Mantic Installer changes language English to Russian during install"
date: 2023-09-28
forum: Ubuntu Development Version
---

### Post by andrewlatham on 2023-09-28
Ubuntu 23.04 to 23.10 BETA upgrade by running update-manager -d on 
ASUS X540LA Laptop
8GB RAM, 256GB SSD UEFI boot
Intel HD Graphics 5500
Dual Boot with WIN10 
English UK keyboard

Upgrade process launched fine in English and successfully downloaded packages and was probably over half way thru the install process when the installer text suddenly changed to Russian (google translate says its Russian),  Fortunately the terminal output was still in English, so I could still see that the install was progressing smoothly and subsequent dialog boxes/windows all were in Russian ( not English).
23.10 Install was successful and I appear to have a stable working system 
No Language or keyboard settings were changed on during install and all remain as English UK, so it appears to be an issue with the installer? Posting it here as it might prove useful to someone to check
I managed to capture a screenshot to show the issue in the mantic installer which is attached

A[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292802&stc=1[/IMG]

---

### Post by Rubi1200 on 2023-09-28
You should file a bug report on Launchpad, there may be others who have experienced this or similar.

By the way, if you are testing beta releases I would make sure you have _very good_ backups of all your data, whether Windows or Ubuntu.

---

### Post by Claus7 on 2023-09-28
Hello,

I came across this bug, yet just on the title bar during upgrade. As the OP mentions it didn't affect the installation. I suppose that it might be related to some font change that is taking place to the newest version of ubuntu.

Regards!

---

### Post by jbicha on 2023-09-28
That is not Russian.

I have experienced this bug every time I have upgraded from Ubuntu 23.04 to 23.10.

This issue has been reported as [https://launchpad.net/bugs/2034986](https://launchpad.net/bugs/2034986)

---

