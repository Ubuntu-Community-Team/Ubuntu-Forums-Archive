---
title: "Virtual Box Giving Me Trouble..."
date: 2012-05-17
forum: Virtualisation
---

### Post by Mazate on 2012-05-17
I'm running Vista on my machine and I'm trying to install Ubuntu on virtual box.  I can't get virtual box to install Ubuntu because I'm trying to install it from a USB drive.  Virtual Box just doesn't see it.  I've installed the extensions as well from VirtualBox's website but that hasn't helped.  I'm open to using any virtualization software out there.  Any suggestions that anyone may have would be most appreciated.

---

### Post by zach2825 on 2012-05-17
Quick question do you have virtualbox-ose and virtualbox-ose-guest-utils installed? Its the only way i can get the virtualbox to recognize usb

Another way could be to download the iso and mount it threw the options before you turn on the VM

---

### Post by Mazate on 2012-05-17
> **zach2825 said:**
> Quick question do you have virtualbox-ose and virtualbox-ose-guest-utils installed? Its the only way i can get the virtualbox to recognize usb

Another way could be to download the iso and mount it threw the options before you turn on the VM

No, haven't installed either one.  I'll try that and see what happens.

---

### Post by Vereinfachen on 2012-05-17
Don't listen to what zach2825 said, he didn't understand your question. The OP wants to install Ubuntu on his VirtualBox in Vista.

Mazate, why do you want to install Ubuntu from an USB Drive? You can directly mount the Ubuntu ISO in VirtualBox and run the installation without problems.
If you don't have the iso anymore then just download it from ubuntu.com. Then go to your Virtual Machine Preferences and under CD Drive mount the ISO ;)

---

### Post by Mazate on 2012-05-17
> **Vereinfachen said:**
> Don't listen to what zach2825 said, he didn't understand your question. The OP wants to install Ubuntu on his VirtualBox in Vista.

Mazate, why do you want to install Ubuntu from an USB Drive? You can directly mount the Ubuntu ISO in VirtualBox and run the installation without problems.
If you don't have the iso anymore then just download it from ubuntu.com. Then go to your Virtual Machine Preferences and under CD Drive mount the ISO ;)

Ok, that makes sense.  I'm such a noob.

---

### Post by zach2825 on 2012-05-17
> **Vereinfachen said:**
> Don't listen to what zach2825 said, he didn't understand your question. The OP wants to install Ubuntu on his VirtualBox in Vista.

Mazate, why do you want to install Ubuntu from an USB Drive? You can directly mount the Ubuntu ISO in VirtualBox and run the installation without problems.
If you don't have the iso anymore then just download it from ubuntu.com. Then go to your Virtual Machine Preferences and under CD Drive mount the ISO ;)
that was in the 2nd part of what i said way to repeat that..

---

### Post by Mazate on 2012-05-17
> **Vereinfachen said:**
> Don't listen to what zach2825 said, he didn't understand your question. The OP wants to install Ubuntu on his VirtualBox in Vista.

Mazate, why do you want to install Ubuntu from an USB Drive? You can directly mount the Ubuntu ISO in VirtualBox and run the installation without problems.
If you don't have the iso anymore then just download it from ubuntu.com. Then go to your Virtual Machine Preferences and under CD Drive mount the ISO ;)

Well, I think I'm gonna hang it up.  After finally being able to mount the iso on the virtual drive, I saw it start to load the iso and then I got one message that said that it was detecting my color settings at 24 bit and to go change them to 32 bit.  I found no such settings.  Then, I got a message saying that the linux kernel is for a 64-bit processor and its detecting a 32 bit processor and stopped there.  I have a dual core 64 bit processor so I think at this point I'm sticking with windows, unfortunately.

---

### Post by Vereinfachen on 2012-05-18
No! :KS
You have to enable virtualization extensions on your CPU and in VirtualBox.

Check this in your VirtualBox:
[http://gigapple.files.wordpress.com/2008/12/dsl-xmas-general-1.png](http://gigapple.files.wordpress.com/2008/12/dsl-xmas-general-1.png)

---

### Post by Mazate on 2012-05-18
> **Vereinfachen said:**
> No! :KS
You have to enable virtualization extensions on your CPU and in VirtualBox.

Check this in your VirtualBox:
[http://gigapple.files.wordpress.com/2008/12/dsl-xmas-general-1.png](http://gigapple.files.wordpress.com/2008/12/dsl-xmas-general-1.png)

How do I do it on my CPU?

---

### Post by QIII on 2012-05-18
Via your BIOS settings.

Also, in your initial set up, did you set up the machine as 64 bit?

Unfortunately, it is simply impossible with some motherboards to create a 64 bit virtualization environment.

---

