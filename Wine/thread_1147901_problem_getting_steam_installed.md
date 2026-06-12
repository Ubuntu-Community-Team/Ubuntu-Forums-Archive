---
title: "problem getting steam installed"
date: 2009-05-03
forum: Wine
---

### Post by jasonhill01 on 2009-05-03
Everytime i try to install steam via wine in terminal i get this error.

Jason@jason-desktop:~$ wine msiexec /i SteamInstall.msi
err:msi:copy_package_to_temp failed to copy package L"SteamInstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"SteamInstall.msi"


how do i fix this. i put the steaminstall.msi in the right directory. but still something is weird, and yes i'm new to linux in general.

---

### Post by jasonhill01 on 2009-05-03
i have even try the tutorial on 

[http://ubuntuforums.org/showthread.php?t=1145504&highlight=steam+install](http://ubuntuforums.org/showthread.php?t=1145504&highlight=steam+install)

but i get 

[email]jason@jason-desktop:~/.wine[/email]/drive_c/windows/system32$ wine steaminstall.exe
wine: could not load L"C:\\windows\\system32\\steaminstall.exe": Bad EXE format for 


when i try to install there.

---

### Post by jasonhill01 on 2009-05-03
ok got it to work with the tutorial from 

[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

---

