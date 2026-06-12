---
title: "Why was the screens and monitors menu removed in Hardy?"
date: 2008-05-18
forum: The Cafe
---

### Post by Methuselah on 2008-05-18
At least, I couldn't find it.
I eventually found out it invoked displayconfig-gtk so I launched it and was able to get widescreen resolutions. Question is....why remove it from the menu?

---

### Post by KOld Iron on 2008-05-18
Yes, this has been asked many times already. Fact is that is has NOT been removed, just cleverly hidden (no idea why, somebody really just had a very wrong idea about this). Anyways, this how you get it:

It can be found in your menu at "Other". But to make it more challenging :-( you first need to enable it through "System/Preferences/Main Menu/Other" and select it, so it will be shown in the menu tree. After that it's there and ready for use.

---

### Post by Joeb454 on 2008-05-18
It's still there, it is just hidden.

Right click the Applications Menu, and then choose edit menus.

Scroll down a little, and select "Other" and you enable it using the box on the right (it's in there somewhere).

---

### Post by Methuselah on 2008-05-18
Thanks, I figured it might be hidden as well but didn't know where to find it. Hiding it is definitely not the best idea.

---

### Post by 23meg on 2008-05-18
[http://www.bryceharrington.org/drupal/display-config-2](http://www.bryceharrington.org/drupal/display-config-2)

---

### Post by Methuselah on 2008-05-18
> **23meg said:**
> [http://www.bryceharrington.org/drupal/display-config-2](http://www.bryceharrington.org/drupal/display-config-2)

OK, I see. Still, autodetecting widescreen monitors still isn't working yet. The screen resolution preferences don't list the higher resolutions and the refresh rate was wrong with no option to change it. You'll still need to use the display-config-gtk or edit xorg.conf by hand then the new resolutions and refresh rates will become available.

---

### Post by FuturePilot on 2008-05-18
Do you have a Nvidia card? If you do you should really be using the nvidia-settings.

---

### Post by Methuselah on 2008-05-18
No, it's an ATI Radeon X700.

---

### Post by 23meg on 2008-05-18
> **Methuselah said:**
> OK, I see. Still, autodetecting widescreen monitors still isn't working yet. The screen resolution preferences don't list the higher resolutions and the refresh rate was wrong with no option to change it. You'll still need to use the display-config-gtk or edit xorg.conf by hand then the new resolutions and refresh rates will become available.

Please file a bug report. [http://www.bryceharrington.org/drupal/node/51](http://www.bryceharrington.org/drupal/node/51) and [https://wiki.ubuntu.com/X/Reporting](https://wiki.ubuntu.com/X/Reporting) can help.

---

### Post by Methuselah on 2008-05-18
> **23meg said:**
> Please file a bug report. [http://www.bryceharrington.org/drupal/node/51](http://www.bryceharrington.org/drupal/node/51) and [https://wiki.ubuntu.com/X/Reporting](https://wiki.ubuntu.com/X/Reporting) can help.

Really?
I have never had X automatically detect my widescreen so I assumed it was a known limitation rather than a bug. I'm actually perfectly fine with configuring these things myself. However, it's a lot easier when the tools aren't removed. :)

---

### Post by 23meg on 2008-05-23
A known limitation is usually a valid reason to file a bug report, because it's something that needs to be fixed at some point. If X doesn't autodetect your hardware, well, it should; you shouldn't have to manually configure it. While *you* may need displayconfig-gtk in the *current* non-optimal situation with *your* combination of hardware, keeping it on the menu just advertises its presence and leads to broken configurations.

---

