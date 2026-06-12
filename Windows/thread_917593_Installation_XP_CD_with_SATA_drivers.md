---
title: "Installation XP CD with SATA drivers"
date: 2008-09-12
forum: Windows
---

### Post by daka on 2008-09-12
I have a Satellite L300, have erased Vista... unfortunately still need an adjacent Windows op sys for a little while.  Does anyone have the specific instructions on how to integrate XP Sata drivers into a copy of an XP installation disk?

Many thanks

Daka

---

### Post by iaculallad on 2008-09-12
> **daka said:**
> I have a Satellite L300, have erased Vista... unfortunately still need an adjacent Windows op sys for a little while.  Does anyone have the specific instructions on how to integrate XP Sata drivers into a copy of an XP installation disk?

Many thanks

Daka

Try posting your question on a windoze specific forum so you can get the reply you wanted. (This is not Ubuntu as marked in your thread title)

---

### Post by fiddledd on 2008-09-12
[Here](http://bancaldo.wordpress.com/2008/04/07/downgrade-vista-xp-how-to-integrate-sata-drivers-into-xp-iso/) is a guide.

---

### Post by forger on 2008-09-12
You're looking for [nliteos]("http://www.nliteos.com/")

---

### Post by jaqie on 2008-09-12
I came into this thread to tell you to find nLite, only to find it was already recommended. That is the best, easiest way to make a remastered (slipstreamed) XP install disc with your SATA drivers on it. I have done it myself for my own systems, I include my SATA and aftermarket PATA PCI card in it (one of my systems uses one for it's primary HDD) and they work perfectly.

nLite is what you want, just like the above poster said.

---

### Post by bigken on 2008-09-12
have you looked at your bios to see if you can change the hdd settings ?

---

### Post by jaqie on 2008-09-12
> **bigken said:**
> have you looked at your bios to see if you can change the hdd settings ?
BIOS HDD settings have ZERO effect on any SATA system I have ever worked with, when talking about XP install. XP install CD has *NO* sata drivers built into it, you have to use a textmode sata driver floppy if you do not modify the install CD to include SATA drivers.

---

### Post by bigken on 2008-09-12
> **jaqie said:**
> BIOS HDD settings have ZERO effect on any SATA system I have ever worked with, when talking about XP install. XP install CD has *NO* sata drivers built into it, you have to use a textmode sata driver floppy if you do not modify the install CD to include SATA drivers.


Well I beg to differ on older systems yes I agree on newer ones I have install xp without using the sata drivers by changing the bios settings

---

### Post by jaqie on 2008-09-12
With SP2 slipstreamed, I take it? Pre SP2 there were none, and most CDs (restore and install) are still pre SP2.

---

