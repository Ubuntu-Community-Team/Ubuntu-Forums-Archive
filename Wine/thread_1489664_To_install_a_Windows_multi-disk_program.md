---
title: "To install a Windows multi-disk program"
date: 2010-05-21
forum: Wine
---

### Post by vaino on 2010-05-21
Hi
I need help to install a Windows program whose data are distributed on several cds.
Each one works correctly through  wine with the relative cd in its drive.
I would like to have all of them on my hard disk so that one can launch them with a single command. 
In this way one doesn't need to go thru the hassle of having to put each cd on the tray in succession, while still being able to access all data seamlessly in one go.
Thank you

---

### Post by cogadh on 2010-05-21
You could combine them all into a single disk image and try running the install from that, but that is not guaranteed to work at all. Some installer routines are pre-configured to look for multiple disks, so even if you put them all in one image, it is still going to ask you to swap the disks when it reaches a pre-determined point in the installation process. Also, sometimes the application data on all disks is set up with the same directory structure and file names , so you won't be able to combine the disks without over writing necessary files.

We could probably give you better advice with some more specifics, such as what application are you trying to install?

---

