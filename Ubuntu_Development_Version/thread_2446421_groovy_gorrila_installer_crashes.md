---
title: "groovy gorrila installer crashes"
date: 2020-06-30
forum: Ubuntu Development Version
---

### Post by dbergst on 2020-06-30
I just tried both of the available images on cdimage.ubuntu.com and  neither one makes it through installation without the installer  crashing.  If any of the developers are monitoring these forums, the  following images failed to install:

[http://cdimage.ubuntu.com/kubuntu/daily-live/20200628/](http://cdimage.ubuntu.com/kubuntu/daily-live/20200628/)
[http://cdimage.ubuntu.com/kubuntu/daily-live/20200629/](http://cdimage.ubuntu.com/kubuntu/daily-live/20200629/)

---

### Post by CelticWarrior on 2020-06-30
Please tell us where and how it crashes.

---

### Post by dbergst on 2020-06-30
THe installation at first appears to proceed normally, then after completing almost all the operations, a window pops up saying that the installer has crashed and that a bug report should be filed.  This issue occurs from both installation options, i.e., Install Kubuntu, or from the live environment running the installer there.

---

### Post by dbergst on 2020-06-30
I just confirmed the issue reported occurs with today's build, i.e:

[http://cdimage.ubuntu.com/kubuntu/daily-live/20200630/](http://cdimage.ubuntu.com/kubuntu/daily-live/20200630/)

---

### Post by acheronuk on 2020-07-01
Please provide a link to the reported bug. Thanks.

---

### Post by dbergst on 2020-07-01
> **acheronuk said:**
> Please provide a link to the reported bug. Thanks.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1885976](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1885976)

---

### Post by acheronuk on 2020-07-02
Ok. Looks like that is already known, not specific to the KDE front end, and a fix is in the works.

---

### Post by Chanath on 2020-07-02
The problem is more or less a month old. There are no dailies to be downloaded. Last Ubuntu Daily was on 9th June.

---

### Post by corradoventu on 2020-07-02
You may find a recent but not fully tested daily here: [http://cdimages.ubuntu.com/kubuntu/daily-live/pending/](http://cdimages.ubuntu.com/kubuntu/daily-live/pending/)

---

### Post by sudodus on 2020-07-04
It seems there are several severe bugs affecting Groovy Gorilly right now. See for example [Bug report #1886148](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148)

I notice that the cloned systems try to **boot via grub also in BIOS mode**. where we used to have syslinux. It will be interesting to see, if this means, that Canonical is launching a major revamp of the boot system for live drives, and that there will be some heavy lifting for the developers until our Ubuntu flavours boot in a smooth way again.

Maybe the live drives as we know the concept will be skipped in favour of cloned images of installed systems with or without RAM drives, for example something similar to what is used for Raspberry Pi or in Easy OS.

PS.
If you are a moderator, and want to move this post to an own thread, I'd be happy :-)
DS.

---

### Post by mc4man on 2020-07-05
If one were to choose safe mode at 1st dialog then likely the boot up would proceed as expected

---

### Post by sudodus on 2020-07-05
> **mc4man said:**
> If one were to choose safe mode at 1st dialog then likely the boot up would proceed as expected

Good idea, but no, it does not help me in this case. Please try in your computer with the current Groovy Gorilla.

---

### Post by dbergst on 2020-07-07
For those who wish to follow the current bug report, below is a link to it.

[https://bugs.launchpad.net/bugs/1885414](https://bugs.launchpad.net/bugs/1885414)

---

### Post by mc4man on 2020-07-07
> **sudodus said:**
> Good idea, but no, it does not help me in this case. Please try in your computer with the current Groovy Gorilla.

Works fine here, just tried again..

---

### Post by P-I H on 2020-07-08
Tested installation in VirtualBox of Ubuntu desktop amd64 version 20200707.1 in both BIOS and EFI mode. Both worked OK.

---

### Post by sudodus on 2020-07-08
> **mc4man said:**
> Works fine here, just tried again..

I have a set of computers of different age and quality (generation 2,3,4 Intel i3, i5 and i7 CPUs). Some of them are enterprise class laptops, but they are getting old . The newest computer, that I have access to is a consumer class [Lenovo laptop with generation 7 Intel i5](https://dustinweb.azureedge.net/media/494085/v130.pdf).

None of these computers boots from a USB drive cloned from a current groovy iso file. But I have VirtualBox in a Dell Precision M4800, and it boots and works well in a virtual machine where it is booted directly from the iso file seen as a virtual optical drive.

So I would really want to know how you manage to install Ubuntu Groovy. It is an installed system that works well. How did you install it?

- Did you use the current groovy iso file?
- What computer is it?
- How did you create the boot drive: Boot medium, method/tool to make it bootable?
- Did you use some special boot options or tweaks?

---

### Post by sudodus on 2020-07-08
> **P-I H said:**
> Tested installation in VirtualBox of Ubuntu desktop amd64 version 20200707.1 in both BIOS and EFI mode. Both worked OK.

Yes, it works in VirtualBox for me too. Please try to boot from a USB drive.

---

### Post by P-I H on 2020-07-08
Tested in BIOS mode on a computer with Nvidia GPU. Doesn't work. get an error message about /DEV/SR0 No media found.
Will test on another computer in EFI mode.

Doesn't work in EFI mode either. Error message "Unable to find a medium container a live file system"

The USB is made with mkusb, will make a copy with DD and try again.

Doesn't work. Same problem doesn't find the iso.

---

### Post by sudodus on 2020-07-08
It seems that most computers fail to boot USB drives made from these groovy iso files. But there are computers that can boot too. I know one case, a very new computer with a generation 10 Intel CPU.

I expect that the developers at Canonical will squash this bug, because a large part of the users have older computers (than those with generation 10 Intel CPU). I think all computers with Intel i3, i5 and i7 should work with Ubuntu or at least with the light-weight community flavours. I think also core2duo computers (and computers with AMD CPUs of similar specs) should be able to boot and run Ubuntu family flavours.

---

### Post by mc4man on 2020-07-08
> **sudodus said:**
> I have a set of computers of different age and quality (generation 2,3,4 Intel i3, i5 and i7 CPUs). Some of them are enterprise class laptops, but they are getting old . The newest computer, that I have access to is a consumer class [Lenovo laptop with generation 7 Intel i5](https://dustinweb.azureedge.net/media/494085/v130.pdf).

None of these computers boots from a USB drive cloned from a current groovy iso file. But I have VirtualBox in a Dell Precision M4800, and it boots and works well in a virtual machine where it is booted directly from the iso file seen as a virtual optical drive.

So I would really want to know how you manage to install Ubuntu Groovy. It is an installed system that works well. How did you install it?

- Did you use the current groovy iso file?
- What computer is it?
- How did you create the boot drive: Boot medium, method/tool to make it bootable?
- Did you use some special boot options or tweaks?

This is machine I stll use for Ubuntu - 
```
$ inxi -MCG
Machine:
  Type: Laptop System: LENOVO product: 20217 v: Lenovo IdeaPad Y510P 
  serial: <superuser/root required> 
  Mobo: LENOVO model: VIQY0Y1 v: 31900058STD 
  serial: <superuser/root required> UEFI: LENOVO v: 74CN44WW(V3.05) 
  date: 09/18/2013 
CPU:
  Topology: Quad Core model: Intel Core i7-4700MQ bits: 64 type: MT MCP 
  L2 cache: 6144 KiB 
  Speed: 2395 MHz min/max: 800/3400 MHz Core speeds (MHz): 1: 2397 2: 2395 
  3: 2395 4: 2400 5: 2396 6: 2396 7: 2395 8: 2402 
Graphics:
  Device-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915 
  v: kernel 
  Device-2: NVIDIA GK107M [GeForce GT 755M] driver: nouveau v: kernel 
  Device-3: Realtek Lenovo EasyCamera type: USB driver: uvcvideo 
  Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4600 (HSW GT2) 
  v: 4.5 Mesa 20.0.7 

```
Booted from live cd of 20.10 current, choose safe graphics (so I could boot to live session) > tlive session > install. 
Install works fine..

---

### Post by sudodus on 2020-07-09
@mc4man,

Thanks for these details :-)

- CPU: Quad Core model: Intel Core i7-4700MQ - This is close to my Dell Precision M4800, where I failed to boot.
- Booted from live [SIZE=3]**cd**[/SIZE] of 20.10 current - This makes a difference. I try from a **USB drive**, with the system cloned from the iso file.

[hr][/hr]
Since my previous post here, I tried with 'grub-n-iso' alias 'isoboot' according to [this link](https://help.ubuntu.com/community/Installation/iso2usb/isoboot)

This way I can make a bootable USB drive that boots

- both in UEFI and BIOS mode
- both live-only and persistent live

The method is to boot into a 'grub template' and then into an iso file. So this 'grub-n-iso' method works, but a cloned drive from the sane iso file fails (when tested in the same Dell Precision M4800 as used for the tests described above).

[hr][/hr]
This morning I notice that the developers have uploaded a new iso file with a fix for this bug, that i will test soon - I think and hope that it will squash the bug, because the intention is that a **cloned** USB drive should work :-)

---

### Post by sudodus on 2020-07-09
Cloned Groovy USB drives boot again, at least in some of my computers :-)

This is tested with the Lubuntu Groovy iso file '20200708.1'

```

$ md5sum groovy-desktop-amd64.iso
5ad5e3bfd76a06d371d6a00a4932daca  groovy-desktop-amd64.iso

```

**+** I tested in my Dell Precision M4800 and it works as usual in UEFI mode (and via grub) in BIOS mode.

**-** But the Lenovo V130 does not boot in UEFI mode and secure boot - When I select the USB drive from the temporary menu, it skips to the internal drive. This is a different failure mode compared to the previous iso files. (This computer is willing to boot from the grub-n-iso system of [comment #26 in the bug report #1886148](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148) and from cloned drives made from groovy iso files from June.)

[dustinweb.azureedge.net/media/494085/v130.pdf](https://dustinweb.azureedge.net/media/494085/v130.pdf)

**+** I tested in my Toshiba laptop, and it works as usual in UEFI mode with and without secure boot (and via grub) in BIOS.

[www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

**+** It works in a HP Probook 6450b with an Intel i5 M520 CPU, tested only in BIOS mode.

[hr][/hr]
It will be interesting to see, if other current bugs are affected by this bug-fix aimed at [Bug #1886148](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148).

---

### Post by P-I H on 2020-07-09
Made an USB boot disk with mkusb and tested the Groovy Ubuntu Desktop amd64 version 20200709.

Worked with MBR/BIOS mode on a desktop computer with an AMD Bulldozer CPU and Nvidia 1660 GPU. There were however some peculiar things
- Graphical artifacts during the installation. Perhaps "Safe graphics mode" is needed. 
- Had to power off after the installation to boot the computer
- At boot you get the message: BootOrder not found. Initializing default. Creating boot entry "Boot002" with label "ubuntu" for file \EFI\ubuntu\shimx64.efi

Worked as expected on a newer computer with Ryzen CPU and Radeon GPU.

---

### Post by mc4man on 2020-07-09
Trying the same usb (last current, not the current current) on a much newer laptop I have it boots up to live session with no issue.
So older fails unless safe graphics are chosen, newer doesn't. The fail is basically the can't find live media blah, blah.

So taking same usb on new machine, connecting a usb cd/dvd drive before booting, then that boot now fails with same can't find live media. My older laptop has a built-in cd/dvd drive, newer one does not have one.

Edit: the new current avail. today is even worse.
Takes a lot longer to fail.
Using safe graphics fails.
On machine where previous current worked it fails also.
So a step back..

---

### Post by sudodus on 2020-07-10
> **mc4man said:**
> Trying the same usb (last current, not the current current) on a much newer laptop I have it boots up to live session with no issue.
So older fails unless safe graphics are chosen, newer doesn't. The fail is basically the can't find live media blah, blah.

So taking same usb on new machine, connecting a usb cd/dvd drive before booting, then that boot now fails with same can't find live media. My older laptop has a built-in cd/dvd drive, newer one does not have one.

Edit: the new current avail. today is even worse.
Takes a lot longer to fail.
Using safe graphics fails.
On machine where previous current worked it fails also.
So a step back..

Please give feedback to the developer Michael Hudson-Doyle at [this bug report](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148). I think he needs all possible information of how the boot fails in various computers in order to find where to modify the code. (See for example comment #34 in the bug report.)

---

