---
title: "Machine Check Error - Ubuntu 14.04 Alpha2"
date: 2014-02-24
forum: System76 Support
---

### Post by clvx on 2014-02-24
Hi all,

I wanted to test Ubuntu 14.04 desktop edition in my lemu4, but I got 'Machine Check Error' during boot with the live cd.  I used the daily image of 02/21/14 to test the system, although with no success.

Actually my laptop is running 13.04 without issues.

If anyone knows something related to this, I'd appreciate any workaround.

Thanks in advanced.

---

### Post by isantop on 2014-02-24
Try re-downloading the image you installed from. I'm guessing that either A) the ISO image was corrupted during download/burn, or B) There was a bug in the daily image that's likely to be worked out in the near future (likely the next day's daily image).

---

### Post by clvx on 2014-02-25
I think is not a problem with the daily build. I tried to boot with a ubuntu 12.04 disk, and with a minimal centos, but I got the same message after bios 'Machine Check Error'. 
Also, I tried to boot with a windows 7 disk, and it worked without an issue.

So far, centos and ubuntu images aren't helpful. well, i'm running out of ideas, any idea will be good to hear.


PS: probably I pass this thread to general discussion 'cause it seems that it's not related specifically to system76.

---

### Post by clvx on 2014-02-25
Got it ..

Grub was giving me the problems, after running sudo update-grub everything started to work properly.

---

