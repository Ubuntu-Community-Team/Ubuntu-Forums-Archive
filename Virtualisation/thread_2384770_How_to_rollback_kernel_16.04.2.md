---
title: "How to rollback kernel 16.04.2?"
date: 2018-02-11
forum: Virtualisation
---

### Post by mongo42 on 2018-02-11
Hi all,

I am faced with a kernel update problem, in that the latest kernel broke VMWare Workstation 12 (Ubuntu 16.04 host).  After upgrading from kernel version 4.10 to 4.13, VMWare would no longer compile.  My VMs are critical, so I regressed back to 4.10 via the grub menu, and turned updates off (as a cybersecurity practitioner, this is less than ideal).  So, I am stuck at 4.10, and am afraid to update anything else for fear of getting a new version of something that depends on the newer kernels (and breaking them since I do not have the newer kernel).  After some research, I found out about the HWE kernels (unique to Ubuntu?), and that the generic kernel is still at version 4.4.  Below is an exercise I did in an Ubuntu VM (started at kernel 4.8, and updated to kernel 4.13), and I want to double-check with the Ubuntu gurus (I am an Ubuntu newbe;  I am doing well if I successfully grep something).

First, I pulled the 4.4 generic kernel in via the following command (from a post from user Bashing-om):

sudo apt install --install-recommends linux-generic xserver-xorg-core xserver-xorg xserver-xorg-video-all xserver-xorg-input-all libwayland-egl1-mesa

Second, I rebooted to the 4.4 kernel via the grub menu, and executed everything I could think of (everything seemed to work fine).

Third, I removed the 4.13 and 4.8 kernels using Synaptic Package Manger, as well as anything related to HWE (I used the search function)

Fourth, I rebooted to kernel 4.4, and all seemed to be well.

Fifth, I have absolutely no clue (beyond clean, autoclean, and autoremove) what else needs to be cleaned up

(deep breath)....

OK, now that I am back to version 4.4, here is my confusion:

1) Am I off of the HWE track, meaning that the Ubuntu software upgrade application will only "see" the 4.4 upgrades, and not pull me back to 4.13?  What flags Ubuntu that I am no longer on the HWE track (a config file, etc)?

2) What about other updates (browser, etc)?  Is it possible that some updates might be HWE-specific and that, in the absense of HWE, an update would break those applications?  Is Ubuntu smart enough to see that HWE is not present and just give me the appropriate updates?

3) What else needs to be cleaned off?

Thanks!

---

### Post by wildmanne39 on 2018-02-11
*Thread moved to **Virtualisation, a more appropriate forum**.*

---

### Post by cruzer001 on 2018-02-12
If you ran a search in Synaptic on "hwe", then you should of caught everything HWE related.  Autoremove is also good at catching leftover packages.  So yes, you should be good.

linux-headers-generic
and
linux-image-generic

Also go with the 4.4 kernel.  Have you installed them?

Your thread title is all wrong.  16.04.2 refers to the Ubuntu version (which still has HWE) and not the kernel you seek.  16.04.1 was the last version with the 4.4 kernel installed.  18.04 and 18.04.1 (when they come out) well also have the kernel with long term support.  Then the rest will have HWE.

---

