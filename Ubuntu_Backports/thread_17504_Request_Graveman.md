---
title: "Request: Graveman"
date: 2005-02-28
forum: Ubuntu Backports
---

### Post by punkrockguy318 on 2005-02-28
A warty backport of graveman would be very helpful:  We would actually have a GTK2 CD Burning application for warty!  Could this be backported please?

---

### Post by rufius on 2005-02-28
[QUOTE=punkrockguy318]A warty backport of graveman would be very helpful:  We would actually have a GTK2 CD Burning application for warty!  Could this be backported please?[/QUOTE]
 I'll look into it tomorrow night.

---

### Post by landotter on 2005-03-01
With the right dependencies installed via synaptic, the newest Mandrake Cooker rpm for Graveman installed and worked flawlessly on my warty box using alien:

sudo alien -i gravemanxxx.rpm

Warning: don't try to upgrade vital system bits and bobs with alien, but proggies like this should be harmless.

There's also Gnomebaker and Mr. Burns. The newest Gnomebaker is pretty nice too. :D

[http://rpm.pbone.net/index.php3/stat/4/idpl/1693809/com/graveman-0.3.8-1mdk.i586.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1693809/com/graveman-0.3.8-1mdk.i586.rpm.html)

---

### Post by joede on 2005-03-01
I've done a backport and I must say, that gnomebaker is the better choose. There are several drawbacks in graveman. Just have look at the bug reports.

[http://savannah.nongnu.org/bugs/?group=graveman](http://savannah.nongnu.org/bugs/?group=graveman)

---

### Post by Jad on 2005-03-01
whats wrong with Nautilus burner?
I didn't have any trouble with it till now

---

### Post by landotter on 2005-03-01
[QUOTE=Jad]whats wrong with Nautilus burner?
I didn't have any trouble with it till now[/QUOTE]


Nothing at all wrong with Nautilus, just doesn't do audio CDs, copying, blanking, etc. Works great for data CDs though--I just wish it would add up the total MB used when you're dragging files into the burner window.

---

### Post by landotter on 2005-03-01
[QUOTE=Jad]whats wrong with Nautilus burner?
I didn't have any trouble with it till now[/QUOTE]


Nothing at all wrong with Nautilus, just doesn't do audio CDs, copying, blanking, etc. Works great for data CDs though--I just wish it would add up the total MB used when you're dragging files into the burner window.

---

