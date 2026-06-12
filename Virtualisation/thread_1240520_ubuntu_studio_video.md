---
title: "ubuntu studio video"
date: 2009-08-14
forum: Virtualisation
---

### Post by Jerry.S on 2009-08-14
I have installed virtualbox on a ubuntu9.04 host and have install ubuntu studio under vm. The problem that I am having is that ubuntustudio takes a long time to load and then the video is not working it is like the driver that eather VB or US is not working. I have been thinking about trying to load the additions after it has loaded but I can not logon to US so I just dont know what to do.

---

### Post by jocampo on 2009-08-14
> **Jerry.S said:**
> I have installed virtualbox on a ubuntu9.04 host and have install ubuntu studio under vm. The problem that I am having is that ubuntustudio takes a long time to load and then the video is not working it is like the driver that eather VB or US is not working. I have been thinking about trying to load the additions after it has loaded but I can not logon to US so I just dont know what to do.

Ubuntu Studio on VM? :-( not a good idea... 

I just tried that 1 or 2 months ago with low results. And the reason is that Ubuntu Studio kernel has been tweaked, so you can get most juice of your hardware; when running on a virtual machine, there is no real hardware and the RAM and virtualbox limitations make it Studio act kind of slow. Better if you dual boot, in my opinion.

That said ... why don't you reinstall and run upgrades and updates 1st. If I recall well, Studio does not install GUI by default. Try to run it 1st with nothing on it and do all kind of updates and upgrades via console. Once done, move to graphical interface.

---

