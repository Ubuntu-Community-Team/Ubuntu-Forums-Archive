---
title: "Live Session Vs Virtualization Vs Frugal Install"
date: 2011-04-26
forum: The Cafe
---

### Post by linuxyogi on 2011-04-26
Hi,

[B]Suppose you want to test a distro which of the following method will you

prefer the most & why ?[/B]

1) Live CD Mode

2) Installing it in any Virtualization tool (like VirtualBox)

3) Frugal Install

---

### Post by BrokenKingpin on 2011-04-26
I download the live CD first and have a go on one of my machines just to see if it recognizes my hardware properly. If it looks decent, I usually then go ahead and install it in VirtualBox to install my preferred applications and see if I can configure it to my liking. If that all works I will go for the install.

When a new Ubuntu release comes out I do a minimal install in VirtualBox, install XFCE and my apps from scratch on top of that. Once I get it all configured correctly I use remastersys to give me an ISO to install on all my other machines.

---

### Post by linuxyogi on 2011-04-26
> **BrokenKingpin said:**
> I download the live CD first and have a go on one of my machines just to see if it recognizes my hardware properly. If it looks decent, I usually then go ahead and install it in VirtualBox to install my preferred applications and see if I can configure it to my liking. If that all works I will go for the install.


I didn't understand one thing. Applications for example say Gimp, isn't Gimp the same irrespective of distribution ? It may differ a bit if there's a version difference.


> **BrokenKingpin said:**
> 

When a new Ubuntu release comes out I do a minimal install in  VirtualBox, install XFCE and my apps from scratch on top of that. Once I  get it all configured correctly I use remastersys to give me an ISO to  install on all my other machines.

[B]WOW !!!

[/B]Honestly**,** that is the most coolest thing I have heard in a long time.

Are those computers in a network ?

One of my friends was doing his MCSE and he once showed me a Remote Installation using Win Server 2003.

Is something similar available for the Linux platform ? Have you tried it ?

---

### Post by psusi on 2011-04-26
Definitely live cd.  Actually installing can be a bit painful as you shuffle around partitions and have to reboot.  A VM is still a little bit of a pain to setup and use, and doesn't quite provide a true experience, though I have been using it a bit lately because I have been testing so much and I got tired of rebooting.

---

### Post by linuxyogi on 2011-04-26
> **psusi said:**
>   A VM is still a little bit of a pain to setup and use, and doesn't quite provide a true experience

Yes, I agree and that's why I created this thread to know what you guys do.

---

### Post by snowpine on 2011-04-26
First I use Virtualbox. If the distro shows promise then I create a Live USB to test it on my actual hardware. If everything works great then I install. Sometimes if a distro is particularly awesome, I burn a Live CD for my archives so I can install it on other computers at a later date.

---

### Post by nothingspecial on 2011-04-26
I use another partition.

---

### Post by beew on 2011-04-26
> **linuxyogi said:**
> Hi,

[B]Suppose you want to test a distro which of the following method will you

prefer the most & why ?[/B]

1) Live CD Mode

2) Installing it in any Virtualization tool (like VirtualBox)

3) Frugal Install

None of the above, I would do a full install in an external hard drive. It is a full fledged real install (unlike a live usb with persistence, you can do system and kernel upgrade) but it is also portable in that you can plug it in different machines with totally different specs so you can test different hardware as well (provided you don't install proprietary graphic cards). You can also install proprietary graphic cards if there are machines you want to test with such, just remember to uninstall them when you boot from a machine with a different card (if you only want to test one machine of course this inconvenience doesn't arise)

A live cd is pretty useless, it is slow and you can't save any change. At a minimum you need a live usb with persistence.

---

### Post by Johnsie on 2011-04-26
+1 For live USB. I was given alot of free 1gb usb disks and they boot faster than the boot cd. I would never judge an OS by how well it performs as a VM because the VM uses fake hardware etc, so you dont get the real experience.

If you're interested in trying distros without having to download then I recommend visiting [http://susestudio.com](http://susestudio.com) or the Edubuntu site. Both of those sites have facilities for trying the OS in your browser. You wont get the same performance as on your machine, but it's still interesting.

---

### Post by linuxyogi on 2011-04-26
> **nothingspecial said:**
> I use another partition.

So, what OS is already installed on your PC ? Is it Windows or is it Linux ?

If it is Linux, does every other distro you install on the other partition successfully add a grub menu entry for your existing Linux OS ?


**Thanks to all for your replies.**

---

### Post by Old_Grey_Wolf on 2011-04-26
I use a VM to check out new features/functionality. However, VMs do not test compatibility with the actual hardware. Sometimes VMs will not allow checking out new features; such as, Unity. If I find the new features/functionality compelling enough I will install it on a test partition.

---

### Post by trollger on 2011-04-26
I have a 20 GIB partion set up just to try new linux distros. Its real easy(if you know how to manage a partion table) JUST MAKE SURE YOU DON'T INSTALL A BOOT LOADER. Once I install it to disk I go back to ubuntu update grub and restart the computer, so far I have had no broblems.

---

### Post by beew on 2011-04-26
> **trollger said:**
> I have a 20 GIB partion set up just to try new linux distros. Its real easy(if you know how to manage a partion table) JUST MAKE SURE YOU DON'T INSTALL A BOOT LOADER. Once I install it to disk I go back to ubuntu update grub and restart the computer, so far I have had no broblems.

Actually there is no option  of not installing a bootloader for Natty, instead you can choose to install it in the partition rather than the drive (so say Natty is in sda2, install the bootloader in sda2 instead of sda) that will allow the stable Linux (say mav in sda1) to retain control over grub.

---

### Post by beew on 2011-04-26
> **linuxyogi said:**
> So, what OS is already installed on your PC ? Is it Windows or is it Linux ?

If it is Linux, does every other distro you install on the other partition successfully add a grub menu entry for your existing Linux OS ?


**Thanks to all for your replies.**

If the already installed OS is Ubuntu (or any distro that use grub2) then you need to run "sudo update-grub" in its terminal after you add another Linux to the drive in  order for the new addition to show up in the boot menu.

Like I said, I test with installing into an external drive,--it gives the best performance as well as the identical operating environment to an internal install as it is every bit a real install, --but the idea is the same. 

I have 5 Linuxes installed in the external, with Maverick controlling grub (I have natty, two Fedoras and another distro on the same hard drive) For the others, I either didn't install a bootloader or if I had to (Natty), install it in the partition  where the OS (Natty) is instead of the drive (sdb12 instead of sdb) so that Mav retains control over grub. Everytime I add a new distro I have to log into maverick to run 'sudo update-grub".

---

### Post by nothingspecial on 2011-04-27
> **linuxyogi said:**
> So, what OS is already installed on your PC ? Is it Windows or is it Linux ?

If it is Linux, does every other distro you install on the other partition successfully add a grub menu entry for your existing Linux OS ?


**Thanks to all for your replies.**

I only have linux on all my systems. On my main rig I have two Ubuntus, at the moment 10.10 and 11.04, when I'm happy 11.04 is stable (probably never but that's a different issue) I'll put 11.10 alpha or beta over it. This is with a shared home.

On my laptop the other partition tends to have a different distro, Fedora with gnome 3 atm.

---

