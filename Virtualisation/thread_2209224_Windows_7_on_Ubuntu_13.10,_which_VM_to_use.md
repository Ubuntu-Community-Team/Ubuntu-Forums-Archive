---
title: "Windows 7 on Ubuntu 13.10, which VM to use?"
date: 2014-03-04
forum: Virtualisation
---

### Post by jdallara on 2014-03-04
Hello,
  After looking at web pages for several hours, I'm still no closer to an answer, so I'm asking here.  I want to run Windows 7 on my desktop that is running Ubuntu 13.10.  I've looked at VirtualBox, Xen with XAPI, VMWare, and Qemu-KVM.  Qemu is the only one who actually shows how to install and configure Windows, albeit XP.  Unfortunately, Qemu says that it is not good at running Wndows.  The other three state they can run Windows but don't give much information as to how to install and configure it.  Any suggestions?

Thanks in advance,

Jon.

---

### Post by ajgreeny on 2014-03-04
I am running WinXP in VirtualBox PUEL version direct from Oracle with total success, except that it seems so slow compared with Xubuntu.

I installed using the XP install DVD in the normal way other than it was using a small virtual disk (WinXP.vdi) that I made at the start of the install.  I know XP is probably very different from Win7, but I presume the installation procedure will be the same.

---

### Post by Simon_WM on 2014-03-05
> **ajgreeny said:**
> I am running WinXP in VirtualBox PUEL version direct from Oracle with total success, except that it seems so slow compared with Xubuntu.

I installed using the XP install DVD in the normal way other than it was using a small virtual disk (WinXP.vdi) that I made at the start of the install.  I know XP is probably very different from Win7, but I presume the installation procedure will be the same.

+1

I would go with VirtualBox and create a Windows 7 VM, and install the VirtualBox Guest Tools, and the VirtualBox Additional Tools - So you can get USB mount support.
Did this for a year or so when I used Ubuntu, and worked very well.

---

### Post by blightedagent on 2014-03-06
> **Simon_WM said:**
> +1

I would go with VirtualBox and create a Windows 7 VM, and install the VirtualBox Guest Tools, and the VirtualBox Additional Tools - So you can get USB mount support.
Did this for a year or so when I used Ubuntu, and worked very well.

I'm attempting this right now but i can't get the additional packages installed for usb support. I'm downloading from here [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)   but when I try to install I get this message:  

Failed to install the Extension Pack /tmp/Oracle_VM_VirtualBox_Extension_Pack-4.2.20-90983-1.vbox-extpack.

VBoxExtPackRegister returned VERR_VERSION_MISMATCH, pReg=00000000 ErrInfo='VirtualBox version mismatch - expected 4.2 got 4.1'.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ExtPackManager
Interface: IExtPackManager {3295e6ce-b051-47b2-9514-2c588bfe7554}

---

### Post by jdallara on 2014-03-07
Thank you for the input.  I'll give VitualBox a try.

Thanks,

Jon.

---

### Post by Simon_WM on 2014-03-09
> **blightedagent said:**
> I'm attempting this right now but i can't get the additional packages installed for usb support. I'm downloading from here [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)   but when I try to install I get this message:  

Failed to install the Extension Pack /tmp/Oracle_VM_VirtualBox_Extension_Pack-4.2.20-90983-1.vbox-extpack.

VBoxExtPackRegister returned VERR_VERSION_MISMATCH, pReg=00000000 ErrInfo='VirtualBox version mismatch - expected 4.2 got 4.1'.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ExtPackManager
Interface: IExtPackManager {3295e6ce-b051-47b2-9514-2c588bfe7554}

From the error message, it looks like you downloaded the older verison for the EXT Pack

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) - Latest Virtual Box for Linux 

Latest Download for EXT download.virtualbox.org/virtualbox/4.3.8/Oracle_VM_VirtualBox_Extension_Pack-4.3.8-92456.vbox-extpack

---

