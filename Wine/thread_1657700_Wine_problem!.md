---
title: "Wine problem!"
date: 2011-01-01
forum: Wine
---

### Post by asusshqip on 2011-01-01
Hello,
Im using Ubuntu 10.10 64bit and i have isntalled wine from Ubuntu software center but i have some real problem with wine. Some app can install and open but some of them (autocad 2008 and many others)cant open. When i try to launch i duble click but nth showes up. And some .exe cant be installed. And when i try to remove those app that cant open i cant! Please help me

---

### Post by cogadh on 2011-01-01
Wine doesn't work for everything, check the Application Database to see what will and will not work with Wine:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by asusshqip on 2011-01-01
Is there any chance to install autocad on uBuntu 10.10 because i really like this OS and i dont wanna change it.

And how to remove apps from wine?

---

### Post by cogadh on 2011-01-01
Judging by the info on AppDB, it depends on which version you are trying to install, some work better than others. If the version you are trying to run is one of the recent versions, you're pretty much out of luck with Wine. Your only other possible option would be to use a virtual machine (like VMware or VirtualBox) with Windows installed. Alternatively, you could try to find a Linux native alternative to AutoCAD (not sure if one exists).

Uninstalling software from Wine is just like uninstalling software from Windows, just use the unistall shortcut created when you installed the application or if that is not an option (or it doesn't work), open a terminal and run "wine uninstaller" to launch Wine's version of the Add/Remove Programs app. As a last resort, you can always simply delete your .wine directory from your home directory to erase everything installed with Wine and start fresh.

---

### Post by asusshqip on 2011-01-01
I have already installed win 7 another partiton but i would like to run autocad on ubuntu. A have tried to instAll VMware on wine but does not work. What u preferedme to do? Should i use another version of wine or ubuntu (10.4) Im beginner user for ubuntu but i feel good on it.

P.s its better to use ubuntu linux or macOS for secondary OS on my pc?

---

### Post by cogadh on 2011-01-01
You don't install VMware in Wine, you install it in Ubuntu (did you try to install the Windows version of VMware instead of the Linux version?). After it is installed, you then install Windows in VMware, then install AutoCad in the virtual Windows installation within VMware.

Another version of Wine or Ubuntu won't make any difference. If the software doesn't work in Wine, it doesn't work, period... at least until Wine improves more.

It is not better or worse to have any particular secondary OS, its just a matter of preference, however, I don't think you can install MacOS on any machine that is not already a Mac (that may have changed since Macs switched to Intel-based hardware).

---

