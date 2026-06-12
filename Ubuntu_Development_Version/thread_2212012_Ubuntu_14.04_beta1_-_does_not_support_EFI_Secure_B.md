---
title: "Ubuntu 14.04 beta1 - does not support EFI Secure Boot"
date: 2014-03-18
forum: Ubuntu Development Version
---

### Post by realavaloro on 2014-03-18
Hi,

I've got a Lenovo x240 with EFI mode enabled in BIOS (GUID Partition Table).
I made a bootable USB with Ubuntu gnome 14.04 beta1 and it won't boot. It brings me to a grub prompt command line (and i don't know what to do there) and I could read that Secure Boot prevented it from booting.
I was able to boot Ubuntu 13.10 with USB in EFI mode properly.

My question is that I understood Ubuntu (including gnome distro) has EFI Secure Boot support since 12.04, and if 13.10 has Secure Boot support.. why the 14.04 beta1 has not this support?

I am trying to install Ubuntu with Windows 8.1 dual booting and I have to decide what ubuntu version to install. I wanted to install ubuntu gnome 14.04 beta1 and then update to LTS without messing with Grub, but seeing I cannot boot it unless I disable Secure Boot I might go for installing 13.10 that handles properly the secure boot enabled.

Anybody with same issue?

Thank you

---

### Post by Bucky Ball on 2014-03-18
*Thread moved to **Ubuntu +1**.*

Any and all threads regarding 14.04 LTS go here for now. Thanks.

---

### Post by slooksterpsv on 2014-03-19
I have an idea on why this may be (I could be wrong) - until the LTS is officially released, they may have not chosen to sign the EFI, as for every daily build, beta, etc. up until the release, they'd have to resign the EFI. Where Beta is not meant for production machines, and thus preferred to reinstall for the LTS, it only seems logical to not worry about the signing the EFI until it ships/releases.

---

### Post by oldfred on 2014-03-19
Post link to bootinfo report.
I know there was a bug on grub booting Windows 8.1 when secure boot is on, but it should install. Unless as slooksterpsv suggests it is not fully implemented yet. But I would think they want that tested also.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Some UEFI based systems do have issues and you have to install in BIOS boot mode, then use Boot-Repair to convert to UEFI.

---

### Post by grahammechanical on 2014-03-19
Grub is not used in a Ubuntu live session. Grub is only used after Ubuntu has been installed. One of the last things that the installer does is install Grub.

I doubt very much the claim that Ubuntu 14.04 Beta does not support Secure Boot. UEFI and Secure Boot are different subjects. And there are other reasons why a live session will not run and we might need to use the F6 options Or an installed Ubuntu will not load.

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[/FONT]
[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Other than that I would support the advice to wait until 14.04 is officially released. In the past I have had development images fail to load or install. This can happen at the start of the development cycle and it can also happen towards the end of the development cycle. It is part of the development cycle as the developers move from adding new features to fixing known bugs prior to release.

I do not have a motherboard with UEFI or Secure boot so I do not speak from experience but I also think that the live session has to be run in EFI mode as well.

Keep in mind that over the development cycle we have had several changes to the Linux kernel version. If those kernels were not signed in accordance with the secure boot protocols then everyone of those kernels would have failed to install on the machines with secure boot that the testers were using.

Regards.

---

### Post by mc4man on 2014-03-19
I know that daily images of Ubuntu & Lubuntu both will boot to live session  when Secure boot is enabled, tested here on Lenovo y510p
(i turn off SB here in use but that's besides the point.

I think the question here is  - is there an issue with the Ubuntu Gnome image is this regard, haven't had a chance to ck. though I'd use the daily image to see (or do an install from..
[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/)

---

### Post by alex.wedensky on 2014-03-19
daily builds of 14.04 Ubuntu Unity and Kubuntu boot from live USB on my Yoga 2 Pro without any tinkering (no need to turn Secure Boot off).

---

### Post by grahammechanical on 2014-03-20
I do not see a Ubuntu ISO image for non-secure boot motherboards and a Ubuntu ISO image for secure boot motherboards. The same 64 bit ISO image is offered for both types of motherboard. I do not think that it is necessary to have a signed Linux kernel for secure boot motherboards and an unsigned Linux kernel for non-secure boot motherboards. To try to do things that way would create extra work in building and testing the images.

Before we jump to the conclusion that secure boot does not work in 14.04 we should first eliminate all the other reasons why Ubuntu 12.04 or 13.10 and 14.04 fail to run a live session on a machine with Windows 8 installed. And also why they fail to install and load to a working desktop on Windows 8 machines. And there are plenty of posts in the other sections of this forum that show that it is not just 14.04 that has problems with Windows 8 machines. First eliminate the obvious. That is part of testing.

Regards.

---

### Post by mc4man on 2014-03-20
Tested with current Ubuntu-gnome image & again no issue booting to live usb with Secure boot enabled. So Op's issue is something else other than thread title

---

### Post by ronb19495 on 2014-03-23
> **realavaloro said:**
> Hi,

I've got a Lenovo x240 with EFI mode enabled in BIOS (GUID Partition Table).
I made a bootable USB with Ubuntu gnome 14.04 beta1 and it won't boot. It brings me to a grub prompt command line (and i don't know what to do there) and I could read that Secure Boot prevented it from booting.
I was able to boot Ubuntu 13.10 with USB in EFI mode properly.

My question is that I understood Ubuntu (including gnome distro) has EFI Secure Boot support since 12.04, and if 13.10 has Secure Boot support.. why the 14.04 beta1 has not this support?

I am trying to install Ubuntu with Windows 8.1 dual booting and I have to decide what ubuntu version to install. I wanted to install ubuntu gnome 14.04 beta1 and then update to LTS without messing with Grub, but seeing I cannot boot it unless I disable Secure Boot I might go for installing 13.10 that handles properly the secure boot enabled.

Anybody with same issue?

Thank youno 1 14.04 does support secure boot I have it running on this machine dual booting with windows 8.1.when you say it wont boot are you using a usb stick . if so try this put your usb stick in reboot when it gets to bios when booting hit f2 or delete whatever gets you into your bios setup,got to boot option in bios look at what it has in boot option in regards to cd dvd usb look to see if you have 2 usb entries for booting one will be mbr and the other will be usb uefi if so make that your first boot then reboot it should come up with ubuntu menu and uefi is a black background when running from live boot.I has similar problem to you on my pc till I found the uefi problem

---

