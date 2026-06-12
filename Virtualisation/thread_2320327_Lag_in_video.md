---
title: "Lag in video"
date: 2016-04-12
forum: Virtualisation
---

### Post by ameya2 on 2016-04-12
Hello ,

I have installed Ubuntu on Virtual box and i see lag in watch videos on youtube ad VLC.

I have installed guest additions and my host os is windows 10.

I am not sure why there is a lag but need it fixed asap as I can't use the operating system.

Any help would be appreciated.

Thanks

---

### Post by QIII on 2016-04-12
Hello!

I have bad news.

You will never get very good video media performance from VirtualBox.  A guest OS does not communicate directly with your video hardware.  It relies on a hardware abstraction layer provided by the virtualization software.  The video capability provided by that hardware abstraction layer is not robust and performs poorly.

This is a limitation of VirtualBox.

---

### Post by ameya2 on 2016-04-12
Should we create a bug report with Virtualbox then ? That is very sad news indeed.

---

### Post by QIII on 2016-04-13
It is not a bug.  It is simply a limitation of the software -- one shared by many virtualization solutions.  More robust KVM (kernel-based virtual machine) virtualization will, under the right circumstances, allow video pass-through.  But those solutions are not as easy to use as things like VirtualBox.

---

### Post by SeijiSensei on 2016-04-13
Before giving up, see how much video memory you allocated to the VM.  Open the Virtualbox Manager, right-click on the machine listed in the left column, and pick Settings.  Then go to Display and push the slider for video memory all the way over to the right to its maximum value of 128 MB.  You can also try checking the 2D acceleration box and see whether that helps.  For video, 3D acceleration shouldn't matter.

---

### Post by ameya2 on 2016-04-14
Increasing video memory doesn't help, unfortunately...

If I try to enable 2D it says. 
The virtual machine is set up to use Video stream acceleration. As this feature only works with Windows guest systems it will be disabled.

Interesting update Guys ! I now ran SMPlayer and it plays video without any lag !! VLC has still lag. Youtube videos also has lag. I wonder why VLC has lag..

---

### Post by Bucky Ball on 2016-04-14
*Thread moved to **Virtualisation**.*

---

### Post by SeijiSensei on 2016-04-14
I prefer SMPlayer+mpv over any other player combination.  Have you tried using SMTube to watch YouTube?  It's an interface that lets you search YouTube and play the videos in SMPlayer. Maybe that will work better for you, too.

In my menus it's called "YouTube Browser for SMPlayer".

---

### Post by ameya2 on 2016-04-16
I installed that player but on left hand side it says tonvid.com so I cannot search for videos from youtube.com ?

---

### Post by ameya2 on 2016-04-16
Yeah much better with SMPlayer !! Thanks heaps for that :):)

---

### Post by ameya2 on 2016-04-16
If you can clarify why it says tonvid.com instead of youtube.com then that would be great !

---

