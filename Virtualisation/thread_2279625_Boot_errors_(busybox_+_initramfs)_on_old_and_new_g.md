---
title: "Boot errors (busybox + initramfs) on old and new guest installations"
date: 2015-05-24
forum: Virtualisation
---

### Post by AussieGuy on 2015-05-24
I was running kubuntu 14.04 as a guest in VirtualBox, the host being Windows 7 Enterprise 64 bit.  I decided to upgrade last week (mainly to avoid constant messages telling me that  a "security update" was available for my system).  And afterwards, it didn't boot, I got the dreaded "ALERT!  /dev/disk/by-uuid/<long string> does not exist.  Dropping to a shell!" message.

On the advice of others, I devided to install a new system from scratch, which I just did this morning (upgrading VirtualBox first); I installed the guest additions, updated and upgraded as advised by the installation documentation - and guess what: the same old error again!  So it seems that upgrading, somehow, breaks the system.

Is there any way round this?  Or should I just remember to never ever ever enter "sudo apt-get upgrade" again?

Thanks,
-A.

---

