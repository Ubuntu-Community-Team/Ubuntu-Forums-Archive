---
title: "Gnome-calculator launcher icon not visible"
date: 2013-03-27
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-03-27
I just found out one funny issue.
I use Gnome-shell desktop environment with Gnome3 PPA and Gnome3 Staging PPA enabled.
The gnome-calculator was not visible in gnome-shell menu, there was no such an icon.
According to the file /usr/share/applications/gcalctool.desktop it should be found from "accessories - calculator".

Then, I noticed the name of this launcher icon file: it is gcalctool.desktop.
It should be gnome-calculator.desktop.

Well, I changed the file name into gnome-calculator and it became immediately visible in the menu.

Have you notived this same issue.

PS. Note that I have removed the transitional package gcalctool, leaving only gnome-calculator left.
      Also, I have found out that if Gnome3 and Gnome3 Staging PPA:s are purged the icon is visible in menu and there are no issues.

---

### Post by zika on 2013-03-27
> **Harry33 said:**
> I just found out one funny issue.
I use Gnome-shell desktop environment with Gnome3 PPA and Gnome3 Staging PPA enabled.
The gnome-calculator was not visible in gnome-shell menu, there was no such an icon.
According to the file /usr/share/applications/gcalctool.desktop it should be found from "accessories - calculator".

Then, I noticed the name of this launcher icon file: it is gcalctool.desktop.
It should be gnome-calculator.desktop.

Well, I changed the file name into gnome-calculator and it became immediately visible in the menu.

Have you notived this same issue.

PS. Note that I have removed the transitional package gcalctool, leaving only gnome-calculator left.
      Also, I have found out that if Gnome3 and Gnome3 Staging PPA:s are purged the icon is visible in menu and there are no issues.```
:~$ sudo apt-get purge -s gcalctool 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-calculator gstreamer1.0-alsa gstreamer1.0-plugins-base-apps
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gcalctool* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
Purg ubuntu-desktop [1.296]
Purg gcalctool [1:3.8.0-0ubuntu1]
```
```
:~$ cat /usr/share/applications/gcalctool.desktop [Desktop Entry]
Name=Calculator
Comment=Perform arithmetic, scientific or financial calculations
Keywords=calculation;arithmetic;scientific;financial;
Exec=gnome-calculator
Icon=accessories-calculator
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Utility;Calculator;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-calculator
X-GNOME-Bugzilla-Component=general
X-Ubuntu-Gettext-Domain=gnome-calculator
```
I still have to go to GS to see if launcher icon is visible...
Up-to-date with all GS PPAs...
Update&#8321;:  Icon is present and functional...

---

### Post by mc4man on 2013-03-27
> gnome-calculator (1:3.7.92-0ubuntu1) raring; urgency=low

  * New upstream release.
    - Rename gnome-calculator.desktop back to gcalctool.desktop
Your launcher icon (just an entry in gsettings) pointed to a non-existent file. Could as well replaced it (the launcher icon) or edited gsettings to reflect new name.

---

