---
title: "No &quot;Trigger secondary click by holding down the primary button.&quot; for precise 12.04"
date: 2012-04-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mutrax on 2012-04-09
Hey guys & gals,

I've installed (fresh) 12.04 b2 on my touchscreen in the bathroom (shuttle x50b with egalax touchscreen). I used to have 10.04 on it with the egalax drivers (nothing else worked descent).


I need the right click (for "back" in xbmc) functionality as before, but I can't seem to find it in the accesibility menu.

Is this left out by design? am I missing the new location? not implemented yet? 

the touchscreen uses usbtouchscreen module, and calibration was pretty easy (had to cut-paste some hid settings, but still easier than in the past)

I've tried the egalax touch drivers to, they work, but are buggy (lockup of click functionability)

Any help or pointer in the right direction would be greatly appreciated. 

Overall great release!

---

### Post by sffvba[e0rt on 2012-04-09
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*


404

---

### Post by ojdon on 2012-04-09
I'm assuming it's only missing in Unity? How about moving to Gnome-shell instead? The option should be under Mouse settings

Unity isn't designed for tablets and won't be for several future releases. Gnome-Shell however is looking to be fit for Tablets/Touchscreens in the next few releases!

---

### Post by mutrax on 2012-04-09
hey ojdon, 
If I don't figure this one out I'll give it a try (or gnome-classic)....

I'ml taking precise for a spin for this reason... It did the trick in lucid so one would expect no significant loss of functionality... I'll keep digging around, or give the egalax drivers a go ad find out why they bug.

---

### Post by Mr. Picklesworth on 2012-04-09
This is under Universal Access settings. Control Center has been pretty extensively patched, with many panels only showing in Unity (and other strange decisions leaking over to Gnome Shell), but I don't think anyone has touched the UA panel.

It's called "Simulated Secondary Click" in the "Pointing and Clicking" tab.

[ATTACH]215764[/ATTACH]

---

### Post by mutrax on 2012-04-09
> **Mr. Picklesworth said:**
> This is under Universal Access settings. Control Center has been pretty extensively patched, with many panels only showing in Unity (and other strange decisions leaking over to Gnome Shell), but I don't think anyone has touched the UA panel.

It's called "Simulated Secondary Click" in the "Pointing and Clicking" tab.

[ATTACH]215764[/ATTACH]

found that, but in the localized dutch version, its claimed to be a double click, and even that doesn't work (guess that IS a bug)

thanks for taking the time answering me.

---

### Post by Mr. Picklesworth on 2012-04-09
It happens when you *release* the mouse button, by the way. I wasn't expecting it to behave that way, so perhaps you're doing the same.

---

### Post by mutrax on 2012-04-09
> **Mr. Picklesworth said:**
> It happens when you *release* the mouse button, by the way. I wasn't expecting it to behave that way, so perhaps you're doing the same.
Oh my (does it on shell, presume unity to)!  Thanks a million kind sir! +1  internets for you.

It does work with mouse , so if it doesn't on touching the screen its a touch issue (I'm not at the display atm.)
now lets see if i can get the single tap to open desktop shortcuts and i'm off testing 12.04 on touch

---

