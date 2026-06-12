---
title: "Ubuntu Studio and Windows 7 Dual boot not working"
date: 2012-07-31
forum: Ubuntu Studio
---

### Post by Jacob Collstrup on 2012-07-31
Heya,

I want to try out Ubuntu studio, but I'm running into problems. I'm installing on my laptop. I installed Windows 7 as the first OS, after that was finished I installed Ubuntu Studio. But there is no boot menu! I don't get a choice for what OS to start. The laptop keeps starting up Windows 7. I tried re-installing Ubuntu but the same happened.

I'm a linux newbie. I can figure out the system as long as it works. So I hope some can help me figure this out. I DO have a gparted boot disc.

Best regards,

Jacob Collstrup

---

### Post by irv on 2012-07-31
It sounds like you didn't install the boot loader on the right partition. If you are booting Windows on sda1 and the MBR, your Master Boot for windows resides there you need to make sure grub is installed there. This way when you boot up the grub will come up giving you the option to boot into Ubuntu or Windows.

---

### Post by drmrgd on 2012-07-31
Just to help assess the situation, it might be helpful for you to load up a live session from the Ubuntu installation media you used (CD or USB or whatever), download Boot Info Script from the link below, and paste the output here using the Code tags.  That will help determine where you installed the bootloader, and how your system is configured.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Jacob Collstrup on 2012-07-31
Heya,

I sort of fixed it. I installed Bodhi linux too. So the laptop now has Windows 7, Ubuntu Studio AND Bodhi. The laptop is now booted in Ubuntu Studio.

I'm not sure if I'm satisfied with the solution, though. 

The laptop has two physical harddisks. Could that be the source of the problem? It's never been a problem those countless times it's been running Windows 7 and OpenSuse side by side.

Jacob

---

### Post by irv on 2012-07-31
> **Jacob Collstrup said:**
> Heya,

I sort of fixed it. I installed Bodhi linux too. So the laptop now has Windows 7, Ubuntu Studio AND Bodhi. The laptop is now booted in Ubuntu Studio.

I'm not sure if I'm satisfied with the solution, though. 

The laptop has two physical harddisks. Could that be the source of the problem? It's never been a problem those countless times it's been running Windows 7 and OpenSuse side by side.

Jacob
I shouldn't have been a problem, I still think it was the fact that the grub was installed in the wrong partition. By installing Bodhi linux it must have install the grub in the right place and saw all the OS's. I have Ubuntu Studio installed on an older laptop and using it to control a sound system. It boots a little slow, but once it up and running it does a good job.

---

### Post by Jacob Collstrup on 2012-07-31
I thought the installer would have handled that automatically.

I didn't consciously follow this guide, but it is what I did:
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

I remember selecting a "Install them side by side, choosing between them each startup"-esque option. I don't remeber its exact wording.

Jacob

---

### Post by drmrgd on 2012-07-31
Two hard drives are not a problem at all.  The key is to be sure that you've installed Grub into the correct partition, which is not selected by default necessarily (at least that's the case with Kubuntu 12.04).  I would agree with Irv that Bodhi probably by chance did install Grub to the correct partition, and that's why things are working. 

Again, if you run Bootinfo Script, you'll be able to see your partitions, where Grub is installed, and what it's pointing to.

---

### Post by irv on 2012-07-31
My guess what might of happen when installing Ubuntu was it was installed on the drive that didn't have the MBR and by default it installed the grub there so when it booted from the MBR, which was on the drive with Windows it would have just booted right into Windows. When installing Ubuntu it should have given you an option to install grub on the drive with MBR, (at that point you would not have taken the default) this way grub would have worked.

---

