---
title: "Unity launcher freezes"
date: 2013-02-08
forum: Ubuntu Development Version
---

### Post by skyggen on 2013-02-08
After upgrading to 13.04, the whole system will freeze if i try to move an icon on the unity launcher. If i hold down on any icon it just freezes. I am using Nvidia 310 tested drivers.

Anyone have any idea what would cause this?

SOLVED:

Problem solved by doing a complete removal of nvidia drivers using purge, then reinstalling them. ):P

---

### Post by dino99 on 2013-02-08
when you have upgraded, did you also:
- deactivate the third party repo ? (ppa, ...)
- be sure of your sources.list settings
- clean the system: clean/autoclean/autoremove/gtkorphan/bleachbit
-glance at your logs: .xsession-errors & /var/log/dmesg

):P

---

### Post by skyggen on 2013-02-08
> **dino99 said:**
> when you have upgraded, did you also:
- deactivate the third party repo ? (ppa, ...)
- be sure of your sources.list settings
- clean the system: clean/autoclean/autoremove/gtkorphan/bleachbit
-glance at your logs: .xsession-errors & /var/log/dmesg

):P

```

Script for cjkv started at run_im.
Script for default started at run_im.
Script for cjkv started at run_im.
Script for default started at run_im.
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
gnome-session[14189]: WARNING: Failed to start app: Unable to start application: Feil under kjøring av underprosess «unity-dodge-maximized-windows» (Ingen slik fil eller filkatalog)
gnome-session[14189]: WARNING: Failed to start app: Unable to start application: Feil under kjøring av underprosess «unity-dodge-windows» (Ingen slik fil eller filkatalog)
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
** Message: applet now removed from the notification area
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/dennemann/.compiz/session/1095a3bf8ee9468332136036970396336500000141890033"
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
** Message: using fallback from indicator to GtkStatusIcon
** Message: moving back from GtkStatusIcon to indicator
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returnerte feilen 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Ingen slik fil eller filkatalog
Please ask your system administrator to enable user sharing.


** (zeitgeist-datahub:14643): WARNING **: zeitgeist-datahub.vala:231: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

(eog:14700): EOG-CRITICAL **: eog_list_store_length: assertion `EOG_IS_LIST_STORE (store)' failed

```

This is the output from xsession-errors right after the crash.

---

### Post by sameerbo on 2013-03-15
Could you share how did you purge nvidia driver and how you installed again. Sorry I am new to ubuntu

Thanks

---

### Post by dino99 on 2013-03-15
Note that reopening a "SOLVED" thread, is not the way to go; you might have opened your own thread but not here (into upgrades subforum, as its a basic question)

To purge a package:
sudo apt-get purge packagename

then install:
sudo apt-get install packagename

note2: an easy way is to use the synaptic gui
sudo apt-get install synaptic

---

