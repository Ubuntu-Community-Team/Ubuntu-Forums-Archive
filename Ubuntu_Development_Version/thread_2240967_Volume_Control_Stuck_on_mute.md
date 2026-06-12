---
title: "Volume Control Stuck on mute"
date: 2014-08-23
forum: Ubuntu Development Version
---

### Post by hiltonking on 2014-08-23
[SOLVED] I've tried a few things but I can't unmute the volume.  I can move the slider up and down but it this pop up, [http://i.imgur.com/rIScBth.png](http://i.imgur.com/rIScBth.png) remains.
  Please let me know what further info you require so I may be helped.
  Also the volume works on the other accounts.

Running a dall xps 210. It happened when I was raising the volume.  I don't know why?  On ubuntu 14.10

---

### Post by hiltonking on 2014-08-24
[https://wiki.manjaro.org/index.php/Volume_Stuck_on_Mute_%28XFCE_Desktop%29](https://wiki.manjaro.org/index.php/Volume_Stuck_on_Mute_%28XFCE_Desktop%29)

---

### Post by ibjsb4 on 2014-08-24
Just a heads up :)

There is a separate forum for posting problems with 14.10.

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

---

### Post by Toz on 2014-08-24
*Moved to the **Ubuntu Development Version** sub-forum.*

---

### Post by Cavsfan on 2014-08-24
Try this first in terminal:

```
sudo alsa force-reload
```


If that doesn't do the trick try the 1st 3 steps on this page.

[http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)

I wouldn't try step 4 though as it's not for 14.10.

Welcome to the forum. :)

---

### Post by Cavsfan on 2014-08-24
This is what mine looks like:

[ATTACH=CONFIG]255804[/ATTACH]

---

