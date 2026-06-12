---
title: "I just had a breakthrough with wireless and ndiswrapper!"
date: 2011-05-13
forum: The Cafe
---

### Post by RJ12 on 2011-05-13
Ok, so if you look at my posts that I have made, you will see that I have been using NDISwrapper for quite a while... because Ubuntu would not connect to my router (with a password) but would connect fine to the open networks... I just figured out what was wrong! It was not the drivers, not the card... but it was the router!! We just got a new router a couple of days ago, and right now I just pulled up a live usb of Ubuntu 10.10 and when I tried to connect to my network, it connected properly!!! When I pulled up Firefox to test the internet, it worked!! I just had a breakthrough! I guess there was some incompatible setting on the old router which made my computer not want to connect to it, and somehow NDISwrapper was fixing it behind the scenes I guess... whatever it is... I'm happy!

---

### Post by doorknob60 on 2011-05-13
Don't know if the router is completely to blame there since it worked with the Windows driver, but maybe so. Glad you got it working though :)

---

### Post by RJ12 on 2011-05-14
I just realised... this means I can use 64Bit now! This was the thing holding me back from 64bit!!

---

### Post by NormanFLinux on 2011-05-14
Why? NDISwrapper isn't necessary with new computers. If your computer has an Atheros or Broadcom wireless chipset, Ubuntu should support it out of the box. You seldom need a Windows driver for Internet connectivity nowadays.

---

### Post by RJ12 on 2011-05-14
> **NormanFLinux said:**
> Why? NDISwrapper isn't necessary with new computers. If your computer has an Atheros or Broadcomm wireless chipset, Ubuntu should support it out of the box. You seldom need a Windows driver for Internet connectivity nowadays.

It's complicated... I thought that the driver OOTB didn't allow me to connect to Secured Networks.. I guess I was wrong and it turns out it was most likely due to my router!

---

### Post by 3rdalbum on 2011-05-14
A lot of people have little problems with their wireless, not because of a lack of drivers but because their router doesn't stick to standards or the WRONG driver is loading. Then they install Ndiswrapper and it's not compatible with that Windows driver. Then they try to follow the instructions for native drivers, but Ndiswrapper prevents the native driver from working.

---

