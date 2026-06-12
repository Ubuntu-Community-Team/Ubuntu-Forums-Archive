---
title: "How to run Windows along with Ubuntu 12.04 LTS simultaneously"
date: 2013-04-17
forum: Virtualisation
---

### Post by cartaparagary on 2013-04-17
I recently installed UBUNTU to try it out, and I'm very comfortable with it, I've decided to work with it permanently.  However, there are some Windows programs I need for work that I haven't been able to install using WINE or any other alternative I've researched.  I would like to be able to run the current Windows OS it's already installed in my Hard Drive, in order to run the program using Windows, WHILE I'm working with UBUNTU.  Basically, I need to retrieve information from the Windows program, so I can create documents using Ubuntu.  I hope this can be done.  Help, anyone?

---

### Post by ibjsb4 on 2013-04-17
Could use VirtualBox.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by coldraven on 2013-04-17
I run Widows XP in Virtualbox with no problems. You can share data between both systems.
If you have install media with a serial number it is easy to do. 
Installing from a restore disc can be done but you need to create a script to fool Windows into activating.
As for cloning your existing installation, it may be possible but I don't know how.
Your hardware needs to support virtualisation and have sufficient memory. I have 4GB in my laptop.

---

### Post by heiko_s on 2013-04-18
You can mount your Windows NTFS partition under Ubuntu and open your documents using for example LibreOffice or OpenOffice (similar to guess what?). If it's only access to Microsoft Office documents, this could solve 95% - 100%.

VirtualBox is quite easy to set up, but making it work with an existing installation of Windows is a pain in the you know what.

If you run Windows 8, you could run Ubuntu on Hyper-V (I guess?). This is what Microsoft wants you to do and the reason they now "support" Linux with drivers (that allow to run Linux on Windows/Hyper-V).

I did the opposite and more: run Windows on Linux / Xen hypervisor with Windows having direct access to a dedicated graphics card for bare-metal performance (this is called VGA passthrough). This will only work with specific hardware features (VT-d / IOMMU) and is rather challenging to set up, but it gives you Linux and Windows running on the same computer at the same time, both with excellent bare-metal like performance. Data sharing can be over a Samba share, and since both communicate via a virtual bridge, data transfer speed is a non-issue.

Regarding performance: Virtualbox seems to improve but is still behind Xen and kvm. If graphics performance of the guest OS is important, for example gaming on a Windows guest, you got only two choices: Xen or kvm with VGA passthrough as mentioned above.

If you're new to Linux, try Virtualbox and reinstall Windows in a virtual machine. Or vice versa, use Windows as host and install Linux in either Virtualbox or Hyper-V.

---

