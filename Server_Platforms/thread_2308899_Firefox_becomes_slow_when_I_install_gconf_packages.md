---
title: "Firefox becomes slow when I install gconf packages"
date: 2016-01-06
forum: Server Platforms
---

### Post by mario69 on 2016-01-06
Hi all,

I have a test server that is without physical graphical interface, but with a Xvfb interface. In this interface there are some selenium tests that take the time of various pages. The tests are working fine with FireFox. Now I need to add in the same server some tests that are working on Chrome.

The issue that I have is: when I try to install Chrome, it will install the packages **gconf-service gconf-service-backend gconf2-common**. But as soon as I install this 3 packages all the tests becomes more slowly of 10 seconds. When I delete the packages the time return beck to normal.

I have Ubuntu 14.04.2 LTS and Mozilla Firefox 42.0 

Thank you for any help.

---

### Post by MAFoElffen on 2016-01-06
gconf-service, gconf-service-backend & gconf2-common:  the gnome configuration database system is used for storing application preferences. It is intended for storing user preferences Google Chrome uses this system to stored it's preferences.

The translation to others reading this post is that you are doing headless browser testing. Selenium automates browsers. Xvfb is an virtual X server that can run on machines with no display hardware and no physical input devices. It emulates a dumb framebuffer using virtual memory.

You say that you run 10 seconds slower with the 3 gconf packages installed, than with them "removed". Your title (not your post, so reading between the lines in interpreting that...) states that Firefox runs 10 seconds slower, with the packages that Chrome installs as it's dependencies???. 

Your post states what is happening, and thanks us for help, BUT ... does not ask any question, nor does it ask for any kind of help--
Was there something you needed help on? Is there a specific question you have? (just because I didn't see one and wnat to make sure you are helped...)

---

### Post by mario69 on 2016-01-18
> **MAFoElffen said:**
> gconf-service, gconf-service-backend & gconf2-common:  the gnome configuration database system is used for storing application preferences. It is intended for storing user preferences Google Chrome uses this system to stored it's preferences.

The translation to others reading this post is that you are doing headless browser testing. Selenium automates browsers. Xvfb is an virtual X server that can run on machines with no display hardware and no physical input devices. It emulates a dumb framebuffer using virtual memory.

You say that you run 10 seconds slower with the 3 gconf packages installed, than with them "removed". Your title (not your post, so reading between the lines in interpreting that...) states that Firefox runs 10 seconds slower, with the packages that Chrome installs as it's dependencies???. 

Your post states what is happening, and thanks us for help, BUT ... does not ask any question, nor does it ask for any kind of help--
Was there something you needed help on? Is there a specific question you have? (just because I didn't see one and wnat to make sure you are helped...)

Yes sorry, my post was not clean.

How can I have Firefox and Chrome working on the same server without the 10 seconds delay?

---

