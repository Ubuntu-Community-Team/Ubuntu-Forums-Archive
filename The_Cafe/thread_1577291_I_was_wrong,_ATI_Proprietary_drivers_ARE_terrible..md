---
title: "I was wrong, ATI Proprietary drivers ARE terrible."
date: 2010-09-18
forum: The Cafe
---

### Post by Brent0 on 2010-09-18
Today I installed 10.04 on my computer. After everything was all done, I rebooted and then installed all updates. After updating, I installed the latest Catalyst Control Center, 10.9. After a quick reboot, I've been having a lot of problems. Compiz doesn't work, my graphics card is constantly HOT, I can't scroll through pages without it jumping, Youtube doesn't work right, I got a Kernel Panic when I booted up, and many others. The open source driver was okay except for compositing not working. 
I only had problems with Youtube with older versions of the driver.
It's like they're going in the wrong direction! :mad:

In the past, I have said there is nothing wrong with the drivers and that it was just rumors or from bad experiences in the past. Well community, you were right. :P
I don't regret choosing an ATI card though. It is still a great bang-for-the-buck compared to similarly priced Nvidia cards. Plus, most of my 3D programs are in Windows.

And on a side note, does anyone know how to get rid of the proprietary driver and go back to the open source driver?

---

### Post by Lucradia on 2010-09-18
I have a 5750, and it doesn't even allow ubuntu to show graphics to my monitor. How does yours work, and mine doesn't? Oh right, the kernel doesn't support my graphics card yet, but wait, yours is newer.

See this thread, if you don't know what I mean: [http://ubuntuforums.org/showthread.php?t=1566487](http://ubuntuforums.org/showthread.php?t=1566487)

---

### Post by Brent0 on 2010-09-18
> **Lucradia said:**
> I have a 5750, and it doesn't even allow ubuntu to show graphics to my monitor. How does yours work, and mine doesn't? Oh right, the kernel doesn't support my graphics card yet, but wait, yours is newer.

See this thread, if you don't know what I mean: [http://ubuntuforums.org/showthread.php?t=1566487](http://ubuntuforums.org/showthread.php?t=1566487)

Hmm your problem is very strange. The kernel in 10.04 should support the 5750. It may be a BIOS issue.

---

### Post by Lucradia on 2010-09-18
> **Brent0 said:**
> Hmm your problem is very strange. The kernel in 10.04 should support the 5750. It may be a BIOS issue.

No CrossFire, as Fedora 13 boots fine. No matter what I set for graphics in the BIOS, ubuntu fails to boot. Switching to and from pnp doesn't work either.

---

### Post by Legendary_Bibo on 2010-09-18
Hey I'm not the only one! Yeah I had tried the Catalyst 10.7 I believe to see if I could fix the issues of a flickering cairo-dock. It would make my laptop overheat for no reason, and then my fonts would start corrupting. All I did was follow ATI's instructions to uninstall it (well it took 3 tries before it actually worked) Then I installed the FGLRX graphics drivers and a week later there was a fix for cairo dock that fixed the flickering. Well it flickers at boot up, but after it flickers enough times it stops. Oh and playing UT2K4 with the catalyst drivers made my graphics card go 1.5 times the max temperature it should have run at. With the FLRX, I get the same performance and it stay about 30-40 degrees Celsius below its max.

---

### Post by Lucradia on 2010-09-19
And btw, I forgot to answer your "removal of propietary driver..."

Search for **fglrx_uninstall.sh**

---

