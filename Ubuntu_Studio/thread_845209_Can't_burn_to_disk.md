---
title: "Can't burn to disk"
date: 2008-06-30
forum: Ubuntu Studio
---

### Post by Niekk on 2008-06-30
Hi,

I have some videos (.avi) and converted them with DeVeDe to .iso's. The structure seems okay. 
But when I burn it to a DVD, I can't play it with my home DVD player. I burn the .iso's by right clicking on the .iso, and select "CD/DVD Creator" and enter the maximum write speed.
I am completely sure of the writing speed, but it does not work on my DVD player @ home. When I insert the DVD in my ubuntu computer again, immediately "Movie Player" pops up and plays my DVD.

Why isn't it working ?

Best Regards,
Niek van der Steen

---

### Post by cjv8888 on 2008-07-01
The problem is probably due to the genisoimage file in Hardy.
You may need to downgrade to version 1.1.2 or compile to version 1.1.8.
Have a look at this 

[thread]("http://ubuntuforums.org/showthread.php?t=787299")

---

### Post by alegallo on 2008-07-01
I had more or less the same problem as you, but with DVDStyler. 
I solved it by installing the 1.1.8-1ubuntu3 version of genisoimage, which requires also mkisofs to be installed.

To do this I had to add the gutsy repositories amongst my sources, then I had to force the downgrade of geisoimage from version 1ubuntu6 which comes with hardy to 1ubuntu3 from gutsy.

This uninstalled DVDStyler and ManDVD, then I blocked the version of genisoimage at 1ubuntu3, reinstalled the 2 apps and mkisofs too, and everything worked like charm now.

It seems that genisoimage 1.1.8-1ubuntu6 includes the mkisofs functions, but it must be buggy, at least in my hardy 64bit.

I followed the thread linked by cjv8888 too.

---

