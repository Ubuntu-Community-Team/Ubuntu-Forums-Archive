---
title: "Nvidia blue tint bug fix for Quantal"
date: 2012-05-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pt123 on 2012-05-16
Here is the bug : - 333 people affected by it (highest I have seen).
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/968489](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/968489)

in this askubuntu someone created a patch for vdpau
[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)

is it possible to have that patch in the ubuntu repositories for Quantal and Precise.

---

### Post by mc4man on 2012-06-15
The current libvdpau in 12.10 now has this patch
> libvdpau (0.4.1-6ubuntu1) quantal; urgency=low

  * Merge from Debian Unstable (LP: #1010920). Remaining Changes:
    - Drop gcc-multilib and ia32-libs-dev from build-dependencies
    - Drop lib32vdpau1 binary package from debian/control
    - Drop lib32vdpau1.{lintian-overriders,install,symbols,postinst} files
    - Comment out 32-ARCHS in debian/rules so multilib stuff isn't run
    - Mark Debian VCS links XS-Debian

libvdpau (0.4.1-6) unstable; urgency=low

  [ Maurizio Avogadro ]
  * Apply the wise patch supplied by Stephen Warren to fix Adobe Flash
    insanities.  (Closes: #668512)


---

### Post by pt123 on 2012-06-15
12.04 users can use ppa
sudo add-apt-repository ppa:tikhonov/misc
sudo apt-get update
sudo apt-get install libvdpau1

---

### Post by t1497f35 on 2012-06-15
> **pt123 said:**
> 12.04 users can use ppa
sudo add-apt-repository ppa:tikhonov/misc
sudo apt-get update
sudo apt-get install libvdpau1

I wonder, since it's not installed by default, does it mean that by default we don't have VDPAU functionality even if using proprietary nVidia drivers?

---

### Post by pt123 on 2012-06-15
no it fixes the vdpau library to handle the stupidness of the bug in Flash
this is the same fix in 12.10

---

### Post by emptythevoid on 2012-08-20
Thank you thank you thank you!

---

