---
title: "How do I use external disk drive with virtualbox?"
date: 2010-01-11
forum: Virtualisation
---

### Post by wildmanne39 on 2010-01-11
Hi, everyone, can anyone tell me how to set up an external hard disk to be used to boot suse linux as guest on my ubuntu system? Thanks to everyone in advance,all help is greatly appreciated.

---

### Post by HermanAB on 2010-01-12
Howdy,

The free version of Virtualbox doesn't support USB, so that is your first problem.

---

### Post by mkvnmtr on 2010-01-12
As the other poster said you will need to download the latest Sun version. Uninstall the OSE version if it is installed and install the new version. You will have support for USB devices. While you are on the Sun site download the manual and you will be all set. Any questions after you have installed someone will be glad to answer.

---

### Post by wildmanne39 on 2010-01-12
Hi, I am using ,the version that allows usb support, I just cant get it to install suse linux on the usb disk drive I am having trouble after I enter the path for it to set up the disk drive it will not save for use with the usb disk drive. I had permission problems, I fixed them I think but that might still be what is keeping me from writing to the disk, I can see it and view files but I can not set it as the boot disk for my linux guest. Thank you for your help anymore help is appreciated, I have 2 ubuntu books I have been reading them but they dont cover virtualbox. I have been using virtuabox for a year know with windows guest and but I have never been able to set the guest up on the usb disk.
> **mkvnmtr said:**
> As the other poster said you will need to download the latest Sun version. Uninstall the OSE version if it is installed and install the new version. You will have support for USB devices. While you are on the Sun site download the manual and you will be all set. Any questions after you have installed someone will be glad to answer.

---

### Post by mkvnmtr on 2010-01-12
OK in system you have the boot order. You can set the ck to be first. Then you go to storage and add a cd. Then you click on the cd and to the far right there is a file to click on. It opens a window where you can add a cd device. You can search for the hard drive and have it be the cd. This will depend on having enabled it under usb devices and added the filter. That should get you booting from the drive. You might need grub on the drive but. I must say I havent tried this. Could you not just mount the iso o your computer  drive. That is the way i do all of mine. If it is not a ISO I believe there is an app to make it one.

---

