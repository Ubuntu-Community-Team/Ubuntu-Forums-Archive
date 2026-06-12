---
title: "Upgrading my distro now"
date: 2009-09-28
forum: The Cafe
---

### Post by ade234uk on 2009-09-28
Well I thought I would take the chance and just upgrade from 9.04 to 9.10 update-manager -d, hopefully this will resolve my sound issues. I'm missing sound on Ubuntu. 

When I tried the Alpha sound worked out of the box, I am hoping doing this It will achieve the same.

---

### Post by slakkie on 2009-09-28
Hope you backed up Jaunty in case Karmic breaks your setup.

---

### Post by ade234uk on 2009-09-28
Well luckily enough I got away with it. XServer crashed on me, so I booted with the other kernel, downgraded the Nvidia beta driver and now everything is ok, however I still have no sound. Will wait for final release because it worked on the Alpha Live CD.

OS feels a bit quicker too, but remember it's a bit of mash up at the moment, so hopefully will once I do a fresh install it should a lot quicker.

The new boot sequence looks very professional, and the new Ubuntu Software Center will be so easy for new people coming to Ubuntu. I know some people don't like it, but I found it helpful.

---

### Post by LowSky on 2009-09-28
sound not working can be a easy fix if you know what to look for.

what chipset do you have?

---

### Post by ade234uk on 2009-09-28
Its an intel chipset.

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller

---

### Post by LowSky on 2009-09-28
I thought so, follow these instructions
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by ade234uk on 2009-09-28
I will try that tommorow morning. Thank you very much. I will let you know how I get on.

---

