---
title: "Nvidia/Qemu"
date: 2016-11-18
forum: Virtualisation
---

### Post by T.J. on 2016-11-18
This is one of those very rare instances that I have to ask for help instead of offering it.  I have an interesting situation for which I have not found an answer,  I've been pondering this on my own for about two weeks. I have two Nvidia cards: a 960 and a 1060.  

When I install the nvidia driver 367.57 package, qemu with VGA passthrough to the 1060 locks  up and does not function. However, when I  manually install the exact same driver on 16.04; everything functions as it should.  I do not consider that a good solution for a number of reasons, especially since an official package causes a serious malfunction in another.

There is no change in the VM settings.  There is no change in the kernel  that would cause the issue.  16.04 uses the exact same kernel in both  cases and the exact same version of the nvidia driver is being used - so it is not a  kernel patch. 

It has to be something in the nvidia driver package, causing passthrough to fail and qemu  to lock up. 

For the life of me, I can't fathom what it is.  The VFIO device nodes  are present, and the card is properly bound - but it is acting like the  card is in a busy state unless I manually install the driver on 16.04. 

At this point, I can dig through the file-system looking for some minute  change or I can ask for help. 

Any thoughts?

---

