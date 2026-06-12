---
title: "KTechLab on Precise"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Xelort on 2012-04-20
Hi.

I'm trying to install a wonderful program called KTechLab on my netbook with the precise beta (fully up to date).

I was surprised when found that there's no pakage for the program since some time ago, as i have it installed on my desktop pc (over Lucid, 10.04). 

Searching the forum, i saw somebody noted the same thing, here: [http://ubuntuforums.org/showthread.php?t=1722912](http://ubuntuforums.org/showthread.php?t=1722912)
Please see first post on page 2.

Tried to manually install it without success, and don't want to mess again with any dependency nightmare (like it was when tried to install liquidsoap v1 on lucid) in the middle of a beta state.


So, the question is: is there any information about the future of this package? 
It's an important software for me, and i'm having a hard time trying to adapt to the alternatives.
 
Thanks.

---

### Post by cariboo on 2012-04-20
The missing paclkage, kdelibs4c2a, is still available for Natty, you can get it [here]("http://packages.ubuntu.com/search?keywords=kdelibs4c2a&searchon=names&suite=all&section=all"). I won't guarantee that it'll work though.

---

### Post by Xelort on 2012-04-20
> **cariboo907 said:**
> The missing paclkage, kdelibs4c2a, is still available for Natty, you can get it [here]("http://packages.ubuntu.com/search?keywords=kdelibs4c2a&searchon=names&suite=all&section=all"). I won't guarantee that it'll work though.

Cariboo,

Many thanks for this effort.
kdelibs4c2a depends on the package "kdelibs-data" (>= 4:3.5.10), and it seems Precise has the non compatible "kdelibs5". So, i also downloaded kdelibs-data from here: [http://packages.ubuntu.com/hardy/kdelibs-data](http://packages.ubuntu.com/hardy/kdelibs-data)

Gdebi said then that all dependencies of "kdelibs-data" were satisfied. So tried to install it, and unfortunately the process throws and error: "trying to overwrite '/usr/share/doc/kde/HTML/en/common/10.png', which is aldo in package kdelibs5-data 4:4.8.2-0ubuntu1 ".

If it does what i think it does, i guess it's not a very good idea to try to uninstall kdelibs5 from precise. =/

So... any suggestion?

Perhaps editing somehow the ktechlab or kdelibs4c2a in order to use kdelibs5? Is something like that possible? 

Thanks.

---

### Post by lordadi on 2012-04-20
Wonder if you can simply install KDE4 desktop and have Precise figure out the dependencies for you?

If so, that should satisfy KTechLab's dependencies as well :)

---

### Post by cariboo on 2012-04-20
> **Xelort said:**
> Cariboo,

Many thanks for this effort.
kdelibs4c2a depends on the package "kdelibs-data" (>= 4:3.5.10), and it seems Precise has the non compatible "kdelibs5". So, i also downloaded kdelibs-data from here: [http://packages.ubuntu.com/hardy/kdelibs-data](http://packages.ubuntu.com/hardy/kdelibs-data)

Gdebi said then that all dependencies of "kdelibs-data" were satisfied. So tried to install it, and unfortunately the process throws and error: "trying to overwrite '/usr/share/doc/kde/HTML/en/common/10.png', which is aldo in package kdelibs5-data 4:4.8.2-0ubuntu1 ".

If it does what i think it does, i guess it's not a very good idea to try to uninstall kdelibs5 from precise. =/

So... any suggestion?

Perhaps editing somehow the ktechlab or kdelibs4c2a in order to use kdelibs5? Is something like that possible? 

Thanks.

From the sourceforge page it looks like it hasn't been updated since 2011, I'd suggest you contact the author, and ask about updates.

---

### Post by Xelort on 2012-04-20
Hi lordadi.

Sounds fine, but only if i can have kde4 along with kde5. 
I've checked, and my precise has runtime packages already installed. However, i don't know what other "kde-XXXXXXX" package should i install: i understand that it should be enough with "kde-runtime" and "kdebase-runtime" (both 4:4.8.2-0ubuntu2) for the case. 
So, i guess this approach is somehow tricky and not really what i want to do here.


Cariboo,

I will contact then the software developers, and post here any information if i ever get some. 


Thanks.

---

