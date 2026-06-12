---
title: "This kernel requires the following features not present on the CPU: 0:6"
date: 2009-03-11
forum: Virtualisation
---

### Post by Iwantu_ubuntu on 2009-03-11
I'm using VMWare server 2 on Ubuntu 8.10.  This on a Thinkpad T40 machine.  I want to test out Ubuntu Server 8.04 LTS as a Virtual Machine. The install goes smoothly and after the cd is ejected and the virtual machine reboots, I get the following error:

"this kernel requires the following features not present on the CPU: 0:6"

I searched around and couldn't find a fix for this. Apparently in Virtual Box this error is corrected by:

General -> Advanced -> check Enable PAE/NX

I couldn't find any such option in VMware Server 2.  

Can anyone help? I'm sure people have installed Ubuntu Server as a Virtual Machine in VMware Server succesfully right?

---

### Post by dcstar on 2009-03-18
> **Iwantu_ubuntu said:**
> I'm using VMWare server 2 on Ubuntu 8.10.  This on a Thinkpad T40 machine.  I want to test out Ubuntu Server 8.04 LTS as a Virtual Machine. The install goes smoothly and after the cd is ejected and the virtual machine reboots, I get the following error:

"this kernel requires the following features not present on the CPU: 0:6"

I searched around and couldn't find a fix for this. Apparently in Virtual Box this error is corrected by:

General -> Advanced -> check Enable PAE/NX

I couldn't find any such option in VMware Server 2.  

Can anyone help? I'm sure people have installed Ubuntu Server as a Virtual Machine in VMware Server succesfully right?

Are you installing 64 bit versions on a 32 bit host?

---

### Post by hftb on 2009-04-05
I too have a Thinkpad (T42) and I'm getting the same error.  I have Ubuntu 8.04 installed, and I'm trying to create a new VMWare image with VMWare 2.0.  The image I've created is Ubuntu 8.04 server, and it went through the install smoothly, but then when it rebooted, it gives the same error as you've described.

Did you manage to solve it?

Rob.

---

