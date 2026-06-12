---
title: "Installing a fresh Ubuntu from within Ubuntu on the same machine?"
date: 2012-02-26
forum: Server Platforms
---

### Post by TheForumTroll on 2012-02-26
Anyone know a good guide to install Ubuntu from within Ubuntu, removing the old install along the way - without using any CD's, floppys or USB sticks?

This is a headless server, so doing it via SSH would be the ultimate solution, but monitor and keyboard is available if needed.

---

### Post by sudodus on 2012-02-26
I think you want to install it on the same computer (so it is not installing to another computer via the network).

Do you want to upgrade to a new version, or do you want to clear Ubuntu and make a fresh install of the same version?

---

### Post by enjoijesus94 on 2012-02-26
Depends On Wat You Wanna Do :lolflag:

---

### Post by TheForumTroll on 2012-02-26
Seriously did you read my post? It answers your questions :D 

Well, as I said I want to install a fresh Ubuntu from within a current install of Ubuntu, removing the old install along the way. So yes, on the same machine and no, not an upgrade. Like a format, install, but with a constant connection to the computer as there is no way to start from fresh from a dics ):P

---

### Post by sudodus on 2012-02-26
> **TheForumTroll said:**
> Seriously did you read my post? It answers your questions :) 

Well, as I said I want to install a fresh Ubuntu from within a current install of Ubuntu, removing the old install along the way. So yes, on the same machine ):P
If you don't want to use a CD or USB stick, I suggest

- either from a flash card (for example an SD card) ;-)

- or directly from an iso file in another partition on the HDD,
see this link [[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11227153&postcount=349_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11227153&postcount=349")

I know no way to do what you want directly from an installed Ubuntu. But the software is there so it should be possible. But why?

---

### Post by TheForumTroll on 2012-02-26
Because the server doesn't have any CD drive, floppy drive or flash card readers and I have had no luck getting it to boot from a USB stick.

What are the alternatives? If I format the hard-drives there is no way to boot it up except going and taking the system apart.

---

### Post by sudodus on 2012-02-26
1. Maybe you can borrow or buy an external CD drive (via USB),

2. or if you have an old internal CD, get a USB to IDE and SATA cable set, which can be used to connect CDs as well as HDDs to any computer with USB ports,

3. [COLOR="Red"]or let's hope that some experienced linux user will read this thread and come with a solution using your system on your internal HDD[/COLOR].

Such a cable set can be useful many times, when you need to work with HDDs as well as CDs or DVDs. Recently I made a persistent boot HDD drive from an old IDE HDD, that works well when booting via my USB to IDE and SATA cable set.

---

