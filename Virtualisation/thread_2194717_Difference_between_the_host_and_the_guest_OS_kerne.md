---
title: "Difference between the host and the guest OS kernel versions"
date: 2013-12-20
forum: Virtualisation
---

### Post by praveensripati2 on 2013-12-20
I had installed Ubuntu 12.04 64-bit on my Laptop (host OS)  when it was released (around April, 2012) and after applying all the  patches (sudo apt-get update;sudo apt-get dist-upgrade), the version of  Linux kernel is
  uname -r
3.2.0-53-generic
  Recently I downloaded ubuntu-12.04.3-desktop-amd64.iso and used if  for installing a guest OS on top of VirtualBox, the default Linux kernel  is
  uname -r
3.8.0-29-generic
  And 3.8.0-34 is available on doing a dist-upgrade on the guest.


  Why is not the kernel version getting upgraded to 3.8.0-* on the host  OS even after a dist-upgrade? I am getting the rest of the upgrades  though.

Also, because of the kernel mismatch I am not able to install the VirtualBox guest additions.

---

### Post by tgalati4 on 2013-12-20
Because of the long term support nature of 12.04, newer kernels were backported.  There is a difference between 12.04 and 12.04.3.  So perhaps reinstall your host using 12.04.3 or use some instructions that are available on the web for upgrading the kernel.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

According to the release notes, 12.04.2 had a mechanism to automatically upgrade to 12.04.3.  So I presume you have to upgrade to 12.04.2 then reboot and continue to perform updates until you are at 12.04.3.  Pay attention to the section entitled: ** LTS Hardware Enablement Stack**

---

### Post by QIII on 2013-12-20
The developers decided that to get the 3.8.x kernel and the Hardware Enablement Stack for 12.04.2/3, users would have to manually and deliberately install them from 12.04/12.04.1.  If you haven't done that, your upgrades are going to keep the kernel at 3.2.x.  There are changes significant enough that there is this "Are you really sure?" step that dist-upgrade will not take on its own.

Have a look [here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") for more discussion.

---

