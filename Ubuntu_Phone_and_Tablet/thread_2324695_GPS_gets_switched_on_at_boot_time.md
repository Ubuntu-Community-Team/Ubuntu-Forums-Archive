---
title: "GPS gets switched on at boot time"
date: 2016-05-15
forum: Ubuntu Phone and Tablet
---

### Post by andrew-q2 on 2016-05-15
hi,   for a few weeks now, perhaps since OTA10, GPS is being switched on when I power up my MX4 with Ubuntu Touch.  Within about 30 seconds, the icon appears at the top and Battery shows it switched on.  Are others getting this please?  I don't like this, it wastes battery, and it's not the sort of good behaviour I expect from Ubuntu!  I know GPS is a bit confusing, with several settings under Privacy \ Location, but I think it's quite nice to leave these alone, and use the Battery setting as a "master" switch.

On a separate query, does anyone know if anything is happening about a Touch version of something like 7Zip please, i.e. zip file processing including encryption?

Also, the Storage info is showing Cut the Rope Free using 31Mb.  I don't think I ever installed that, and last time I looked, there was no such app, so I couldn't un-install it (just the paid for version in the store).  Can I get rid of this / how please...

Thanks, Andrew

---

### Post by donquichot2016 on 2016-05-19
I have the same problem on my BQ E5. But GPS is shown as turned on **only** on the battery page, and not in the location indicator at the top. Have you filed a bug yet?

You use tar/gzip/gnupg from the terminal to archive/compress/encrypt files. I don't know of any easy zip programs, like on the desktop version (e.g. file-roller).

Cut the rope comes pre-installed on some phone, so you can't easily uninstall it. You would have to the mount the OS partition as writable and then manually remove it.

---

### Post by David_Farkas on 2016-05-20
Yes, the Cut the rope free is pre-installed. Just press and hold the apps icon and then choose uninstall.

---

### Post by andrew-q2 on 2016-05-22
Thanks donquichot.
I haven't filed a bug report I'm afraid.
I will try gzip etc, good call!  (though Terminal is a fiendishly small font as I recall)
Mounting the partition is probably a bit risky with my limited knowledge, but thanks for the info.  Doesn't stuff like this interfere with future updates?
Regards, Andrew

---

### Post by andrew-q2 on 2016-05-22
David, the thing is, there's no icon. It's not down the side of the screen, and not among the apps in the standard scope, only the paid-for version.  A.

---

### Post by donquichot2016 on 2016-05-22
Okay. On my phone it looks like GPS is not actually turned on, but just appears on in the GUI. I tried getting the location in uNav and SensorStatus, but nothing happens until I manually turn on GPS. Do you get the same behaviour on your phone?

You can change the font size in the configuration screen of the Terminal app.

Yes, mounting that partition writable disables image-based updates (OTA updates). But the updates are turned back on after you remount the partition as read-only. And I agree, it's not worth doing, unless you absolutely need to recover some extra storage space.

---

### Post by andrew-q2 on 2016-05-23
hi again, regarding GPS, I think there is a further factor confusing things, which I've suspected before, and which is that apps don't seem to respond to GPS being turned on, even when you re-launch them.  You have to re-boot, poor.  This is what I checked out just now...   1) turn on (boot up) phone and wait for GPS icon to appear at the top of the screen. Battery also shows it as now on.  2) Turn off via Battery.  3) Try Nearby scope. It can't find me (though I'm outside).  Neither can HERE maps.  4) Turn on GPS.  Try Nearby and HERE again - no good.  5) Re-boot and wait for icon to appear.  6) Nearby and HERE now finding me.  (Incidentally I have GPS only set in privacy i.e. no WiFi or phone used for location sensing).  So yours and mine seem to be behaving a bit differently.

---

