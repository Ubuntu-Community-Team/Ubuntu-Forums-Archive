---
title: "Lightdm"
date: 2012-05-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Miykel on 2012-05-04
G'Day, Well I fixed it this time, I uninstalled gdm then run "sudo dpkg-reconfigure lightdm" then rebooted, got to the Ubuntu screen, with the "dots", and thats where it stopped, pressed Esc to see what was going on, two entries of concern,
 1  start lightdm
 2 stop  lightdm
Any ideas how to make lightdm keep running, or is it something else ??
Regards Miykel

---

### Post by ronacc on 2012-05-04
try this , open a terminal ( ctrl+alt+F1 ) then enter ```
 sudo service lightdm start 
```

---

### Post by Miykel on 2012-05-05
Thanks ronacc, I did that when I removed gdm, and tried again in the recovery/drop to root, but no good, push comes to shove I'll reinstall, but I'd like to know how to get around these things for my own sake.
Regards Miykel

---

### Post by MacUntu on 2012-05-05
Dude, what's that thread title supposed to tell me? oO

---

### Post by mörgæs on 2012-05-05
Please use a more informative thread title.
Changed.

---

### Post by Miykel on 2012-05-05
Sorry about the title, I'll be more specific in future. 
 Could not resolve the problem so I reloaded the system.
Regards Miykel

---

