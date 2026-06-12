---
title: "Broadcom Wireless drivers.. Maybe in intrepid?"
date: 2008-05-31
forum: The Cafe
---

### Post by Kosimo on 2008-05-31
Many new Broadcom devices don't work on Hardy in any way (not even using Proprietary Drivers option).. I found some how-to's but I couldn't spend time to do it with some friend's laptop's. 

Thing is, I fail converting some friend to Ubuntu due to the impossibility of setup Broadcom mini-pci devices. (It happen on three different machines) 

Question is.. Does anyone knows if this devices are going to work (out of the box) in future Ubuntu releases?

---

### Post by SunnyRabbiera on 2008-05-31
> **Kosimo said:**
> Many new Broadcom devices don't work on Hardy in any way (not even using Proprietary Drivers option).. I found some how-to's but I couldn't spend time to do it with some friend's laptop's. 

Thing is, I fail converting some friend to Ubuntu due to the impossibility of setup Broadcom mini-pci devices. (It happen on three different machines) 

Question is.. Does anyone knows if this devices are going to work (out of the box) in future Ubuntu releases?

Well remember the world we are dealing with, this wolrd is too microsoft owned for most of these companies to care.
Ubuntu is not at fault, its these companies who do not wish to co operate with it.

---

### Post by Kosimo on 2008-05-31
> **SunnyRabbiera said:**
> Well remember the world we are dealing with, this wolrd is too microsoft owned for most of these companies to care.
Ubuntu is not at fault, its these companies who do not wish to co operate with it.

Why Microsoft? Is broadcom a microsoft subsidiary? 

Does Broadcom make linux drivers for some other devices?  Because some of them works great in Ubuntu. (with a firmware upgrade).  Anyway, I'm still asking the same question. 
I presume that in future Ubuntu versions it'll be so easy to enable them, but I'm not sure about it. Because there are still lots of laptops that can't use this Broadcom device if not using terminal and many specific "tweaks"

---

### Post by Iandefor on 2008-05-31
> **Kosimo said:**
> Many new Broadcom devices don't work on Hardy in any way (not even using Proprietary Drivers option).. I found some how-to's but I couldn't spend time to do it with some friend's laptop's. 

Thing is, I fail converting some friend to Ubuntu due to the impossibility of setup Broadcom mini-pci devices. (It happen on three different machines) 

Question is.. Does anyone knows if this devices are going to work (out of the box) in future Ubuntu releases?My understanding is that, while there are drivers in the mainline kernel which should work for most Broadcom wireless chipsets, they need to load proprietary firmware to which Broadcom has the rights, and Broadcom doesn't allow for free redistribution of that firmware.

The best Ubuntu can do is to make it as painless as possible to download Broadcom's drivers, cut out the firmware, and install it.

---

### Post by tbroderick on 2008-05-31
> **Iandefor said:**
> 

The best Ubuntu can do is to make it as painless as possible to download Broadcom's drivers, cut out the firmware, and install it.

Ubuntu does that already. The problem is that the new b43 kernel driver doesn't work very well. Normally, the solution would be to use ndiswrapper and the Windows driver, but there is a problem with Hardy which prevents ndiswrapper form working without a little help. This thread should work, [HOWTO: Get Ndiswrapper working in Hardy Beta]("http://ubuntuforums.org/showthread.php?t=734003"). It did for me and many others. Hopefully this will be fixed in future releases.

Another solution is to install another distro. I'm using Mandriva 2008.1 and ndiswrapper works as it should. No extra configuring needed.

---

