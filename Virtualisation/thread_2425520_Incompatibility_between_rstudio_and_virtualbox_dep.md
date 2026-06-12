---
title: "Incompatibility between rstudio and virtualbox dependencies"
date: 2019-08-26
forum: Virtualisation
---

### Post by firthu on 2019-08-26
Rstudio files (.R, .Rmd, etc) do not open from nautilus (or console xdg...) , or, Rstudio does not open at all with segmentation fault. dmesg error:
traps: rstudio[16450] general protection fault ip:7f9f343a6a99 sp:7fffe73b6190 error:0 in libQt5XcbQpa.so.5.9.5[7f9f3434a000+fb000]

After removing libqt5core5a
sudo apt-get remove libqt5core5a


Which also unistalls:
  libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5
  libqt5printsupport5 libqt5svg5 libqt5widgets5 libqt5x11extras5
  qt5-gtk-platformtheme virtualbox-qt

The nautilus opening problem or segmentation fault disappears.

If I reinstall 

sudo apt-get install libqt5core5a

Rstudio coutinues working well. 

I installed several versions of virtualbox, and each one breaks the functionally of Rstudio. Anyone having the last Rstudio and virtualbox working?

---

### Post by SeijiSensei on 2019-08-26
Are you running Ubuntu and RStudio in a VirtualBox VM?  Or are you running it on the host machine?

Have you tried installing Kubuntu in a VM instead of vanilla Ubuntu? Kubuntu uses KDE which is built on Qt.  It might have fewer problems.

Also, I suggest installing the version of VirtualBox in the Oracle repositories. It always works flawlessly for me. 

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by TheFu on 2019-08-26
Would you consider not using virtualbox?  There are other options.

---

### Post by firthu on 2019-08-26
@seijisensei They are not running in a virtualbox. Problem happens with the latest version in the virtualbox page also.

---

### Post by firthu on 2019-08-26
@theFu, problem is I have already created a virtualdisk in virtualbox and would like to use again. Should I quit virtualbox?

---

### Post by TheFu on 2019-08-26
> **firthu said:**
> @theFu, problem is I have already created a virtualdisk in virtualbox and would like to use again. Should I quit virtualbox?

Just offering an alternative.  Moving to a different hypervisor might be easy or it might need a fresh install or anything in-between. Just depends on the VM setup and the OS involved.

---

### Post by SeijiSensei on 2019-08-27
> **firthu said:**
> @seijisensei They are not running in a virtualbox. Problem happens with the latest version in the virtualbox page also.

So if you uninstall VirtualBox, the problem disappears?

Again I suggest installing Kubuntu in a VM, and see if that's any better.

---

### Post by slickymaster on 2019-08-27
Thread moved to **Virtualisation** for a better fit.

---

### Post by firthu on 2019-08-28
@seijisensei,  I am not talking about guests. problem is in host ubuntu 18 with rstudio and virtualbox. uninstalling virtualbox problem disappears yes.

---

### Post by SeijiSensei on 2019-08-28
I'm running Kubuntu 19.04 with both RStudio and the Oracle version of VirtualBox installed.  I don't have these issues.

---

### Post by firthu on 2019-09-17
I unistalled virtualbox, but the happiness didn't last. At some point I installed something using qt5 and problem reappeared.

---

### Post by firthu on 2019-09-22
I got the segmentation fault again. I decided to install 19.04. I can open Rstudio now.

---

