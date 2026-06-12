---
title: "PREVIEW: Hotplug time halved! Or better!"
date: 2004-12-16
forum: The Cafe
---

### Post by jdong on 2004-12-16
[http://sourceforge.net/forum/forum.php?forum_id=430876](http://sourceforge.net/forum/forum.php?forum_id=430876)

I backported Hoary's insanely fast Hotplug and grepmap.

> 
--A quick comparison on time to restart Hotplug-- 
Before Backport: 
 
real: 11.6s 
user: 6.64s 
sys: 0.51s 
 
After backport: 
real: 3.77s 
user: 1.22s 
sys: 0.51s 

The numbers speak for themselves!

As stated in the article, you have to update hotplug **and install grepmap** to get the benefits!

---

### Post by flibblesan on 2004-12-16
[QUOTE=jdong][http://sourceforge.net/forum/forum.php?forum_id=430876](http://sourceforge.net/forum/forum.php?forum_id=430876)

I backported Hoary's insanely fast Hotplug and grepmap.



The numbers speak for themselves!

As stated in the article, you have to update hotplug **and install grepmap** to get the benefits![/QUOTE]
 Whoah! I'm trying this out! My system tends to go slow at the hotplugging stage since I installed the Speedtouch stuff

---

### Post by flibblesan on 2004-12-16
Ok I've just upgraded hotplug and installed grepmap as you said. Now hotplug is RAPID. However one slight problem. Hotplug is so fast my ADSL modem doesn't have a chance to initialise in time before ubuntu tries to access the ntp server. Any was of removing the ntp update from the startup script?

Great work again jdong!

---

### Post by jdong on 2004-12-16
**rm /etc/rcS.d/S51ntpdate**

Better, do a similar symlink to rc2.d:
/etc/init.d/ntpdate -> /etc/rc2.d/S99ntpdate

This way, Ntpdate runs after GDM starts, so you can still get your time updated!

---

