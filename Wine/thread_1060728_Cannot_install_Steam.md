---
title: "Cannot install Steam"
date: 2009-02-05
forum: Wine
---

### Post by Kow on 2009-02-05
I'm using the exact default options in the SteamInstall.msi installer and It will not install when I press okay at the location where to install it. It says "C:\Program Files" and when I press okay it says "Folder path contains unknown files" The installer is bugged and wont even let me change the install location. I've tried using Wine in the intrepid repos and also winehq's latest version (1.1.14) and there is absolutely no difference. This is using a fresh wine install, btw.

---

### Post by Kow on 2009-02-05
Ah I figured it out.. stupid hidden files. For anyone else with the problem: Make sure Program Files is empty before you install Steam. If you already have stuff installed there then simply move it to a backup folder (C:\backup) and then move it back after you install Steam. I had a test file sitting in there to make sure file permissions were correct.

---

