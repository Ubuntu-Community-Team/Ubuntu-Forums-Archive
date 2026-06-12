---
title: "Manually turning off &quot;auto&quot; attribute of a network"
date: 2010-10-25
forum: System76 Support
---

### Post by Dave_L on 2010-10-25
Ubuntu 10.04.1, model star3

I posted this question in Networking & Wireless forum several days ago, since it didn't seem System76-specific, but haven't gotten an answer:

[http://ubuntuforums.org/showthread.php?t=1601633](http://ubuntuforums.org/showthread.php?t=1601633)

Any help is appreciated. :)

---

### Post by isantop on 2010-10-26
Instead of simply turning off auto, the better option may be to simply delete the connection. Right-click on the network manager icon in the panel, then click "Edit connections". Go to the Wireless tab, then select the network you don't want and click Delete. Repeat this for each network you don't want.

---

### Post by Dave_L on 2010-10-26
Thanks, I'll try that.

But won't the entries get recreated the next time the networks are detected?

I didn't create the entries, so I assume they were automatically detected.

---

### Post by thomasaaron on 2010-10-27
The entry may get re-created, but network manager shouldn't re-connect to it automatically. It will only do that once you've connected to it the first time. 

In other words, it sees everything, but automatically connects to the first available network that you've previously connected to.

---

### Post by Dave_L on 2010-10-27
Thanks, that seems reasonable.

I'm still curious why the Apply button is disabled.

---

