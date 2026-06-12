---
title: "Install updates while installing"
date: 2013-11-03
forum: Server Platforms
---

### Post by edgyeft on 2013-11-03
Hi
I am installing Ubuntu Server 12.04.03 LTS.  To install updates after installing, I know I can run sudo apt-get update && sudo apt-get upgrade and then reboot to install kernel updates, but is there any way to do this all during installation and save the install/reboot afterwards?

Thanks

---

### Post by ian-weisser on 2013-11-03
Yes, but I don't find it worthwhile.

Essentially, you must customize (update) the install packages. The time involved to do all that package work is much greater than the time savings on the install(s).

A much simpler method for mass installs is to use a preseed file and one-time shell script that handles the initial update.

Another simpler method is to install from the mini iso. Only a little duplication - most of the downloaded system packages will be the updated versions.

There is also a great benefit to knowing that the installed system is functioning before updating/customizing. Just browse the forums to see all the "install failed" and "update failed" threads. In the rare event you get a failure, knowing which type of failure you are troubleshooting can save a lot of time.

---

### Post by SeijiSensei on 2013-11-04
If you are installing from an image file, you can tell the installer to download the updates along the way.  The easiest way to do this is to boot the image and choose "Try Ubuntu".  Then use the network manager to connect the system to the Internet.  Double-click the installation icon on the desktop, check the box to install updates (and restricted-extras if you want), and you'll have the most up-to-date packages when it completes.

---

