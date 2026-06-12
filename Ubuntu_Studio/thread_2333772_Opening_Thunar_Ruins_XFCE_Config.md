---
title: "Opening Thunar Ruins XFCE Config?"
date: 2016-08-12
forum: Ubuntu Studio
---

### Post by mikey93898 on 2016-08-12
Hey all,

So, I start my computer and see one config/setup (ie: settings, position of icons, visibility of mountable drives, etc). Then, the second I open Thunar, my config suddenly changes to something else (ie: different settings, different positions of icons, etc). Both sets of configs seem to save themselves.

This would be fine I suppose, if it weren't for the fact that my "Settings Manager" and subprograms aren't able to configure the 2nd config; the one that applies after opening Thunar for the first time.

So basically I'm left with a Desktop environment that I'm unable to configure, since one of the first things I do is open Thunar for something.

How should I go about debugging this, or determining which config the runtime is pointing to at any given time, or syncing the settings manager with my XFCE environment? I've already tried completely uninstalling and reinstalling thunar+xfce+settingsmanager and a few others to no avail.

Flavor: Ubuntu Studio
"lsb_release -a" says:
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

XFCE::About says I'm on version 4.12
"thunar --version" says: Thunar 1.6.10 (Xfce 4.12)

Any suggestions?

---

