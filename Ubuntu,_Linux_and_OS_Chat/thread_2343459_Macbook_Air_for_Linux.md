---
title: "Macbook Air for Linux"
date: 2016-11-16
forum: Ubuntu, Linux and OS Chat
---

### Post by evilvargon on 2016-11-16
I am currently a computer science student and have an MSI Gaming laptop. I have been dual booting Ubuntu and Windows 10 since my program requires Linux terminal. However, I haven't used windows in months. My gaming laptop isn't being used for gaming, I have a desktop for that now. So I put my laptop up for trade in hopes of getting something smaller, lighter, and with a longer battery life. I have gotten a trade request from a person who owns a 13 inch 2016 Macbook air ($1199 model at [http://www.apple.com/ca/macbook-air/specs.html](http://www.apple.com/ca/macbook-air/specs.html)). First thing I would do is of course replace OSX with Ubuntu.

Would this be a good trade considering my needs? Are there many issues going from OSX to Ubuntu? I would love any and all opinions on the matter.

---

### Post by g33zr on 2016-11-18
You can either dual-boot Ubuntu with OSX or wipe OSX and install Ubuntu over it. To dual-boot, I recommend that you install rEFInd within OSX (see: [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)) and then follow Rod Smith's instructions carefully. Some people recommend devoting at least part of your partition table to OSX so that you can perform firmware updates. Other people advocate running Linux only. I've done both and see the logic of both alternatives. In either case, however, I recommend that you set up your boot partition as /boot/efi, followed by /, swap, /home, and whatever other partition you think might be necessary. Good luck!

---

### Post by &amp;KyT$0P# on 2016-11-18
> **g33zr said:**
> Some people recommend devoting at least part of your partition table to OSX so that you can perform firmware updates. 
That's not the only reason to hang on to Mac OS.  I needed it for set up graphics on my MacBook Pro.

Do dual-boot, or at least be sure to keep an installation of Mac OS on hand.  Then you won't be caught out.

---

### Post by g33zr on 2016-11-18
^Yes, good point. Should you get caught out, you might have to take your Mac to the nearest Apple store or repair shop and pay to have MacOS reinstalled.

---

