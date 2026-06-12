---
title: "How much ram do you allocate to XP"
date: 2009-05-04
forum: Virtualisation
---

### Post by GuiGuy on 2009-05-04
Hi,
I've been playing around with VirtualBox on 9.04. Hardware is high end AMD2, 4G RAM. I'm relatively new to this, so bear with me;

The [SATA drive access issues]("https://bugs.launchpad.net/bugs/119730") I am severely subjected to not withstanding, I am starting to coax some quite reasonable performance from WinXP. I have Vista Home virtualised as well, but, Vista is Vista. 

Anyway, I notice that allocating more RAM to the XP installation doesn't necessarily mean better performance. I thought that given 4G RAM, allocating 1G to XP would work. But I perceive better performance allocating about 620M. 

Comments?

---

### Post by clhsharky on 2009-05-04
I use 512MB on XP without problems in KVM.

---

### Post by jkarcz on 2009-05-04
I allocate 1G RAM for XP home in using virtualbox.  I have been running XP without a paging file to try an eek out as much performance as possible.  I also dial down all the fancy XP menu stuff too.  I only use one or two apps in XP so I haven't had the dreaded low mem error.  The only performance degradation I have noticed is when you do a save state.  1GB takes longer than 512MB.  SATA was a bit tricky, but did provide a noticeable improvement.

YMMV

---

### Post by javyn999 on 2009-05-04
I have 2 gigs ram, allocating 768 to my XP VBox.  Good idea on disabling the paging file in XP, I didn't even think of that.

---

### Post by GuiGuy on 2009-05-05
Thanks guys.

---

### Post by GuiGuy on 2009-05-05
> **jkarcz said:**
>  I have been running XP without a paging file to try an eek out as much performance as possible.

<cancelled>

Thanks

---

### Post by GuiGuy on 2009-05-05
> **javyn999 said:**
> Good idea on disabling the paging file in XP, I didn't even think of that.

Wow! Doesn't that seem to make difference!

Cheers

---

### Post by HermanAB on 2009-05-05
How much RAM depends on what the VM is supposed to do.  However, usually I find that 385MB is enough and 256MB is too little.

---

