---
title: "How do I change my graphics card driver and settings?"
date: 2008-01-22
forum: Ubuntu Christian Edition
---

### Post by endacoz on 2008-01-22
I got Ubuntu set up a few days ago and got drivers and everything set up just right.  Then i found out that there was Ubuntu CE (Christian Edition)  I just finished installed CE from scratch.  There is one obvious difference from normal to CE and that is that I do not see an option in administration to setup the graphics driver and monitor type.  This option was in Ubuntu  but I do not see it in CE.  Can someone help me?  What would be a command to bring up the settings for such?  Reason I want to do that is my resolution is 800x600 and My video card will do much more that that.  Any help would be great!

Thanks

---

### Post by renzokuken on 2008-01-22
open a terminal and run

```
sudo dpkg-reconfigure xserver-xorg
```

follow the wizard through to the resolution page and select the resolutions your card is capable of. may also be worth noting which driver is currently being used.

---

