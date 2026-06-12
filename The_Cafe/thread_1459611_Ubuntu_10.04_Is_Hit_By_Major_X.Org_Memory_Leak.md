---
title: "Ubuntu 10.04 Is Hit By Major X.Org Memory Leak"
date: 2010-04-21
forum: The Cafe
---

### Post by Excedio on 2010-04-21
[http://it.slashdot.org/story/10/04/21/2021247/Ubuntu-LTS-Experiences-Xorg-Memory-Leak](http://it.slashdot.org/story/10/04/21/2021247/Ubuntu-LTS-Experiences-Xorg-Memory-Leak)

> *Ubuntu 10.04 LTS Beta 2 is experiencing a major [memory leak due to patches for X.org]("http://www.phoronix.com/scan.php?page=news_item&px=ODE3MA"). 'An X.Org Server update that was pushed into the Lucid repository last week has resulted in the system being slower and slower as it is left on, until it reaches a point where the system is no longer usable. ... In order to make the Ubuntu 10.04 LTS deadline, the developers are looking at just reverting three of the patches, which brings the GLX version back to 1.2. Ubuntu developers are now desperate for people willing to test out this updated X.Org Server package so they can determine by this Friday whether to ship it with Ubuntu 10.04 LTS or doing an early SRU (Stable Release Update). Right now this X.Org Server that's being tested is living in the ubuntu-x-swat PPA.'*

Well, this is not good to hear 8 days before release.

---

### Post by frankbooth on 2010-04-21
Lets hope it gets sorted [-o<

---

### Post by doas777 on 2010-04-21
either way, it'll get sorted, but we may have to wait for glx 1.4 (not that I really understand the differance to kibitz about version numbers). if they pull the patches, I don't think most of us would notice.

---

### Post by gnupipe on 2010-04-21
BAD NEWS  :evil:

---

### Post by K.Mandla on 2010-04-21
Sigh. Xorg. #-o

---

### Post by Bachstelze on 2010-04-21
[http://ubuntuforums.org/showthread.php?t=1459417](http://ubuntuforums.org/showthread.php?t=1459417)

If you guys feel like helping...

---

### Post by fillintheblanks on 2010-04-21
it seems fine to me

---

### Post by MooPi on 2010-04-21
I haven't noticed the leak on my system.  It's running stable without a glitch or hitch or etc..........
Maybe just gnome systems ? I'm currently on the system in question beta 2 Xfce4 desktop.

---

### Post by Bachstelze on 2010-04-21
> **fillintheblanks said:**
> it seems fine to me

> **MooPi said:**
> I haven't noticed the leak on my system.  It's running stable without a glitch or hitch or etc..........
Maybe just gnome systems ? I'm currently on the system in question beta 2 Xfce4 desktop.

The bug does not affect everyone. In particular, if you are using the NVidia proprietary driver, it ships with its own GLX implementation, which replaces the one shipped with Xorg, and is not affected by the bug. I don't know about ATi drivers, but they probably do that too.

---

### Post by Excedio on 2010-04-21
I have yet to test out 10.04 beta. My plan is to usually to wait for full release.

Is there anyone here that is experiencing this?

---

### Post by Captain Smiley Pants on 2010-04-21
I downloaded it for kicks, running a intel GMA 945 and I can't even get Compiz to work for whatever reason. Couldn't before the patch either. I miss Compiz. :(

---

### Post by NightwishFan on 2010-04-21
Sure I will help if I can.

---

### Post by koleoptero on 2010-04-21
And I was wondering where the leak was...

---

### Post by Ewingo401 on 2010-04-21
I am so far not seeing any sort of memory leak.  But I'm not sure I'd be affected in the first place.  My testing machine is running the open source ATI drivers.

---

### Post by NightwishFan on 2010-04-21
In on intel mobile, and my xorg is hovering around 40mb. I have been using compiz and testing since my last post. I plan on doing some nonstandard stuff like gnome shell, games, wine, etc. See what happens.

---

### Post by adeypoop on 2010-04-22
Haven't noticed it myself. Although I don't tend to leave the computer running for long periods of time. 

I have noticed some funny things happening with XOrg when trying to play Assault Cube tho, had to turn desktop effects off to fix it. Was losing information about screen res and stuff

---

### Post by Excedio on 2010-04-30
Anyone know if this has been fixed?

---

### Post by Foster Grant on 2010-04-30
> **Excedio said:**
> Anyone know if this has been fixed?

Three days ago.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981)

---

### Post by Excedio on 2010-04-30
Awesome :-)

---

### Post by philinux on 2010-04-30
Thread closed at OP request

---

