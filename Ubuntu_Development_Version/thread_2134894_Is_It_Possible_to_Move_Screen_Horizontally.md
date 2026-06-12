---
title: "Is It Possible to Move Screen Horizontally?"
date: 2013-04-12
forum: Ubuntu Development Version
---

### Post by ping-wu on 2013-04-12
[INDENT]                     Since moving away from Precise, I lost the ability to scroll the  screen horizontally.  I miss it.  Is there any way to put it back to  Raring?                 Currently I am using the left and right cursor keys to shift the screen left and right, respectively.

(Resubmitted b/c previous submission was confusing.)
[/INDENT]

---

### Post by mc4man on 2013-04-12
> **ping-wu said:**
> [INDENT] 					Since moving away from Precise, I lost the ability to scroll the  screen horizontally.  I miss it.  Is there any way to put it back to  Raring? 				Currently I am using the left and right cursor keys to shift the screen left and right, respectively.

(Resubmitted b/c previous submission was confusing.)
[/INDENT]
Not too sure this is any less 'confusing'
scroll in a window, (contents of), or scroll workspaces?

---

### Post by ping-wu on 2013-04-12
should be "scroll in a window".  IOW, when viewing a web page, I can use the two fingers-scrolling, after this feature is activated, to scroll the screen/window up or down.  But now I can't scroll the window horizontally.

---

### Post by mc4man on 2013-04-12
just to note - I only have 1 finger scrolling possible on this touchpad, but  by default hortzontal scrolling is disabled & not in System Settings > mouse and touchpad.

So for me to enable have to do so in gsettings (org.gnome.settings-daemon.peripherals.touchpad horiz-scroll-enabled

---

### Post by dino99 on 2013-04-12
gpointing-device-settings should do what you need also.

---

### Post by ping-wu on 2013-04-12
Thanks.  (Probably due to the horrific problems I had experienced with dconf in the 11.xx days, I was always afraid to use dconf.)

Now the horizonally scrolling is BACK!  Thanks again.

For someone like me who never used dconf, the steps are as follows:

Dash -> dconf editor -> gnome -> settings-daemon -> peripherals -> touchpad then check the horiz-scroll-enabled box

---

### Post by mc4man on 2013-04-12
> **ping-wu said:**
> Thanks.  (Probably due to the horrific problems I have experienced with dconf in the 11.xx days, I was always afraid to use dconf.)

Now the horizonally scrolling is BACK!  Thanks again.

For someone like me who never used dconf, the steps are as follows:

Dash -> dconf editor -> gnome -> settings-daemon -> peripherals -> touchpad then check the horiz-scroll-enabled box

Seems like one of the default settings (disabled)  that should be overridden, particularly because it's not shown in System Settings.
Maybe I'll file a bug on (ubuntu-settings) & see if there is any response
(I set it to be the default here with no issues.. screen

---

### Post by mc4man on 2013-04-12
For the heck of it - 
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1168494](https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1168494)

---

