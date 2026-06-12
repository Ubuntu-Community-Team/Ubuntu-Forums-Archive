---
title: "[Elementary] MacBookAir6,1 and Elementary OS Loki"
date: 2017-12-09
forum: Ubuntu/Debian BASED
---

### Post by x3ua on 2017-12-09
I've been using about week Elementary OS on my MacBookAir6,1. There's still few problems I can't get solved.

1.
Biggest issue is Macbooks own keyboard layout. Euro sign is missing, normally it is shift+4, but now it gives only ¤ sign. I'm using Finnish (Machintosh) layout.
<> -button between left shift and z is swapped with §° -button located right of 1. How fix this?

2.
 Webcam does not work. I don't use webcam so this is not relevant to me, but does anyone know is it even supported?

3. 
WIFI connects much slower than OSX. Maybe 15-20 seconds, when OSX took only couple seconds. Probably driver issue. Not relevant, but nice to have fix.

4. 
Battery drain fast, laptop is hot. Core temp is about 70-80 celsius. (158F-176F) CPU is not high, maybe 10-20% when browser and email are open. But clearly power saving is not good as with OSX. 

1. question is important, other are nice to know.

[IMG]https://support.apple.com/library/content/dam/edam/applecare/images/en_US/keyboards/swedish_keyboard.png[/IMG]

---

### Post by slickymaster on 2017-12-09
*Thread moved back to **Ubuntu/Debian BASED**.*

---

### Post by x3ua on 2017-12-10
No solution how to get macbook keyboard work with Xenial. :/

Is there any linux distribution that works with Macbook? I don't want to go back to OSX..

---

### Post by x3ua on 2017-12-11
I found workaround to swapped keys from here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1245081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1245081)

```
setxkbmap -option apple:badmap
```

Still need to connect eurosign to shift+4.

---

