---
title: "Yep, Si + Cik gcn1+2 Help"
date: 2021-04-15
forum: Ubuntu Development Version
---

### Post by genukie on 2021-04-15
Ok so.. it's my 2nd day on a non windows based o/s 
System specs are 
```
MSI GX60

Device [0] Neptune 8970m /m290x Sea islander // Pitcairn                    0000:01:00.0
amdgpu

Device [1] igpu 8670G Southern islander // Richland                             0000:00:01.0
radeon

```

i cant get amdgpu to work 
Right now it wont even list the 8970m on device info. Just lists 2 x 8650G for openGL / 3D Acceleration


Thus far, running 5.11.14 linux kernel with drm_amdgpu=m, radeon config=Y slapped grub with amdgpu.modeset=1 which kernel ignored as jibberish.
did the modprobe.conf radeon si+cik=0 amd si+cik=1 

Anyways here dmesg of the onbly 2 errors i've got left

I feel like the firmwares are mixed up and not sure how to correct it, as the 8650G is normally device ID 0 and the the discrete 1

But i learnt alot today, getting used to terminal commands and memorising the useful tools. This is like cmd on steroids.
```

[    6.268766] BUG: unable to handle page fault for address: ffff9f12702030cf 
[    6.268816] #PF: supervisor read access in kernel mode 
[    6.268846] #PF: error_code(0x0000) - not-present page
 


[    6.086879] kfd kfd: PITCAIRN  not supported in kfd 
[    6.254986] ACPI BIOS Error (bug): AE_AML_BUFFER_LIMIT, Field [TEMP] at bit offset/length 491520/32768 exceeds size of target Buffer (512000 bits) (20201113/dsopcode-198) 




[    6.255107] ACPI Error: Aborting method \_SB.PCI0.VGA.ATRM due to previous error (AE_AML_BUFFER_LIMIT) (20201113/psparse-529)
 
```

Any feed back would be appreciated, pretty cool how you can break the crap out of the distro and still find a way to get terminal access and setup a network to literally do a reinstall but with kde plasma, wayland and unity DE's available as a back up login. Don't mind me, i feel like im having another moment with tech, when i discovered android from being an iphone user.

---

### Post by grahammechanical on 2021-04-18
I am glad you are having fun. Personally, I do not understand your thread title. Neither do I understand why you have installed Ubuntu 21.04 which is still under development and is not yet released. And whose support life is limited. Expect breakage.

Your hardware is old. Dating back to Windows 8 days. That is according to the MSI web site. Apart from the thrill of testing a development release some of us might install the development release in the hope that the Linux kernel in the development release might, just might, support the latest hardware that we have purchased. This is not necessary for older hardware.

When you installed Ubuntu did you tick the box to install non-free, third party proprietary software? That action would have caused a proprietary video driver to be installed. If we do not tick that box we boot into Ubuntu using an open source video driver that may or may not be capable of running the video card to the full range of its capabilities.

I cannot determine from my brief investigation if that machine has hybrid graphics. Such a set up will run one video card at low power consumption to save battery life on less video demanding software. And another video card with high battery drain for more video demanding software such as games.

The hardware suppliers cooperate with Microsoft so that on Windows the video modes switch seamlessly as user demands change. The same hardware suppliers are not so willing to help Linux developers produce video drivers that will be as effective as those in Windows. This is a fact of life for Linux users.

To find out what video drivers are available for that machine - open a terminal and type

```
ubuntu-drivers list
```

This command will give information about the video card:

```
ubuntu-drivers devices
```

Or, we can open Ubuntu Software & Updates>Addtional Drivers tab. Allow time for Ubuntu to search the internet and then will will be able to choose between a proprietary video driver and an open source video driver.

Regards

---

