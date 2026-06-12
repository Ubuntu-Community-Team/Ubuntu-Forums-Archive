---
title: "New ATI Drivers.. is ATI starting to look at linux?"
date: 2005-06-09
forum: The Cafe
---

### Post by sapo on 2005-06-09
So.. now the ati drivers have a installer (i dont know if it works, still didnt try), btw nvidia already have opengl 2.0 and coolbits support.. is ati just releasing this new driver to support new vgas or maybe they added some more features?

Please if anyone have tried it.. please tell us what did you think  :grin: 

Here the links:

Features:
[http://www2.ati.com/drivers/linux/linux_8.14.13.html](http://www2.ati.com/drivers/linux/linux_8.14.13.html)

Installer:
[http://www2.ati.com/drivers/linux/linux_8.14.13-inst.html#176980](http://www2.ati.com/drivers/linux/linux_8.14.13-inst.html#176980)

Download (35MB):
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

And in this installer is saying something about creating a distribution package from the installer.. btw i didnt understand it.. what about a ubuntu package? anyone could try making a package for us :D

---

### Post by Jesus Franco on 2005-06-09
WOHOO!!! 
Finally they are out! YAY!
I couldn't be happier. Thanks for posting this man.  :)

---

### Post by benplaut on 2005-06-09
i suppose nothing for the older cards...

my poor, neglected mobile radeon 7500  :cry:

---

### Post by KiwiNZ on 2005-06-09
Cool I will have to give these a try , maybe I can use my X800XT to its full potential at last , but time will tell.

---

### Post by sapo on 2005-06-09
I ve installed it and its working perfectly.. to install i ve made this:

Unistalled the fglrx driver (fglrx or xorg-fglrx) and uninstalled the linux-restricted-modules

Then just ran the installer .run and i felt like installing a windows driver.. next next next exit

Then i reboot and its working...

and now i got 770+ fps in fgl_glxgears, with the last driver i got 650+ fps.. so it increased 120 fps  :grin:

---

### Post by TravisNewman on 2005-06-09
whoa. I get about htat many fps with glxgears when I'm running vesa. OK so that's an exaggeration. But with nvidia I'm getting right around 2000 fps. They still have quite a while to go, but good on them for getting it going.

---

### Post by sapo on 2005-06-10
[QUOTE=panickedthumb]whoa. I get about htat many fps with glxgears when I'm running vesa. OK so that's an exaggeration. But with nvidia I'm getting right around 2000 fps. They still have quite a while to go, but good on them for getting it going.[/QUOTE]


You are confusing everything...

glxgears runs WITHOUT 3D support and is DIFFERENT from fgl_glxgears.. here what i got in glxgears:

```

root@stfu:/home/sapo # glxgears
19903 frames in 5.0 seconds = 3980.600 FPS
21999 frames in 5.0 seconds = 4399.800 FPS
22088 frames in 5.0 seconds = 4417.600 FPS
21976 frames in 5.0 seconds = 4395.200 FPS
21829 frames in 5.0 seconds = 4365.800 FPS
22158 frames in 5.0 seconds = 4431.600 FPS

```

the fgl_glxgears is a different test... and the results off course are different  ](*,) 

```

root@stfu:/home/sapo # fgl_glxgears
2865 frames in 5.0 seconds = 573.000 FPS
3070 frames in 5.0 seconds = 614.000 FPS
3061 frames in 5.0 seconds = 612.200 FPS
3071 frames in 5.0 seconds = 614.200 FPS
3082 frames in 5.0 seconds = 616.400 FPS
3095 frames in 5.0 seconds = 619.000 FPS

```

Btw here i was with azureus, amule, firefox and a lot of things running... just with the fgl_glxgears i have about 770fps  :grin:

---

### Post by poofyhairguy on 2005-06-10
Here is the question: Does is support xcompmgr yet? If not, my stronger ATI card will sit in the closet as a weak Nvidia card gives my eye candy.

---

### Post by gil-galad on 2005-06-10
[QUOTE=benplaut]i suppose nothing for the older cards...

my poor, neglected mobile radeon 7500  :cry:[/QUOTE]
 Well at least you get to use the open source drivers, which is better in many ways.

---

### Post by TravisNewman on 2005-06-10
doh! I missed the fgl_

SORRY!!

---

