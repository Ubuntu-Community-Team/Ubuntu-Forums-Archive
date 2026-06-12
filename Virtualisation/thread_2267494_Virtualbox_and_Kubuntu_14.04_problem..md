---
title: "Virtualbox and Kubuntu 14.04 problem."
date: 2015-03-01
forum: Virtualisation
---

### Post by waloshin on 2015-03-01
I have installed Kubuntu and it will not boot stating " FATAL could not read from the boot medium" 

[IMG]http://i58.tinypic.com/2j61o8x.png[/IMG]

[IMG]http://i61.tinypic.com/107q1ck.png[/IMG]

---

### Post by JKyleOKC on 2015-03-04
It looks from the error message you posted as if the VM is failing to identify the drive. This could be due to having the wrong setting for controller type, or to not having the host system's BIOS properly configured to allow PXE operation. Do you have any other VM that operates properly?

---

### Post by SeijiSensei on 2015-03-04
Are you trying to boot from a device or from an ISO image?  I find the latter the simplest solution for VirtualBox.  Put the Kubuntu image somewhere VirtualBox can see it, then choose New from the VB manager and walk through the steps to create a new VM.  When the time comes to identify the boot device, simply point to the ISO image on your computer.  It will boot that and continue the installation.

---

