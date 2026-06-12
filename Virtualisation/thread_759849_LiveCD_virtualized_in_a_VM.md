---
title: "LiveCD virtualized in a VM"
date: 2008-04-19
forum: Virtualisation
---

### Post by DarkW0lf on 2008-04-19
Can I load an LiveCD (ISO file) in a VM (VBox or VMWare or whatever) instead of having to burn the image to a disc.

---

### Post by agurk on 2008-04-19
Yes, definitely.

---

### Post by funrider on 2008-04-19
cant do it with puppylinux...no luck so far

---

### Post by DarkW0lf on 2008-04-20
By the way I have VBox 1.5.6 not the OSE version.

agurk: How ? The only option I see is to use an ISO as the CD Drive for the Guest.
Unless I am reading that wrong that is not what I want to do. I want the CD ISO to be the Guest OS.

funrider: That's wierd virtualbox has a screenshot of doing just that.

---

### Post by agurk on 2008-04-22
DarkW0lf, I think you're just reading it wrong. Let's say you have a computer with Ubuntu and want to try out a PC-BSD live CD (iso). Fire up VBox and point to the iso file. PC-BSD will be loaded as guest.

---

### Post by DarkW0lf on 2008-04-26
That's true but you are showing the settings of a VM.
When I create that VM it still asks to create a virtual hard drive (vdi only).

What I am perhaps not understanding is the need for a vdi when LiveDistros don't use hard drive space by default (usually).

I will see how small of a vdi I can make (why not vmdk?)

-Edit-
I can only make a 4 MB vdi (no vmdk?)
I thought VBox supported both ?
I also have the innotek version (not OSE) and still don't have USB support

---

### Post by FredB on 2008-04-26
> **DarkW0lf said:**
> Can I load an LiveCD (ISO file) in a VM (VBox or VMWare or whatever) instead of having to burn the image to a disc.

Of course, you can test this way live cd versions.

---

### Post by agurk on 2008-04-26
> **DarkW0lf said:**
> When I create that VM it still asks to create a virtual hard drive (vdi only).
Ah, just select the <no hard disk> option when creating your VM:

---

### Post by agurk on 2008-04-26
> **DarkW0lf said:**
> I can only make a 4 MB vdi (no vmdk?)
I thought VBox supported both ?
Correct, VBox can use vmdk's but only create vdi's.

> **DarkW0lf said:**
> 
I also have the innotek version (not OSE) and still don't have USB support
Sorry, can't help you there.

---

