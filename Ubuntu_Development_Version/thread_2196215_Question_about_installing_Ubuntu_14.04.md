---
title: "Question about installing Ubuntu 14.04"
date: 2013-12-28
forum: Ubuntu Development Version
---

### Post by spupazza on 2013-12-28
I'd like to install the daily image of ubuntu.
I have though some questions, about how will updates work.

On my machine I'd need to install nvidia proprietary drivers. Since currently the daily image is running 3.12.x kernel (and 3.13rc images do not seem anyway work with nvidia right now)
and within a month it'll switch to 3.13.x release, what will happen when I'll update?
1-Will I have to reinstall the nvidia drivers (and having black monitor in the meanwhile) or the update process will be painless?

2-Will, applications like vmware and virtualbox which are compiled against a specific kernel need to be reinstalled?

---

### Post by grahammechanical on 2013-12-28
If you go to System Settings>Software and Updates on the first tab (Ubuntu software) of the utility we can uncheck the box labelled  "Proprietary drivers for devices (restricted)." That may stop you getting updates to the Nvidia drivers. You can also at the grub menu select the Advance options for Ubuntu sub-menu and load an older kernel until any problem with 3.13 and Nvidia drivers is fixed. It is a work around that we sometimes have to use during the development cycle.

I have no idea about question 2. Guess it all depends upon how different 3.13 is from 3.12. We always expect breakage when using the development branch. If that is not acceptable then it would be better to wait until 14.04 is released.

Regards.

Regards.

---

### Post by spupazza on 2013-12-28
Thanks for the reply

---

### Post by deadflowr on 2013-12-28
It seems to be a recurring theme.
new kernel rc comes out and nvidia drivers don't work.
then they do, then newer kernel rc comes out and nvidia drivers don't work again.
I don't think the Ubuntu devs are going to update the kernel just to update the kernel, if a majority of users running nvidia end up with a broken system.
If you run the dev release as is, meaning without added ppas like x-edgers or kernel mainline, you should be fine.
Of course card to card nvidia drivers can be great one version broken the next, and so on.
Them's the breaks with dealing with closed-source software.

---

### Post by fjgaude on 2013-12-30
VirtualBox works just fine with 3.12 as it did with 3.11, at least it did for me. Just do whatever an error message says to do if things aren't automatic.

---

