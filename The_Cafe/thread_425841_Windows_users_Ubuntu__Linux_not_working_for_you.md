---
title: "Windows users: Ubuntu / Linux not working for you?"
date: 2007-04-27
forum: The Cafe
---

### Post by Jhongy on 2007-04-27
For Windows users new to Linux (not just Ubuntu) facing instability or other problems, I'm willing to bet the problems are:

**1. Beryl / Compiz**

They're work in progress. Unfinished. Certain Beryl themes/settings are sure to crash your comp.

**2. Overclocking**

Overclocking is all the rage in Windows for power users. However, I've found Linux to be much less forgiving of bad memory than Windows. Bump down the overclock and work back up again; don't assume a stable overclock under Windows will be a stable overclock under Linux. This applies to overclocking anything from the multiplier, FSB to the PCI bus. If "bumping back down" solves problems, I'd recommend a re-install in case dat got currupted during installation.

**3. Bad memory**

Again, Linux appears to be much more sensitive to memory defects. It's worth testing your DIMMs with MemTest86.

**4. Install problems? Badly burned CD**

Lots of people comment on how the CD "never even installed" or "Never even booted up" for them on their computer.

I found this the first time I tried Ubuntu, Mandriva and RedHat. Re-burn the CD image on quality media at as slow a speed as you can. More often than not, a Linux distro burned at maximum speed will not even boot.

**5. Other unsupported software**

It's a windows disease -- surf the 'net and install the first piece of cool software you find. Try to use the Ubuntu repositories whenever possible, as they manage the package dependencies for you; and software you find is more likely to be of a higher quality level.

**6. Roundup of other problems:**

**Screen resolution wrong after new install.**

Install your graphics drivers! Just as you would do in Windows. The open source drivers shipped with Ubuntu are fine for some, but not for all resolutions or features. Search the forum if you need to know how to do this.

**X server crashes after an upgrade?**

Re-install your graphics drivers! They are dependent on the kernel version and won't work after an upgrade. To get back into your system, change the drivers back to the default drivers in your /etc/X11/xorg.conf file. For nvidia, for example, you'd change "nvidia" to "nv". Or search the forum!

**Everything requires command line work!**

No it doesn't! People just get used to the power of the command line. If you see a tutorial with lots of banging away at the command line,  ask for an equivalent in "point and click" -- chances are it will be fully or largely possible.

IMO, the above avenues should be explored before bashing Ubuntu, or any other distro for that matter.

---

### Post by hyperair on 2007-04-28
Good one with this post there. During my short time in ubuntuforums I found many people who begin Ubuntu bashing just because it doesn't work out of the box completely, claiming Windows to be better and whatnot. Hopefully there will be less of this happening.

---

### Post by aysiu on 2007-04-28
This seems more of a Cafe thread--I've moved it out of Testimonials and Experiences

---

### Post by Jhongy on 2007-04-28
Thanks! Maybe people can add any other "obvious" things they can think of to the thread?

---

### Post by reclusivemonkey on 2007-04-28
That's a good point about the overclocking.

Personally I have had my AMD Athlon overclocked by about a third since I put it in my machine, but I've never overclocked my memory. I worked for some time in a computer recycling centre and we only fried a couple of old machines experimenting =]

---

