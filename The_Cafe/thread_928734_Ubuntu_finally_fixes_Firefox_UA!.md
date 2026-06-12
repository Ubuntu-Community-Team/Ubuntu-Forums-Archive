---
title: "Ubuntu finally fixes Firefox UA!"
date: 2008-09-24
forum: The Cafe
---

### Post by Vadi on 2008-09-24
As of the update to 3.0.2 firefox, the ubuntu version now properly identifies itself:
> 
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.2) Gecko/2008092213 Ubuntu/8.04 (hardy) Firefox/3.0.2

Before it just called itself "linux", and caused a massive drop in ubuntu usage according to web statistics. At least the stats will be straightening themselves out now :)

---

### Post by FuturePilot on 2008-09-24
Good to hear :)
A lot of Flash 10 issues seem to be sorted out as well with 3.0.2

---

### Post by ukripper on 2008-09-24
I hope this vulnerability is sorted out too with updates.
[http://ubuntuforums.org/showthread.php?t=928586](http://ubuntuforums.org/showthread.php?t=928586)

---

### Post by antiloop on 2008-09-24
> **FuturePilot said:**
> Good to hear :)
A lot of Flash 10 issues seem to be sorted out as well with 3.0.2

Thank god, if true. Full-screen Flash performance has been terrible.

---

### Post by Vadi on 2008-09-24
Does anyone have reliable flash 10 .debs / ppa's?

---

### Post by sefs on 2008-09-24
I still can't get flash 10 to work with stickam at [http://twitlive.tv](http://twitlive.tv).

The player just does not display correctly or work well in flash 10.

---

### Post by dasunst3r on 2008-09-24
If you want Flash 10, you should uninstall flashplayer-nonfree, download the release candidate from [http://labs.adobe.com](http://labs.adobe.com), and copy the .so file to /usr/lib/xulrunner-addons/plugins

---

### Post by kostkon on 2008-09-24
> **Vadi said:**
> Does anyone have reliable flash 10 .debs / ppa's?
I got mine from this [PPA]("https://launchpad.net/~psyke83/+archive"). Don't add the repo to your sources list if you don't want to, just download the corrensponding deb.

Just do a complete removal of the flash plugin before installing the new one.

You can easily remove it and go back to the Flash plugin provided by the Ubuntu repos if you ever decide, thus it's pretty safe to install.

---

### Post by Vadi on 2008-09-24
ok thanks

---

### Post by kostkon on 2008-09-24
> **Vadi said:**
> As of the update to 3.0.2 firefox, the ubuntu version now properly identifies itself:


Before it just called itself "linux", and caused a massive drop in ubuntu usage according to web statistics. At least the stats will be straightening themselves out now :)
Yeap, at last, they fixed the UA string. Now we can proudly surf the web knowing that we are identified as Ubuntu users. :mrgreen:

---

### Post by FuturePilot on 2008-09-24
> **sefs said:**
> I still can't get flash 10 to work with stickam at [http://twitlive.tv](http://twitlive.tv).

The player just does not display correctly or work well in flash 10.

even with Firefox 3.0.2? It works fine for me with 3.0.2

---

