---
title: "Uninstalling Wine"
date: 2008-12-22
forum: Wine
---

### Post by FalNix on 2008-12-22
Hi, I installed Wine to play Worms World party. I found some problems and errors after the instalation of the game, so I uninstalled it, and Wine.

Now I want to install Wine again to play GTA San Andreas, but it seems to be an error with the instalation of Wine, because I can't see Wine under the Applications menu and I can't configure it.

I uninstalled Wine again. Then I searched for "Wine" in "/" and 12 files were found, but I could not delete or modify these files because says "permisson denied".

It seems to be a configuration problem due to the previous instalation of Wine, but as I said, I can't delete the configuration files.

¿Is there a way to COMPLETE uninstall aplications?.
¿is there a way to login as ROOT, besides Terminal, so I can modify system files in a grafical interface?.

I use Ubuntu 8.04 "Hardy Henron" LTS

Thanks in advance.

---

### Post by DieB on 2008-12-22
start synaptic in system-administartion go to the wine package, and mark it for complete remove via right click and confirm (the green button on top). this will delete your configuration files.

to get root rights to nautilus (=filemanager) type in a terminal "sudo nautilus", now u got hte rights to change things that are own by root.

---

### Post by Cope57 on 2008-12-22
Next time install [Wormux]("http://packages.ubuntu.com/search?keywords=wormux"), it does not require Wine.

> ¿Is there a way to COMPLETE uninstall aplications?.
Yes, you can **sudo purge applicationname**

> ¿is there a way to login as ROOT, besides Terminal, so I can modify system files in a grafical interface?.
**gksu nautilus**
[I]gksu nautilus allows you to go through your directories and files as root, but Ubuntu was not intended to be run as root, for the fact that the user will most likely make matters worse.
Good luck.[/I]

---

### Post by FalNix on 2008-12-22
> start synaptic in system-administartion go to the wine package, and mark it for complete remove via right click and confirm (the green button on top). this will delete your configuration files.


I used Synaptic as you said, but I still find 12 files under "Wine".

file:///usr/share/app-install/desktop/wine.desktop
file:///usr/share/app-install/desktop/wineconfig.desktop
file:///usr/share/app-install/desktop/winefish.desktop
file:///usr/share/app-install/icons/_usr_share_pixmaps_winefish-icon.png
file:///usr/share/app-install/icons/wineconfig.png
file:///usr/share/python-support/guidance-backends/wineread.py
file:///usr/share/python-support/guidance-backends/winewrite.py
file:///var/cache/apt/archives/wine_1.0.0-1ubuntu4~hardy1_i386.deb
file:///var/lib/python-support/python2.5/wineread.py
file:///var/lib/python-support/python2.5/wineread.pyc
file:///var/lib/python-support/python2.5/winewrite.py
file:///var/lib/python-support/python2.5/winewrite.pyc

I don't know if these files generate some problem with the configuration, but I don't see Wine under the aplications menu if I reintall it, so I can't run Wine.

> to get root rights to nautilus (=filemanager) type in a terminal "sudo nautilus", now u got hte rights to change things that are own by root.

That worked thanks!

> Yes, you can sudo purge applicationname

Terminal says this:
sudo: purge: command not found

> gksu nautilus
That worked as well thanks!


Thanks, but as I said above, I still can't run Wine after reinstalling it. Please help me. Thans in advance.

---

