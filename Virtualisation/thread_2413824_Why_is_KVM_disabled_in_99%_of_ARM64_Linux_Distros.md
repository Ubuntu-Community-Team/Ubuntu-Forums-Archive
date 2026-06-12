---
title: "Why is KVM disabled in 99% of ARM64 Linux Distros?"
date: 2019-03-02
forum: Virtualisation
---

### Post by gilius2 on 2019-03-02
Does anyone why KVM is disabled in all ARM64 Ubuntu releases and ports barring the vanilla Server install and developer builds!? This includes all ports of Ubuntu for the Raspberry Pi - official and unofficial.

Is there a way to enable it in raspi2-based kernels despite already compiled with the KVM kernel flags disabled?

Besides Ubuntu, does anyone know why this phenomenon is occurring across the entire ARM64 world of Linux distros? Are the various vendors purposely disabling it, or are they all working from the same kernel fork and some idiot working higher up thought it was a clever idea to disable virtualization? And I guess his (poor) excuse would be security?

---

### Post by DuckHook on 2019-03-02
It isn't necessary to jump to conclusions about nefarious intent or incompetence. It may simply be that the ARM port is new, riddled with bugs and not yet ready for prime time. When one considers that VMs are frequently used in mission-critical roles, one can appreciate why developers throughout the Linux-sphere might consider discretion the better part of valour.

Until recently, VM technology like KVM was foundationally dependent on x86 architecture: specifically, by way of Intel VTx or AMD-V. The ARM port is quite new. Such ports are in their infancy and hence may be nerfed because devs reasonably expect their distros to be reliable.

---

### Post by QIII on 2019-03-03
Please see [this.]("https://packages.ubuntu.com/search?suite=default&section=all&arch=arm64&keywords=libvirt&searchon=names")

---

### Post by gilius2 on 2019-03-03
> **QIII said:**
> Please see [this.]("https://packages.ubuntu.com/search?suite=default&section=all&arch=arm64&keywords=libvirt&searchon=names")
It's not primarily because of that - but because of this:

[ATTACH=CONFIG]282686[/ATTACH]

There are ARM64 KVM counterpart flags that have been deliberately turned off! Sackable offence - literally!

---

### Post by QIII on 2019-03-03
Which model of R Pi are you using and which release of Ubuntu?

---

### Post by gilius2 on 2019-03-03
> **QIII said:**
> Which model of R Pi are you using and which release of Ubuntu?
I've got 3B+, and there are various ports that are using the raspi2 kernel **ALL** **WITH KVM DISABLED:**
raspex-ubuntu-64bit-18.10-lxde-4400mb-181022.img
lubuntu-18.04.2-preinstalled-arm64+raspi3.img
disco-preinstalled-server-arm64+raspi3.img
ubuntu-18.04.1-preinstalled-server-armhf+raspi3-b-plus.img
xubuntu-18.04-desktop-arm64-raspi3-beta.7z
ubuntu-mate-18.04-desktop-arm64-raspi3-beta.7z

The only builds that have KVM enabled are not for the Raspberry Pi:
ubuntu-18.04.2-server-arm64.iso
ubuntu-18.10-server-arm64.iso

Somebody tried to get Disco Dingy to work based on a generic kernel with KVM, but the Ethernet doesn't work:
ubuntu-19.04-minimal-arm64-raspi3-alpha.img

---

### Post by QIII on 2019-03-03
OK.

What about ARM64 ports from other distros?

---

### Post by gilius2 on 2019-03-03
> **QIII said:**
> OK.

What about ARM64 ports from other distros?
All have KVM disabled. The only ones I know of that are enabled:
Gentoo
OpenSuse
ArchLinux

that's about it! Only Gentoo is easy to install. I think Debian had KVM enabled, but there was no working ethernet.

However, switch to AMD64, and KVM is enabled on everything.

---

### Post by 1clue on 2019-03-03
I thought arm64, for the most part, didn't support hardware virtualization features? In other words, you can do QEMU but not KVM.

---

### Post by gilius2 on 2019-03-03
> **1clue said:**
> I thought arm64, for the most part, didn't support hardware virtualization features? In other words, you can do QEMU but not KVM.
It sure does! See this guide for example:
[https://www.raspberrypi.org/forums/viewtopic.php?t=224057](https://www.raspberrypi.org/forums/viewtopic.php?t=224057)

Here's Windows 10 on ARM running at near-native speeds:
[ATTACH=CONFIG]282690[/ATTACH]

You could even run it on a Samsung S8:
[https://limboemulator.weebly.com/android-arm-kvm---kernels.html](https://limboemulator.weebly.com/android-arm-kvm---kernels.html)

Now this guy claims he can enable KVM, say, on ARM64 Ubuntu:
[https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=232796&p=1425121#p1424985](https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=232796&p=1425121#p1424985)

There's a few typos in his commands:
[COLOR=#2E8B57][FONT=Monaco]sudo make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu INSTALL_MOD_PATH=/mnt modules_install
=
[/FONT][/COLOR][COLOR=#2E8B57][FONT=Monaco]sudo make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- INSTALL_MOD_PATH=/mnt modules_install

[/FONT][/COLOR][COLOR=#2E8B57][FONT=Monaco]sudo cp -r modules/ /lib/modules/
=
[/FONT][/COLOR][COLOR=#2E8B57][FONT=Monaco]sudo cp -r modules/ /lib/

[/FONT][/COLOR]But I couldn't get it to work either way. Compiling the kernel didn't produce any .ko modules with a "kvm" prefix, so I think he might have left out some steps. Also, I'm not a dev, so it's not clear what concept he's using:
-upgrading the raspi2 kernel
-changing the raspi2 kernel
-adding a kernel alongside the raspi2 kernel

I wish I understood more about how the kernel works with the distro.

Does anyone else know an easy way to enable KVM in Ubuntu?

---

### Post by 1clue on 2019-03-04
I guess at this point I need to ask why someone would do that. I have a few pi's hanging around, and they're pretty much the minimum hardware I'd choose for any task even after I strip the GUI out. I could see setting up a headless Linux VM for grins just to say I did it, but I can't imagine Windows 10 on a pi even on the bare metal.

---

### Post by gilius2 on 2019-03-04
> **1clue said:**
> I guess at this point I need to ask why someone would do that. I have a few pi's hanging around, and they're pretty much the minimum hardware I'd choose for any task even after I strip the GUI out. I could see setting up a headless Linux VM for grins just to say I did it, but I can't imagine Windows 10 on a pi even on the bare metal.
You took it out of context. The whole point of using the Pi is simply for testing. The Samsung S8 represents more the practical application.

---

### Post by 1clue on 2019-03-04
I suppose testing another arm device, sure. In that case even if it's slower than the target platform for testing purposes, that's not a bad thing.

---

### Post by TheFu on 2019-04-20
> **gilius2 said:**
> It's not primarily because of that - but because of this:

[ATTACH=CONFIG]282686[/ATTACH]

There are ARM64 KVM counterpart flags that have been deliberately turned off! Sackable offence - literally!

In the olden days, we didn't have no fancy GUI to help set config options for our kernel builds.  We'd edit the makefiles for the options we wanted enabled and disabled.  Have you looked at the makefiles?  Bleeding edge stuff requires extra effort.  Feel thankful that partial solutions are possible.

---

