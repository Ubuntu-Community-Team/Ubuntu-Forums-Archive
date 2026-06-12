---
title: "My Mini guide on installing open office 3 in Ubuntu"
date: 2008-10-15
forum: The Cafe
---

### Post by SunnyRabbiera on 2008-10-15
This guide mainly applys to recent versions of Ubuntu (Versions 7.10 through 8.10) as I am unsure if Open office 3 will work in older versions of Ubuntu.
Anyhow I will keep this simple:
Step 1: Download open office 3 for debian
2: Extract the zip file
3: In the debs folder move everything you have into the desktop integration folder by selecting as many of the debian insallers you can at a time but there are a whole crap load of them so this might take a while.
4: For normal Ubuntu users install the package nautilus-open-terminal, for Kubuntu and xubuntu users skip this
5: For normal Ubuntu users, restart your computer, for Kubuntu and xubuntu users skip this.
6: Remove as much of open office 2 as you can
7: go into that desktop integration directory and open up a terminal, now how to open your terminal in Ubuntu is by right clicking in the folder and selecting Open terminal.
Kubuntu and xubuntu users should have the open terminal command in the main menu of both Thunar and Dolphin/Konqueror
8: put in the command: sudo dpkg -i *.deb
9: after dpkg is done you may wish to try to install the package openoffice.org3.0-debian-menus_3.0-9354_all located in your desktop integration folder.
10: done

---

