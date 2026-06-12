---
title: "Wireless AWOL on Lenovo T60."
date: 2010-08-06
forum: Ubuntu Studio
---

### Post by casbahdk on 2010-08-06
I am trying to setup my Lenovo T60 laptop for my daughter with Ubuntu Studio (Lucid). When I boot with an Ubuntu Lucid CD, the wireless card works out of the box, but I have been unable to get this to work with the Ubuntu Studio install.

```
sudo lshw -c network
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
```

Is the above enough of a clue to get this to work?

---

### Post by cchhrriiss121212 on 2010-08-07
See this:
[http://ubuntuforums.org/showthread.php?t=1525705]("http://ubuntuforums.org/showthread.php?t=1525705")

---

### Post by casbahdk on 2010-08-07
> **cchhrriiss121212 said:**
> See this:
[http://ubuntuforums.org/showthread.php?t=1525705]("http://ubuntuforums.org/showthread.php?t=1525705")

Cheers. You got me on the right track. I couldn't get Network Manager to find networks, despite my wireless light turning on. So, I purged as much of Network Manager as I could (there is one depend that threatens to uninstall Ubuntu Studio, so I left that). I then installed wicd and everything seems to be working OK. I am not sure whether this will help me avoid the latency issues that were the basis for the decision to not enable wireless networking, but I am at least satisfied that I have the wireless networking functioning.

---

