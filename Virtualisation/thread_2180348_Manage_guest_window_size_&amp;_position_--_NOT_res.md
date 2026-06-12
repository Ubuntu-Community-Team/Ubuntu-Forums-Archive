---
title: "Manage guest window size &amp; position -- NOT resolution inside window.."
date: 2013-10-12
forum: Virtualisation
---

### Post by NuxNik on 2013-10-12
Hello,

I am new to VirtualBox and have successfully installed Version 4.2.18 on Lubunty 13,04

Currently I have a few problems that are unresolved.
This is one such 

How do I control the guest window size and location on the host machine desktop

My guest window ALWAYS opens full screen and I have to manually resize and position it once it is open
   (this is getting old and annoying real fast)
Since I ultimately want to run 3 different VBox guests,, and have a large enough display to have 3 windows open at the same time, this is an important issue

I have been unable to find any clear instructions in the VBox help or on the internet
(it all seems to be about resolution inside the window)

Your help is appreciated.

---

### Post by TheFu on 2013-10-15
Running full-screen is a setting in the vbox settings.  Press rctl+f to toggle it unless you changed the default "mouse/leyboard-release key". I can't check it now ... sorry.  I think it is in the "view" menu for each VM. there is definitely an option for the command used to start VMs that controls this.  I don't have a vbox system on linux anymore, but the man page will explain. I've seen it before.

Google found this: **VirtualBox --startvm vm_name --fullscreen**  So, there should be an option to start it windowed, perhaps create a tiny script and leave off the --fullscreen option?


In a window, the control over the size and placement is handled by the X/Windows window manager with queues from the app running inside - er ... at least it used to be before desktop environments.  In theory, that should still work, unless the DE gets in the way.  So, which WM are you using?  On straight LXDE, the settings are stored in ~/.config/openbox/lxde-rc.xml for example.

---

