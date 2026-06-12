---
title: "ATI Driver working perfectly"
date: 2009-04-27
forum: Testimonials &amp; Experiences
---

### Post by srikanth.janardhan on 2009-04-27
I installed Jaunty on my Compaq Presario Desktop with Intel P4, ATI Radeon Express 200 graphics Card. The installation was a breeze and was really fast.

Only thing was that the desktop effects could not be enabled. I went through hundreds of forums and yet I was not able to get a proper solution.

I tried to experiment on my own and in my xorg.conf file, I added

[php]Driver        "radeon"
Option          "AccelMethod"    "EXA"  
Option          "EnablePageFlip" "true" 
Option          "TripleBuffer"   "true" 
Option          "DynamicClocks"  "on[/php]to the Device Section and did not make any other changes. I restarted the X Desktop by pressing Ctrl+Alt+BackSpce, and logged in to a console session and typed

[php]sudo /etc/init.d/gdm restart[/php]and all the desktop effects could be enabled. I also experimented the above with the ati, vesa drivers, but they did not run satisfactorily well. One can also try "ati", "vesa", in the Driver Field in xorg.conf.:):P:guitar:

---

### Post by =^,^= on 2009-04-27
> **srikanth.janardhan said:**
> I installed Jaunty on my Compaq Presario Desktop with Intel P4, ATI Radeon Express 200 graphics Card. The installation was a breeze and was really fast.

Only thing was that the desktop effects could not be enabled. I went through hundreds of forums and yet I was not able to get a proper solution.

I tried to experiment on my own and in my xorg.conf file, I added

[php]Driver        "radeon"
Option          "AccelMethod"    "EXA"  
Option          "EnablePageFlip" "true" 
Option          "TripleBuffer"   "true" 
Option          "DynamicClocks"  "on[/php]to the Device Section and did not make any other changes. I restarted the X Desktop by pressing Ctrl+Alt+BackSpce, and logged in to a console session and typed

[php]sudo /etc/init.d/gdm restart[/php]and all the desktop effects could be enabled. I also experimented the above with the ati, vesa drivers, but they did not run satisfactorily well. One can also try "ati", "vesa", in the Driver Field in xorg.conf.:):P:guitar:

I dont understand that but it gives me hope! x]

---

### Post by Luiggipro on 2009-04-27
> **=^,^= said:**
> I dont understand that but it gives me hope! x]

:lolflag: LOL , anyways glad the open source drivers worked for you, I use the propietary fglrx drivers and they work great too :)

---

### Post by srikanth.janardhan on 2009-04-28
> **Luiggipro said:**
> :lolflag: LOL , anyways glad the open source drivers worked for you, I use the propietary fglrx drivers and they work great too :)

Thank you.

---

