---
title: "Different Power Management Woe... (Turning off suspend)"
date: 2009-06-19
forum: System76 Support
---

### Post by Derath on 2009-06-19
I already posted in the earlier power management thread, but I'm hoping I can find a workaround in this thread... I just upgraded from 8.10 to 9.04, or rather due to tracker/bad sata controller (whatever), I have a "fresh" install of 9.04 (whimpers a little due to losing some files from corruption).

So when I am at home I leave the pangolin plugged in all the time and just close the lid when not in use. I have a bunch of IM's, IRC, Mail client with multiple accounts, etc running to keep in contact with people. Here's the problem: For whatever reason, after leaving it idle and lid closed the pangolin goes into Suspend to RAM/Sleep Mode. Needless to say, when it goes into Suspend/Sleep mode, network connection is stopped, which in turn removes the effectiveness of the IMs and Email

I have already set KDE's power management app, KDE's system settings app, and Gnome's power management app to only lock the screen when the lid is closed, and do nothing else while AC is plugged in. I have double checked the settings, and the only time it should go into sleep mode is when on battery and idle for more than 20 minutes.

Notes from the other thread: Of course the kde and gnome power apps don't recognize when the AC is unplugged, but does show the battery discharging and gives an estimated time left. Also the screen dims and all when AC is removed. So I believe it is safe to say that the system knows when AC is connected.

Any ideas would be GREATLY appreciated! Resolutions would be EXTREMELY helpful!

Thanks!

---

### Post by Derath on 2009-06-24
I hate to do a shameless bump, but I am still experiencing issues with this. If anyone has any recommendations, please let me know!

---

### Post by thomasaaron on 2009-06-25
I'm not getting this on our shop Pangolin.

When I set AC to "Blank Screen" when the lid is closed, it doesn't go into suspend.

It could be that there is a conflict between KDE's and Gnome's power manager.

---

