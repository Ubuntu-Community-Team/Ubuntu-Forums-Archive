---
title: "OSX Mavericks on Gazelle Pro"
date: 2013-11-15
forum: System76 Support
---

### Post by allcoms on 2013-11-15
Apologies if this is OT for the Ubuntu forums but this is the only forum for System76 laptop users that I'm aware of. If there is a more suitable place to discuss this, please tell me.

I'm hoping to get OSX installed on my Gazelle Pro. I've got most of the way already as I have Mavericks installed to my SSD, alongside Debian Jessie. The Mavericks installer works fine but after having installed it I'm unable to get past the bluetooth init (the BT works fine under 10.9 as I tested it during installation) and hence not as far as the desktop. However, there is a very good chance we can have Mavericks running full hardware support (except for Centrino wifi) as others have got Mavericks running very well, complete with QE/OpenGL accel, on similar Haswell laptops.

From what I've read, 10.8.5 is the oldest OSX that has Haswell support and hence our only other choice except 10.9 for running OSX natively. As far as I know, there are no 10.9-based OSX 'distros' yet and so any other Gazelle Pro users who want to go Hackintosh will be forced to do a 'vanilla install' like I have. Hackintosh installs are similar to or worse than installing Linux in the early/mid 90's - its really quite a painful and drawn-out experience and only for those who are really determined and/or enjoy messing with operating systems. The other probem with vanilla installs is that you need need an existing OSX install to create the USB installer.

In many ways I prefer Linux over OSX because Linux gives you more  options, its truly free and fully open source and I'm certain Linux is  the OS of the future but as it stands, OSX is a more popular desktop OS  because its a bit easier to use (when you run it on an real Mac,  anyway), it has actual standards and more pro desktop and multimedia  production software - certainly for people like myself who want to  record music.

To get Mavericks installed on my GazP, I mainly followed this guide:

[http://www.insanelymac.com/forum/topic/280756-guide-the-all-in-one-guide-to-vanilla-os-x-including-chameleon-dsdt-for-beginners-updated-for-mavericks/](http://www.insanelymac.com/forum/topic/280756-guide-the-all-in-one-guide-to-vanilla-os-x-including-chameleon-dsdt-for-beginners-updated-for-mavericks/)

However, in step 2.1.7, instead of extracting the mach_kernel from the OSX install image, I instead copied the kernel that is attached to the first post in the following thread, which is also proof that we have a good chance of getting Mavericks running on the GP:

[http://www.insanelymac.com/forum/topic/293503-haswell-early-reboot-mavericks-locked-msrs-and-hp-envy-15-j063cl-i7-4700mq/](http://www.insanelymac.com/forum/topic/293503-haswell-early-reboot-mavericks-locked-msrs-and-hp-envy-15-j063cl-i7-4700mq/)

In step 2.2.1 of the vanilla OSX install guide, I only copy the FakeSMC.kext and not the NullCPUPowerManagement.kext, as NullCPUPM is advised against within that second thread and in step 2.2.4 I saved the MacBookPro8,3 into /Extra on my installtion USB.

Note that the installer will install the original, unmodfied kernel to your HD so in step 3.1 you must also copy the Haswell-friendly kernel to your HD/SSD, overwiting the stock Apple one. With the modfied kernel in place, the installer runs without any special boot parameters so I don't know why I don't reach the desktop when installed to SSD.

Hopefully someone out there has had more success in this project than myself and can tell me what I'm missing or where I'm going wrong?

---

### Post by isantop on 2013-11-15
You're definitely on the wrong forum. ;-)

I would ask at the insanelymac forum.

---

### Post by coffeecat on 2013-11-15
Indeed. We don't support hackintosh here.

From the forum [Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules"): 

> We do not support circumventing TOS, EULA, etc here. 

*Thread closed.*

---

