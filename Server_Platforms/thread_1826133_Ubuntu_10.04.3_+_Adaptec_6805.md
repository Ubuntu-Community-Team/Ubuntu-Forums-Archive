---
title: "Ubuntu 10.04.3 + Adaptec 6805"
date: 2011-08-16
forum: Server Platforms
---

### Post by dkwolf on 2011-08-16
Hey there smart ppl :)

I just got my new Adaptec 6805 controller today. Set it up with the drivers from Adaptec.com and running fine. 
Then i did a apt-get update and upgrade... big mistake, now its upgraded to 10.04.3 (from the 10.04.1-server base intall) and it seems that this breaks the Adaptec driver. Now how to i get it back to working order?

It fails under boot with "Gave up waiting for root device" and i get a Buzybox boot menu. I did read up abit on how to get it to work under 10.04.2 but well i may need abit help on that, since that guide has been written from a fresh install.

---

### Post by disabledaccount on 2011-08-16
You may want to add kernel boot option: rootdelay=60 (seconds to wait before trying to mount root, 60 should be sufficient)

---

### Post by dkwolf on 2011-08-16
> **tomazzi said:**
> You may want to add kernel boot option: rootdelay=60 (seconds to wait before trying to mount root, 60 should be sufficient)

hmm i think its the module for my 6805 that has gone missing in action.. Can't access /boot/ when its in busybox menu. So i am kinda screwed.
So don't think that rootdelay would help that much. So now i am stuck trying to figure out what i do next.

---

### Post by disabledaccount on 2011-08-16
If You are in busybox then it can be problem f.e. with initramfs, not necessarily with the GRUB itself.
Can You tell what is returned by >ls, >lsmod and >set ?

---

### Post by dkwolf on 2011-08-16
ah got it back up running by booting into a rescue system and copying the files over again (aacraid.ko and initrd.img-2.6.32-24-server) using this guide [http://ubuntuforums.org/showthread.php?t=1788356](http://ubuntuforums.org/showthread.php?t=1788356).
But the question is... should i still be worried or should everything be fine now? The server states that its running 10.04.3 LTS now with kernel 2.6.32-24-server.

Don't think i am gonna do a kernel update over the next few days, at least not until Adaptec sends out a new driver.

---

### Post by Entilza on 2011-08-20
Now that 10.04.3 is out my driver's in the above thread are useless but can still be used if you download 10.04.2.

You cannot ever do kernel upgrades with the ubuntu package manager at the moment with your 6805 driver.  Because you custom installed it with the initial install to that initial kernel.

The only way you can do this is by first getting the kernel source then patching the kernel with the new adaptec driver.

The new adaptec driver is part of kernel 2.6.39+ I Believe.  However I doubt 10.04 will ever move up so many kernels.  Maybe slowly.

I'm not sure if ubuntu will merge this driver into the 10.04 kernel series, how is this requested?

---

