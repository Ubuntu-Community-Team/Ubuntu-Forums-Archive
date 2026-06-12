---
title: "Terminal stalls on conversion"
date: 2009-10-25
forum: Ubuntu Christian Edition
---

### Post by cwatford on 2009-10-25
My terminal stalls when I input this line. 
```
*sudo[I] apt-key add - && wget -q [http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc](http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc) -O-*[/I]
```I'm fairly new to ubuntu/linux so I'm not sure what's happening. Am I doing something wrong?
It's the 32bit edition by the way.

---

### Post by amingv on 2009-10-25
Try this:

```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add -
```

Notice that I expanded the address to what I think it was, so you must correct it if it wasn't.

---

