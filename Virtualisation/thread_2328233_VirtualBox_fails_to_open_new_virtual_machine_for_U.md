---
title: "VirtualBox fails to open new virtual machine for Ubuntu 14.04 i386"
date: 2016-06-19
forum: Virtualisation
---

### Post by Robert_Gaines on 2016-06-19
I created a new VirtualBox virtual machine for Ubuntu 14.04, but it can't start. The virtual machine was just creating and does not yet have any operating system installed. This is the error:

Failed to open a session for the virtual machine Ubuntu 14.04 i386.

The device helper structure version has changed.

If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox. (VERR_PDM_DEVHLPR3_VERSION_MISMATCH).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}

I am running Ubuntu 15.10 amd64 desktop.

---

### Post by jeremy31 on 2016-06-19
*Thread moved to **Virtualisation**.*

---

### Post by SeijiSensei on 2016-06-19
Might I suggest uninstalling the Virtualbox version you have now and installing the version in Oracle's repository using the method described here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

I have always found this the most reliable source for VirtualBox, and by adding the Oracle repo, VB will be upgraded automatically just like all the other software on your system.

You should also know that 15.10 will reach its [end of life next month]("https://wiki.ubuntu.com/Releases").  I'd go with an LTS version, either 14.04 or 16.04.

---

