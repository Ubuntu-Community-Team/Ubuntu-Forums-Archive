---
title: "panp5/star1 resume differences[1]: authentication"
date: 2009-12-28
forum: System76 Support
---

### Post by tlroche on 2009-12-28
Dunno how unique this is, but I'm a linux-desktop newbie in a 2xSystem76 household: I've started intensively using a PanP5 (running vanilla jaunty), and my GF just got a Starling (running UNR jaunty), which I've been setting up. I'm noticing some differences in standby/resume behavior between the boxes, which I'd like to harmonize:

If one puts the panp5 to sleep, then resumes it, one gets a GINA dialog, from which one can login, switch user, etc. I like this, since there are several folks in our house, and we share boxes.

If one puts the star1 to sleep, then resumes it, one is immediately in the session of the previous user. I don't like this, for the same reason: I don't want one person to put the star1 to sleep, then another person be able to resume the first person's session.

How to make the star1 behave like the panp5, and require authentication on resume?

---

### Post by thomasaaron on 2009-12-28
Again, I have no access to either computer until Wednesday. But if you open a terminal and run...

gconf-editor

You can then go to apps > gnome-power-manager > lock and select the checkbox by "suspend" and it should prompt for a password when you resume from suspend. (You may need to reboot before the settings take effect.)

Let me know if that doesn't work, and I'll look into it further on Wednesday.

---

### Post by tlroche on 2009-12-28
> **thomasaaron said:**
> if you open a terminal and run...

gconf-editor

You can then go to apps > gnome-power-manager > lock and select the checkbox by "suspend" and it should prompt for a password when you resume from suspend. (You may need to reboot before the settings take effect.)

/apps/gnome-power-manager/lock/suspend was already checked. However 
its long description says

> 
Whether the screen is locked when the computer wakes up from a
suspend. Only used if lock_use_screensaver_settings is false.


and use_screensaver_settings was checked. (Also 
/apps/gnome-power-manager/lock/gnome_keyring_suspend is not (though "gnome_keyring_hibernate" is.) So I unchecked /apps/gnome-power-manager/lock/use_screensaver_settings while keeping the rest unchanged, which worked.

> **thomasaaron said:**
> (You may need to reboot before the settings take effect.)

That was not necessary: on the Starling I just closed gconf-editor, hit Fn-F1 to suspend, waited a bit, then hit the power button: I got the GINA on resume. Thanks!

---

### Post by riseringseeker on 2010-01-25
> **tlroche said:**
> /apps/gnome-power-manager/lock/suspend was already checked. However 
its long description says



and use_screensaver_settings was checked. (Also 
/apps/gnome-power-manager/lock/gnome_keyring_suspend is not (though "gnome_keyring_hibernate" is.) So I unchecked /apps/gnome-power-manager/lock/use_screensaver_settings while keeping the rest unchanged, which worked.



That was not necessary: on the Starling I just closed gconf-editor, hit Fn-F1 to suspend, waited a bit, then hit the power button: I got the GINA on resume. Thanks!

I was googling and searching the forums for how to make it NOT ask for a password on resume from suspend.  I found the above works, but **only** when I either close the lid or do an Fn-F1.  If I choose suspend from the indicator applet (where I would normally logout/shutdown) it still asks for a password - any clue?  

BTW, I can hit any key to resume from suspend.

---

