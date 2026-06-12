---
title: "How Do I add winemp3 file to Wine?"
date: 2011-06-28
forum: Wine
---

### Post by stevedude on 2011-06-28
Hi all,

I'm running Wine 1.2.2 with Ubuntu Natty and I wanted to add "winemp3" [winemp3.acm] to the default Wine configuration from the Wine Libraries for a program I want to use. When I navigate to "Configure Wine" > "Libraries" tab, that file does not show up in the libraries. I checked Windows/System32 in Wine and it is listed there.

My question is; How am I able to add that file to the Wine Libraries so that I can then add it to my configuration? 

Thanks

---

### Post by stevedude on 2011-07-07
Bump. Anyone know how to do this?

---

### Post by Tweak42 on 2011-07-07
Try following this thread on how they got the msgsm32.acm codec installed.

[http://ubuntuforums.org/showthread.php?t=923017](http://ubuntuforums.org/showthread.php?t=923017)

---

### Post by stevedude on 2011-07-07
Thanks tweak42. Your link led me to: [http://www.codeweavers.com/compatibility/browse/name/?app_id=5479;tips=1](http://www.codeweavers.com/compatibility/browse/name/?app_id=5479;tips=1)

winemp3.acm does not appear in the Wine Libraries, even after DL'ing and copying to the file into programs bottle Windows folder as stated in the link's instructions. If you follow those steps outlined above and manually type in the file name in the Wine library then choose "Add", then reboot your bottle it works! 

I was expecting the file to appear in the drop-down list. You just have to manually type it in the drop-down list box, then add it to the library and then the file is recognized.

---

