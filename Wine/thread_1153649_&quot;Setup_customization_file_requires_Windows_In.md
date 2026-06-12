---
title: "&quot;Setup customization file requires Windows Installer 3.1 or greater&quot;"
date: 2009-05-09
forum: Wine
---

### Post by gohanssjn on 2009-05-09
Installing Office 2007 in Ubuntu.  Any idea how to install Windows Installer 3.1 first?

---

### Post by sgosnell on 2009-05-09
Windows programs can't run in Linux, unless you're using wine, and even then I'm not sure MSOffice will run.  I have no idea where you would get the installer, unless it's included somewhere in the MSOffice disk.

---

### Post by gohanssjn on 2009-05-09
> **sgosnell said:**
> Windows programs can't run in Linux, unless you're using wine, and even then I'm not sure MSOffice will run.  I have no idea where you would get the installer, unless it's included somewhere in the MSOffice disk.

I am using Wine, thus being on this board.

I've heard of others running 2007, but not with this issue...

---

### Post by cogadh on 2009-05-09
There was a regression in Wine 1.1.17 that broke the Office 2007 installer and it has not yet been fixed as of 1.1.20. You can get around it by installing an older version of Wine, installing Office, then upgrading Wine (if already installed, it works fine in current versions).

---

### Post by gohanssjn on 2009-05-09
> **cogadh said:**
> There was a regression in Wine 1.1.17 that broke the Office 2007 installer and it has not yet been fixed as of 1.1.20. You can get around it by installing an older version of Wine, installing Office, then upgrading Wine (if already installed, it works fine in current versions).

Ah, cool.  I am a bit of a novice with all of this, how would I get an older version?

Hmmm, 1.1.16 does the same thing.  Maybe I'll just keep using OpenOffice for now.

---

### Post by cogadh on 2009-05-09
You can find archived packages here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Uninstall your current version of Wine, then install from one of the downloaded packages. If you have already added the WineHQ repository, you may be notified of a newer version being available, but it should still let you install the old one.

---

### Post by roberto.eiberle on 2009-05-09
just google for windowsinstaller, there are dozens of sites where you can download and it is less than 2 megas.

---

### Post by NightMKoder on 2009-05-09
Um, you shouldn't ever get the message. The regression appears by having the installer crash 3/4 of the way through installing. The most likely cause is that you have something else installed in your prefix that's giving you that.

Read [http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840)

EDIT:
> **roberto.eiberle said:**
> just google for windowsinstaller, there are dozens of sites where you can download and it is less than 2 megas.

You wouldn't want to do that for two reasons: 1. Winetricks can install the native msi and will override the necessary dlls for you. 2. wine isn't windows, and running native things on wine is usually not a good idea, since many parts of wine are unimplemented.

Wine comes with its own version of the microsoft installer. The fact that yours isn't working is a problem to be solved by fixing your wine installation, and not by installing the native version.

---

