---
title: "[SOLVED] Vurtual Box Question"
date: 2008-01-30
forum: Virtualisation
---

### Post by RadiationHazard on 2008-01-30
I'm trying to install ubuntu studios with virtual box. i'm running ubuntu gusty gibbon. what do i select? the only options are use entire disk. does virtual box not partition out a place for the operating system?

---

### Post by p_quarles on 2008-01-30
Thread moved to Virtualization.

Virtualbox creates virtual hard drives (.vdi files) for you. Prior to installing, you should have been given the option to create such a disk, using either a "dynamically expanding image" or a "fixed size image." 

Either way, though, rest assured that Virtualbox will not overwrite anything that's currently on your physical hard drive. It's not capable of doing that.

---

