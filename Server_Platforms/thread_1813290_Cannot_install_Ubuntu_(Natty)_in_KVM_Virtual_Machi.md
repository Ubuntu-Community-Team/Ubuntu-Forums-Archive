---
title: "Cannot install Ubuntu (Natty) in KVM Virtual Machine"
date: 2011-07-27
forum: Server Platforms
---

### Post by ronzo on 2011-07-27
I've tried several times to create a Virtual Machine using KVM and installing Ubuntu Natty (using virt-manager).

The problem is that each CD Install ISO I've downoaded appears to be corrupt... but it only appears to be! When I choose 'check cd for defects' before I am trying to install, every time a different error is reported... so I fear that the virtual CD drive does not work properly. (I am using IDE with the default settings...)

Has anybody experienced similar problems? Can anyone point me to a hint or solution?

btw... I've installed Windows 7 as a VM the same way. I did not experience any problems so far...

Thanks a lot in advance for your input!

---

### Post by ajgreeny on 2011-07-27
How are you burning the CD; what application and at what speed?  If the .iso is OK according to the md5sum, maybe you're burning it to fast.  Try the slowest speed that you can with your hardware and whatever software you are using; it may help get a good CD.

EDIT:  Sorry, I see you are using KVM which I don't think, from your comments, uses a physical burned CD, so ignore my post if that is the case.

---

### Post by ronzo on 2011-07-28
Any ideas why I always get errors when performing an integrity check on the mounted CD ISO image? The ISO image has no errors, but they are reported when mounted using virt-manager...

---

