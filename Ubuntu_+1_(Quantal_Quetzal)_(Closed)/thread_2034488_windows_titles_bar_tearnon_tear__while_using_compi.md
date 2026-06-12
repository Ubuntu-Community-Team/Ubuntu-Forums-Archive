---
title: "windows titles bar tear/non tear  while using compiz-wobbly"
date: 2012-07-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-07-28
Since Oneiric Ocelot I had noticed that during the development release  the title bar on windows would work seamlessly during a session (using wobbly windows option) and then , after an update, the horizontal tearing would be there which would make it look just awful.

Currently the title borders are working seamlessly (no horizontal tearing) but I am wondering if this will come back  as it has with previous releases?

---

### Post by effenberg0x0 on 2012-07-29
I have noticed that Sync to VBlank is on as default on ccsm for a while. I think it was not like that in the recent past. Disabling (and then restarting the session) causes a significant increase in tearing, which can easily be seen in plugins like wobbly, expo, shift-switcher. This is on NVidia GTS450 using the proprietary installer (v. 304.22). PP with same driver, default ccsm settings, is outperforming in transition effects speed and image quality/less tearing here.

Regards,
Effenberg

---

### Post by ventrical on 2012-07-31
Thanks.

 After updating to 3.5.0-6 there is very tiny noticable tearing with wobbly windows. Before that it was practically non-existent this stretch around.  I fear the same regressions will happen as Quantal progresses to release date.  It's like something upstream is always ready to be a fly in the ointment (for compiz anyways).  Thats why I like those alpha 1's and 2's .. they are so snappy!

---

