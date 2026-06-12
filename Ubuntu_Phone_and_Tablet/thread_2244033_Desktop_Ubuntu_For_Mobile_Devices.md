---
title: "Desktop Ubuntu For Mobile Devices"
date: 2014-09-13
forum: Ubuntu Phone and Tablet
---

### Post by Sparrow40k1 on 2014-09-13
I am sure this is a very noob question..
But if possible, I want a very detailed answer, but:

Why can't Ubuntu (Desktop) be installed on any phone SD card and run how it does for a computer? [Ignoring the fact, that Unity would lag like crazy]
Now I know that there needs to be drivers, kernels, and on top of all that - The ARM architecture is completely different to Intel and AMD based CPUs but I have seen particular devices that have archived this. Such as the Nexus 7, with the Ubuntu installer.

Also; Is the Ubuntu (Such as the one on a Nexus 7), actually the normal Ubuntu just not an .ISO or is it a completely new thing AND will (and if so, how can) it run the normal software made for a desktop CPU (Intel, AMD)

I have ran Ubuntu 13.10 in this VM like setup on my phone with the "Complete Linux Installer" and then used "Android VNC" to view it and I am telling you this, because even as a VM thing.. LXDE environment performance was perfect !

---

### Post by 3rdalbum on 2014-09-13
> **Sparrow40k1 said:**
> I am sure this is a very noob question..
But if possible, I want a very detailed answer, but:

Why can't Ubuntu (Desktop) be installed on any phone SD card and run how it does for a computer? [Ignoring the fact, that Unity would lag like crazy]
Now I know that there needs to be drivers, kernels, and on top of all that - The ARM architecture is completely different to Intel and AMD based CPUs but I have seen particular devices that have archived this. Such as the Nexus 7, with the Ubuntu installer.

Desktop PCs are all built the same, compared to phones. Even between Android phones by the same manufacturer, the way they are flashed and they way they boot up is completely, completely different. ARM isn't backward compatible like x86, where software compiled for a 386 can run on an i7; the different versions of ARM CPUs can't run eachother's binaries.

You mention the Nexus 7. There are two models of Nexus 7: 2012 and 2013. Even though they are both made by Asus and only a year separates them, there are still massive differences.

Now think about Windows Phones versus Android phones - even bigger differences.

PCs are made to be able to run different operating systems. Phones are not.

> Also; Is the Ubuntu (Such as the one on a Nexus 7), actually the normal Ubuntu just not an .ISO or is it a completely new thing AND will (and if so, how can) it run the normal software made for a desktop CPU (Intel, AMD)

I don't understand what you mean by "not just an .ISO" or "normal Ubuntu". Tablet/phone Ubuntu won't run Ubuntu Desktop software, not yet at least, and it will never run x86 binaries unless your tablet has an x86 CPU (the Nexus 7 has ARM). Best case scenario: You might be able to recompile software for a specific ARM CPU.

> I have ran Ubuntu 13.10 in this VM like setup on my phone with the "Complete Linux Installer" and then used "Android VNC" to view it and I am telling you this, because even as a VM thing.. LXDE environment performance was perfect !

Great, but that's running on top of Android so it doesn't need to worry about drivers, flashing, compatibility with non-Android devices or a bootup sequence. Additionally, it doesn't run on all Android devices anyway.

---

### Post by Sparrow40k1 on 2014-09-13
There is a product I know, known as a Beaglebone Black (Basically an ARM PC). Many people install Ubuntu onto it - [Beaglebone Black with Ubuntu 12.04 ARM]("https://www.youtube.com/watch?v=R5XaJvJv4Is")
So, I 100% understand you. This Ubuntu is not the same Ubuntu as I run on my computer and software such as the Firefox is also not the same Firefox on my PC and will not run on my PC (and vise versa)?

---

### Post by grahammechanical on 2014-09-13
Ubuntu for Devices, what used to be called Ubuntu Touch, is built on the standard Ubuntu code base. So, Ubuntu Touch 0.5 was built on the Saucy Salamander (13.10) code base. Ubuntu Touch 1.0 was built on the Trusty Tahr (14.04) code base. And Ubuntu Touch 1.5 is being built on the Utopic Unicorn (14.10) code base.

The purpose from the beginning was to produce, first, an image that could be pre-installed on a mobile phone device by interested OEMs. Then, secondly, to produce an image that could be pre-installed on either a mobile phone device or a tablet device for interested OEMs.

There was never the intention to make Ubuntu for Devices available for download and installation on any and all mobile devices in the same way that we can download and install Ubuntu on laptops and desktop machines.

You also seem to be missing an important point. Ubuntu for phones and tablets is using Unity. The developers have designed a user interface (Unity 8) that scales to a mobile phone size screen when pre-installed on a mobile phone and also scales to a tablet size screen when pre-installed on a tablet device.  The phone core apps will be the tablet core apps and apps in the apps store will scale according to the screen size of the device that they are being installed on.

Another thing that you seem to be unaware of is that Unity 8 is basically a re-write of Unity 7 coded to run in Mir. Please provide information proving that the developers of LXDE are working on getting LXDE running on Mir and also converting it to be a suitable UI for a mobile phone or tablet.

By the release of Ubuntu desktop 16.04 Ubuntu will be running on Mir and using Unity 8. And it will have had the Ubuntu for devices code converged into to it. So, the phone/tablet core apps will be part of Ubuntu desktop UI. The apps in the app store will be available for installation on the desktop. And if the hardware could do it the laptop/desktop would also be a phone. 

All the "normal" software is in Ubuntu but unless the developers of applications like Libreoffice provide a UI for phones and a UI for tablets running those type of applications on a phone or even a tablet would be a very poor quality user experience. The file format of these kinds of applications is open source. So, we have an opportunity for community developers to write apps that will read and edit spreadsheets and word processor documents on phones and tablets.

Regards.

---

### Post by Sparrow40k1 on 2014-09-14
I wasn't asking about Ubuntu for Devices, that's why I kept saying Ubuntu Desktop.
But you've actually cleared up a lot I didn't know about Ubuntu for Devices - so, thank you.

---

