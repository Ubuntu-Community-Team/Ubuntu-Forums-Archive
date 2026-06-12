---
title: "Is it worth submitting unity bugs on older hw?"
date: 2012-10-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by lykwydchykyn on 2012-10-15
My current "test system" for QQ is an old mitac laptop with intel 855 graphics and a pentium M processor.  Right now, Unity doesn't even run.

I've submitted some bugs, but I'm wondering if it's worth the trouble, or if I'm just making noise for hardware that they don't care about supporting.  Has there been any official statement about what hardware Unity will support?

---

### Post by philinux on 2012-10-15
See this.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by lykwydchykyn on 2012-10-15
> **philinux said:**
> See this.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

So, what you're suggesting is that if my system meets these requirements:
> 
1 700 MHz processor (about Intel Celeron or better)
2 512 MiB RAM (system memory)
3 5 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)
4 VGA capable of 1024x768 screen resolution
5 Either a CD/DVD drive or a USB port for the installer media
6 Internet access is helpful 


(and it does) 

...then I should continue reporting bugs?

---

### Post by kaldor on 2012-10-15
> **lykwydchykyn said:**
> So, what you're suggesting is that if my system meets these requirements:


(and it does) 

...then I should continue reporting bugs?

I'd say yes. If your hardware meets the requirements and doesn't work as expected, then I'd be reporting bugs :)

---

### Post by mc4man on 2012-10-15
The only way that hardware is going to run unity anymore is thru llvmpipe which possibly it's not.
(or is and unity isn't starting, you haven't much of a descrip other than 'unity doesn't run' 
I guess if you think it should 'qualify' for llvmpipe then that's one possible bug or if on llvmpipe & unity doesn't start another 
(assuming fully updated or using a very recent image

Odds are even if unity was starting up the experience would be disappointing

---

### Post by jerrylamos on 2012-10-15
The link on minimum requirements mentions Xubuntu, Ubuntu, or Kubuntu.  (ctually I prefer Lubuntu)

Ubuntu i.e. Unity is "all things for everyone all the time" so is most likely to "require the most hardware, most CPU cycles, most battery drain, most disk space, ..." Xubuntu and Lubuntu are noticeably more efficient than Unity if they will do the applications you want to run.  I'm not as familiar with Kubuntu's hardware requirements.

---

### Post by lykwydchykyn on 2012-10-15
> **mc4man said:**
> The only way that hardware is going to run unity anymore is thru llvmpipe which possibly it's not.
(or is and unity isn't starting, you haven't much of a descrip other than 'unity doesn't run' 
I guess if you think it should 'qualify' for llvmpipe then that's one possible bug or if on llvmpipe & unity doesn't start another 
(assuming fully updated or using a very recent image

Odds are even if unity was starting up the experience would be disappointing

Understand, I'm not asking for support in this thread, or filing a bug (I've already filed two on launchpad).  This is a throwaway machine that I merely test things with, I'm not concerned about finding a distro that will run on it.

My question is more whether or not the developers are interested in trying to make Unity work on this kind of hardware.  Seems to me, from looking over philinux's link, that either they need to support this hardware, or update the minimum requirements for "Ubuntu desktop" to something that will run unity.

FWIW Unity 2d *does* run on this hardware, though the performance isn't something I'd personally put up with.

If you're interested in the gory details, the bug is here: [https://bugs.launchpad.net/bugs/1067054](https://bugs.launchpad.net/bugs/1067054), but like I said, I'm not trying to get support here in the forum for this.

---

### Post by novafluxx on 2012-10-15
Are those system requirements for 12.04 as well? If you're running 12.10 those may not necessary apply any longer.

---

### Post by mc4man on 2012-10-16
Well your bug report needs some more info & as mentioned if compiz did/does crash then there should be a crash report (.crash) in /var/crash/.
If so then refile using that report (you can just r.click on the .crash > 'Open with Report a ...'
Even though if unity-2d was crappy then ATM unity/compiz in 12.10 wouldn't be worth using anyway, still no reason not to file on the crash

---

### Post by sammiev on 2012-10-16
> **jerrylamos said:**
> The link on minimum requirements mentions Xubuntu, Ubuntu, or Kubuntu.  (ctually I prefer Lubuntu)

Ubuntu i.e. Unity is "all things for everyone all the time" so is most likely to "require the most hardware, most CPU cycles, most battery drain, most disk space, ..." Xubuntu and Lubuntu are noticeably more efficient than Unity if they will do the applications you want to run.  I'm not as familiar with Kubuntu's hardware requirements.

You raise a few great points there. Test them from a CD/USB and choose the one that works with your hardware.

---

### Post by philinux on 2012-10-16
> **lykwydchykyn said:**
> So, what you're suggesting is that if my system meets these requirements:


(and it does) 

...then I should continue reporting bugs?

+1 correct. If they come back with "your hardware is too old etc etc" then they need to amend the minimum specs.

---

### Post by Stinger on 2012-10-16
> **kaldor said:**
> I'd say yes. If your hardware meets the requirements and doesn't work as expected, then I'd be reporting bugs :)
+1, your hardware seems to exceed the 'Recommended Minimum System Requirements'

Personally I don't think Unity and compiz has a 'Chinaman's chance' running through the llvmpipe on your hardware, and if that's the case, the requirements needs to be upped compared to other distro's like [Fedora]("http://docs.fedoraproject.org/en-US/Fedora/17/html/Release_Notes/sect-Release_Notes-Welcome_to_Fedora_17.html") and [openSuse]("http://en.opensuse.org/Hardware_requirements"). 
Lets hope that Ubuntu is not the leader in power consumption as some threads have indicated :rolleyes:
Cheers

---

### Post by josephmills on 2012-10-16
Yes you should file a bug.

---

