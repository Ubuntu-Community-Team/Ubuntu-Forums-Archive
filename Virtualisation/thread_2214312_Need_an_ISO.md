---
title: "Need an ISO?"
date: 2014-03-31
forum: Virtualisation
---

### Post by Lou_Kitz on 2014-03-31
I'm currently dual booting a Win 2008 server and Ubuntu 13.10 server 64bit.  I want to host the Win 2008 server virtually.  In trying to use the VM app available in 13.10 it wan't me to point to an ISO of the server software.  Is there another VM program that I can just point to the current install or is there a way in Ubuntu I can make an ISO of the current install?

Yes, I'm a noob.  I'm grateful for any links for reading or the names of apps worth learning to do the job.

---

### Post by Lou_Kitz on 2014-04-01
I know this is a noob question but all my google responses for making an ISO in Ubuntu returned results specific to making the install disk.  I have a third party imaging program on my Windows Desktop.  Is there an equivilant program I can install on Ubuntu to make an image file?  Will an image file of an installed OS work for KVM or do I need an ISO of the setup/install program?

---

### Post by sudodus on 2014-04-01
It is rather difficult to make an iso file, to remaster a linux system.

There are alternatives, if what you want is a complete backup image, so that you can clone your system to another drive. ***Clonezilla*** is a tool that can do that job, but it requires that the target drive is the same size or larger. The backup image, however, is a compressed file and can be much smaller (depending on how much of the source drive that is used).

---

### Post by sudodus on 2014-04-01
> **Lou_Kitz said:**
> I know this is a noob question but all my google responses for making an ISO in Ubuntu returned results specific to making the install disk.  I have a third party imaging program on my Windows Desktop.  Is there an equivilant program I can install on Ubuntu to make an image file?  Will an image file of an installed OS work for KVM or do I need an ISO of the setup/install program?

Yes, I have used image files (created by ***dd***), and mounted each of them to a device in the host computer, and it works in KVM. But the images must not be compressed, so if you make 'file.img.xz' you should expand it to 'file.img'.

---

### Post by JKyleOKC on 2014-04-01
> **Lou_Kitz said:**
> Is there another VM program that I can just point to the current install or is there a way in Ubuntu I can make an ISO of the current install?VirtualBox can be configured to use an existing HDD installation instead of a virtual disk, but don't expect any existing installation of any Windows product to work when you do this. All versions of Windows customize themselves during the initial installation, to match the hardware on which they are being installed, and the **virtual** hardware of any virtualization program will be sufficiently different from that **physical** hardware to prevent proper operation.

The only legal way to achieve what you're asking would be to obtain a legitimate Win 2008 Server setup disk, then create your blank virtual machine, set it to boot from CD, and use that setup disk to install a brand new copy of the server system.

You could use dd to copy the CD content to an ISO file, and connect that instead of the CD drive when creating the VM, and it would work the same way -- but there's no practical way to use your existing physical installation. Even the "slipstreaming" techniques you may find via a Google search require a valid setup disk as their starting point.

---

