---
title: "Desktop Resolution Horrors with X"
date: 2008-08-25
forum: Virtualisation
---

### Post by grmbl on 2008-08-25
Hi,

I'm completely new to Linux. Looking to replace my Windows installations which quite often fail or become very slow after some time, I recently installed Ubuntu 8.04 LTS and must say it's looking promising. I'm not ready to replace my real hardware with Linux yet though, so I'm aiming to look at / examine all Ubuntu functionalities using MS Virtual PC 2007 for the time being.

Install went pretty smooth after following some advice on installation from other forums (such as including "vga=791 noreplace-paravirt" in the boot command). 

However, the desktop will only work at 800x600 or 1920x1280 which either isn't enough to comfortably show all of the Desktop area (for instance, I can't configure the email client because the configuration window is larger than the screen, thus I can't click the right buttons), or is too much so I need to scroll back and forth constantly. This bugs me, and as such I've tried editing the /etc/X11/xorg.conf file to tweak desktop resolutions.

Ubuntu seems to ignore all my edits in xorg.conf. for instance, I had 'Modes "800x600"' in xorg.conf, but the Desktop then shows as 1920x1280, and lists all kinds of options when I go to System->Preferences->Screen Resolution. Problem is, whenever I make ANY changes in that screen and apply, the desktop becomes completely garbled, making it impossible to decypher anything! It requires a complete reinstall (or restore of backed up VM) to roll back. Very frustrating.

All I'm aiming for is a desktop screen resolution of 1280x800 or something close to that using MS Virtual PC 2007. Can anybody help?

---

### Post by aidave on 2008-08-25
Unfortunately Ubuntu isnt anywhere close to Windows XP when it comes to handling screen resolution, or multiple monitors, via GUI.  Which sucks IMO.

If you have NVIDIA they have a handy tool to configure your screen and save changes to xorg.conf

---

