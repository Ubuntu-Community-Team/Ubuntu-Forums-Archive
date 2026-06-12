---
title: "Firefox and Ubuntu 64; Why no love?"
date: 2007-08-30
forum: Testimonials &amp; Experiences
---

### Post by coolcalt on 2007-08-30
So what issues have to be resolved to get Firefox to work in ubuntu 64?  I have Gutsey Gibbon installed now.  I made the leap to linux only back in April.

What can I do to speed along the process of getting a browser that I love to work ?  

I know many of you like to point to helpful pages to set up firefox through downloading and scripting and cross your fingers it may work.  

Is it that flash and java are not distributing bits in Linux or is there more to it?

---

### Post by rsambuca on 2007-08-30
The browser works fine in 64bit. Don't blame firefox or mozilla if adobe and sun don't make 64 bit plugins.  In any event, there are scripts that will do everything for you now, so it only takes a double click to get them both working.  In the meantime, keep complaining to adobe.

---

### Post by RomeReactor on 2007-09-01
Hi. To get Java working on Firefox 64 bit, open a terminal (Applications->Accessories->Terminal) and install the following packages:
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre java-gcj-compat java-gcj-compat-plugin gcjwebplugin-4.1
```
To get Flash working use [this script by Kilz]("http://ubuntuforums.org/showthread.php?t=476924").

Yes, the problem is that there's no Flash and no Java plugin for 64 bit, for any OS (as far as I know); we'll just have to make do with these workarounds while we wait for Sun and Adobe to release proper solutions.

Hope this helps.

---

