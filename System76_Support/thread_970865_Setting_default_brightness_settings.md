---
title: "Setting default brightness settings"
date: 2008-11-04
forum: System76 Support
---

### Post by Beridel on 2008-11-04
I just had a quick question thats been on my mind for a while about my GazV5.  Is there a way to set up default brightness for when the laptop is plugged in and when it isn't?  I would like to keep my brightness at minimum while its not plugged in, and at maximum while its plugged in.  When I adjust it with the function keys, it always resets back to the default value and I'm just curious if its possible to change that.

Thanks for the help in advance!

---

### Post by perce on 2008-11-05
Open gconf-editor and go to:

apps > gnome-power-manager > backlight

and change the setting there.

There used to be an easy way through the gnome-power-manager GUI , but they removed it a couple of releases ago; maybe the gnome team thought it was too difficult for their grandmathers.

---

### Post by Beridel on 2008-11-05
Awesome, works perfectly.  Thanks :)

---

### Post by dlzerocool on 2010-09-27
Thank you, that's exactly what I was looking for.
(They should add a slider on the gnome power management tool to change this value.) Because 50% is now good for all netbooks/notebooks.

---

### Post by test_tube_baby on 2011-02-18
This doesn't work for me. I change the values in gconf-editor > apps > gnome-powermanager > backlight

But they have no effect, still when I plug my battery in the default brightness is around 90-100% and around 60% when on battery. I want to reduce these values and I did it on gnome power manager but it doesn't actually have any effect.

What am I doing wrong? Please help!

---

### Post by StephenDavison on 2011-02-18
Is that the same window you get to from
System -> Preferences -> Power Management ?

The "On AC Power" tab has a default brightness setting.
The "On Battery Power" tab has a checkbox to "Reduce backlight brightness"

---

### Post by test_tube_baby on 2011-02-18
There is no reduce brightness level tab under 'On AC Power' but there is a checkbox for reduce backlight level under 'On Battery Power'

WHAT DO I DO....?

---

### Post by StephenDavison on 2011-02-18
I was thinking you'd set the higher brightness level you want using the slider on the On AC Power tab, and also check the 'Reduce backlight brightness' box on the On Battery Power tab.  Brighter when plugged in, dimmer when on battery.  It may not dim as much as you want when on battery power, but that's as close to your original description as I can think of.

---

