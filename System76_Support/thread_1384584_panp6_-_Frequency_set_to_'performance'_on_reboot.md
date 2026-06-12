---
title: "panp6 - Frequency set to 'performance' on reboot"
date: 2010-01-18
forum: System76 Support
---

### Post by revlimiter on 2010-01-18
I just got delivery of my shiny (er, matte) new panp6. Doing the initial system switchover stuff from my old Asus lappy. 

I turned on the frequency scaling monitor on the panel. I noticed that it defaults to "Performance" mode when I have to restart the system for any reason. So it's stuck at 2.5 ghz until I turn it back to "On Demand". Is there a way to select on demand by default? I don't usually reboot my systems very often and would love to not have to remember to do this. 

thanks!

---

### Post by revlimiter on 2010-01-18
[http://ubuntuforums.org/showpost.php?p=8577483&postcount=10](http://ubuntuforums.org/showpost.php?p=8577483&postcount=10)

solved. Now it starts up in On Demand. :D

---

### Post by bryanagee on 2010-01-18
You can change the default settings for this with gconf-editor:

apps -> gnome-power-manager -> cpufreq

---

### Post by revlimiter on 2010-01-18
Not in Karmic. The cpufreq tab is now gone.

---

### Post by bryanagee on 2010-01-18
Right... sorry about that. I was on my jaunty machine at the time.

---

