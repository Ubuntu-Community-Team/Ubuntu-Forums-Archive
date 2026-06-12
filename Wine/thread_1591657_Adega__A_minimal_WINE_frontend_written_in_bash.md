---
title: "Adega:  A minimal WINE frontend written in bash"
date: 2010-10-09
forum: Wine
---

### Post by onemyndseye on 2010-10-09
I started this project for my own use but it has grown into something that I feel is pretty helpful.   From the script header:

> 
Derrived from the Portuguese word for wine estate or wine cellar, Adega is a simple program to help with the task of managing and configuring your wine prefixes doing so completely independent of your systems default wine install and prefix.


This script helps you manage your prefixes in a "less is more" sort of fashion.  Features include winetricks/wisotool management, execution of built in tools such as regedit and winecfg, Menu driven launcher dialog, support for both zenity (Gnome and other GTK based desktops) and kdialog (KDE desktops), Creation of prefixes in a wizard driven manner, Independent precompiled WINE version (thanks to the PlayOnLinux repo), Launcher creation/Desktop Menu integration, Logging, Desktop resolution fixups (dont you hate it when a wine app doesnt reset your desktop size?), prefix backup/compress, and more to come like the ability to build self extracting installers from preconfigured prefixes. (like google picasa)


What this script does NOT do:
Any sort of magic voodoo that is guaranteed to make all your windows apps run. 

Ive tried to stay away from tweaking and fixups for wine apps for the most part as there are plenty of WINE frontends, such as the wonderful PlayOnLinux, that do this for you.   I wanted/Needed something that would allow me to create a prefix, configure/tweak it the way *I* wanted using the readily available tools/scripts (namely winetricks) and install apps.   If you are looking for something fancier then this is not the app for you :)

What not use PlayOnLinux/Cedga? you might ask...   Its an excellent app for sure but sometimes, mostly where there is no supported install script or when updating a app/game its just easier to do things yourself.   This got me writing and putting together bits of code and what ultimately resulted in what I feel is a nice little frontend.  I use it everyday and continue to add features and improvements.  More info and usage info is available at the github project page.

Packages that you will need:
curl, icoutils, imagemagick, wget, zenity|kdialog

Maybe also:
ia32-libs (for 64bit) lib32asound2 libc6-i386 lib32nss-mdns binfmt-support
winbind ttf-symbol-replacement, ttf-mscorefonts-installer


Known bugs:
Menu navigation Back functions need to be improved
Overall error checking could be better
Need better error checking in the update functions
Not much documentation of features/usage

Github Home:
[http://github.com/onemyndseye/adega](http://github.com/onemyndseye/adega)


Direct download:
[http://github.com/onemyndseye/adega/raw/master/adega](http://github.com/onemyndseye/adega/raw/master/adega)


It has certainly developed into something that fills my WINE needs and maybe it will yours as well :)

Take care,
-onemyndseye

---

