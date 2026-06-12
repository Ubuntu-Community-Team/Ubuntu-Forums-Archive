---
title: "Error While installing Wine on Karmic Kowala"
date: 2009-11-07
forum: Wine
---

### Post by The-NightPhoenix on 2009-11-07
After installing Wine : apt-get install wine

the following error was shown 

> --2009-11-06 22:24:38-- [http://surfnet.dl.sourceforge.net/pr...l/andale32.exe](http://surfnet.dl.sourceforge.net/pr...l/andale32.exe)
Resolving surfnet.dl.sourceforge.net... 32.1.6.32
Connecting to surfnet.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Giving up.

sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

however wine worked and i tried some programs and no problems. 

but this error keeps showing after every time i try to install any thing with apt-get 

so please tell me hw can i clear this post innstalletion script or solve this problem

---

### Post by The-NightPhoenix on 2009-11-09
I Found the cause of the problem 

its the package "ttf-mscorefonts-installer" 
which downloads fonts for wine. appearntly there is a problem in the download of some kind so dpkg keeps trying to download them. 

i couldn't solve it , so i removed the package.

---

