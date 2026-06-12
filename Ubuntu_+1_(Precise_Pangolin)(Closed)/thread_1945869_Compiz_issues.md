---
title: "Compiz issues"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by geomcd1949 on 2012-03-23
Somebody fiddled with my compiz setings. Now all I get is a screen with the desktop background and the mouse pointer. No keyboard key or combination seems to work to make anything happen. [I can shut down with Ctrl-Alt-Delete].

Can anything be done to save this machine, or is all lost?

Ubuntu 12.04 beta

Thanks.

~George

---

### Post by uRock on 2012-03-23
Moved to *Ubuntu +1 (Precise Pangolin)*

---

### Post by t1497f35 on 2012-03-23
A new version of compiz and unity (5.8) have just been released, if you can update your system do it now and see if anything works better.

---

### Post by geomcd1949 on 2012-03-23
I have nothing to click on, nor do the keyboard keys do anything.

---

### Post by xombie on 2012-03-23
The latest update just broke my unity 3d. After the update the launcher would strobe when I moused over. On reboot I can only get into unity 2d. I think it may be the compiz update. Lots of error messages about compiz when I do a unity reset.

---

### Post by cariboo on 2012-03-23
> **geomcd1949 said:**
> I have nothing to click on, nor do the keyboard keys do anything.

To shut-down and restart your system without using the power button, press Ctrl-Alt-F1 to get to a console, then press Ctrl-Alt-Del to reboot. Once at the login screen choose Unity-2D for your session, once at the desktop, open compizconfig-settings-manager (ccsm) and make sure the Unity plugin is enabled, then log out, and log into Unity-3D.

---

### Post by mc4man on 2012-03-23
Just to mention -
If you're on Desktop with nothing on it & no apparent way to get a terminal or run dialog, if the right click works then - 

 just create a folder, open it, browse to /usr/share/applications & open Compizconfig Settings Manager from there.

---

### Post by Mark Rooney on 2012-03-23
> **cariboo907 said:**
> To shut-down and restart your system without using the power button, press Ctrl-Alt-F1 to get to a console, then press Ctrl-Alt-Del to reboot. Once at the login screen choose Unity-2D for your session, once at the desktop, open compizconfig-settings-manager (ccsm) and make sure the Unity plugin is enabled, then log out, and log into Unity-3D.

Same issue for me after updating today, when I log into a Unity 2D desktop run CCSM the Unity Plugin is enabled. 

Logging into the guest session I get a normal Unity 3D desktop but if I use my account only the wallpaper is displayed.... I think compiz just broke something again ](*,)

---

### Post by xombie on 2012-03-23
I tried a guest session and it was the same fail.

---

### Post by alphacrucis2 on 2012-03-23
> **geomcd1949 said:**
> I have nothing to click on, nor do the keyboard keys do anything.

Does ctrl alt f1 work?

---

### Post by Procrustes on 2012-03-24
After using Update Manager and installing the recommended Unity 5.8 with Compiz 0.9.7.2-0ubuntu1, I also am left only having the desktop background with no top menu bar, or dash or right-click menu. I pressed Ctrl-Alt-F1 and logged back in to Unity 2D. 

I then typed unity -- reset and ended up with the following error messages:

> unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1400002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1200002

ERROR 2012-03-23 23:39:13 unity.bghash BGHash.cpp:538 could not open file (/home/nick/.cache/unity/bgcachefile): Failed to open file '/home/nick/.cache/unity/bgcachefile': No such file or directory

Screen geometry changed:
   0x0x1280x720

Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00090!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-03-23 23:39:16 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/firefox.desktop' is using a depracted format for it's actions that will be dropped soon.
WARN  2012-03-23 23:39:16 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a depracted format for it's actions that will be dropped soon.
WARN  2012-03-23 23:39:16 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a depracted format for it's actions that will be dropped soon.
WARN  2012-03-23 23:39:16 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a depracted format for it's actions that will be dropped soon.
WARN  2012-03-23 23:39:16 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/chromium-browser.desktop' is using a depracted format for it's actions that will be dropped soon.
WARN  2012-03-23 23:39:16 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/gnome-terminal.desktop' is using a depracted format for it's actions that will be dropped soon.
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing cube options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Setting Update "main_menu_key"
Setting Update "run_key"
Starting gtk-window-decorator
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct


Anyone have a solution?

---

### Post by dino99 on 2012-03-24
ubuntu-bug unity

---

### Post by Procrustes on 2012-03-24
thanks for the command.

filed the report: here is the link replete with spelling mistake

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963942](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963942)

---

### Post by Procrustes on 2012-03-24
I am doing a lot of replying in this thread but I hope it is helpful. I restored Unity 3D and have the launcher and the top menu panel back. The key part of the error message was "unity-panel-service: no process found".

I basically did the same as the first answer here:

[http://askubuntu.com/questions/69046/unity-is-not-working-properly-because-unity-panel-service-was-not-found](http://askubuntu.com/questions/69046/unity-is-not-working-properly-because-unity-panel-service-was-not-found)

restoring unity-panel-services worked.

I have still no clue how or why this module stopped.

---

### Post by The_Autonomist on 2012-04-18
how did you restore unity-panel services????

---

