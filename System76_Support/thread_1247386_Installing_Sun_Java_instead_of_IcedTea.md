---
title: "Installing Sun Java instead of IcedTea"
date: 2009-08-22
forum: System76 Support
---

### Post by samalex on 2009-08-22
Hi,

I'm taking classes online that use BlackBoard, which is an online student information system.  The chat and message forum uses a java-based interface which isn't loading properly for me, and I've read that the IcedTea Java plugin that comes with Firefox through Ubuntu is sub-par and has lots of problems.  In hopes of troubleshooting this I'd like to install and use Sun's Java instead, but I'm not sure exactly how.  

Something else is that BlackBoard doesn't support Firefox 3.5 yet, and though I've tried installing Java Sun Plugin and Firefox 3.5 through Synaptic, it still shows IcedTea and Sun Java installed so I'm not sure which one is being used. 

Thanks for any advice on this.

Sam

---

### Post by gila_monster on 2009-08-22
Sam,

as it turns out, the sites I use won't work with IcedTea/OpenJDK. OpenJDK is not *quite* complete. They do work with Sun Java and its plugin, though. And when I installed Sun Java, it did not uninstall the other plugin, so I too was never sure what it was using.

Problem was that I couldn't remove the OpenJDK stuff without Synaptic also wanting to remove OpenOffice! Weird. So I just went into Tools/Add-ons and disabled IcedTea, and everything was fine.

---

### Post by jdb on 2009-08-23
> **gila_monster said:**
> Sam,

as it turns out, the sites I use won't work with IcedTea/OpenJDK. OpenJDK is not *quite* complete. They do work with Sun Java and its plugin, though. And when I installed Sun Java, it did not uninstall the other plugin, so I too was never sure what it was using.

Problem was that I couldn't remove the OpenJDK stuff without Synaptic also wanting to remove OpenOffice! Weird. So I just went into Tools/Add-ons and disabled IcedTea, and everything was fine.

OpenOffice requires hsqldb-java data base but runtime-java is an optional dependency to add features.
It will use either IcedTea or Sun runtime-java if it is available.
As to what gets used when you have multiples flavors installed, if you figure that one out let us know :)

IcedTea is only a dependency in the OpenOffice package Ubuntu provides.

jdb

---

### Post by SlugSlug on 2009-08-23
goto system > administration > software sources .  tick all the boxes in the first window save a close
open a terminal 
sudo apt-get update && sudo apt-get install sun-java5-jre

---

### Post by jdb on 2009-08-23
> **jdb said:**
> OpenOffice requires hsqldb-java data base but runtime-java is an optional dependency to add features.
It will use either IcedTea or Sun runtime-java if it is available.
As to what gets used when you have multiples flavors installed, if you figure that one out let us know :)

IcedTea is only a dependency in the OpenOffice package Ubuntu provides.

jdb

I did a little experimenting.
I installed OO & it pulled in IcedTea-jre6.
I tried to un-install IcedTea & it said it would also un-install OO, I cancelled.
I then installed sun-jre6.
After that it let me un-install IcedTea without un-installing OO.

I also noticied that if I installed sun-rte6 first, then installing OO did not pull IcedTea in.

jdb

---

### Post by samalex on 2009-08-23
Hi Everyone.

I actually followed the instructions on [this post]("http://ubuntuforums.org/showthread.php?t=1235730&highlight=sun+java&page=2") and it worked great. The post is down the page abit by leoquant, and after removing IcedTea and Hotspot Java through Synaptic and following these instructions I was rocking along.  Also a side note after all this I installed Flash 10 64-bit from Adobe and it worked as well, so bonus!

Sam

---

### Post by gila_monster on 2009-08-23
> **jdb said:**
> I did a little experimenting.
I installed OO & it pulled in IcedTea-jre6.
I tried to un-install IcedTea & it said it would also un-install OO, I cancelled.
I then installed sun-jre6.
After that it let me un-install IcedTea without un-installing OO.

I also noticied that if I installed sun-rte6 first, then installing OO did not pull IcedTea in.

jdb

Wow. Good to know, jdb. Thanks. Can clean up the system a bit now.

---

