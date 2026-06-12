---
title: "Older ISO images will no longer load on secure boot systems"
date: 2020-08-11
forum: Ubuntu, Linux and OS Chat
---

### Post by grahammechanical on 2020-08-11
There had been a couple of requests on this forum for help regarding problems caused by the Community fixing a vulnerability called BootHole that is in Grub2.

I quote from one of the threads and provide information from a Canonical blog post explaining the thread title I have chosen.

> Note:  after this fix, you still can not boot any older LiveUSBs or DVD’s. The  Boot choices menu (F12 on my system) does not even show a bootable  device for the LiveUSB! I think that is the intended action  but I’m not  sure.

Linux distributions can only be loaded on a  UEFI/Secure Boot system if they have a small binary package (a shim)  that has a certificate signed by Microsoft. ISO images that have been  published before BootHole was fixed (if it has been fixed) cannot have  their copy of Grub2 updated. Therefore to prevent an ISO image with a  version of Grub2 that has a dangerous vulnerability from loading  Microsoft had to upgrade its secure boot code to invalidate the  previously signed certificates. Only the very latest ISO images with a  fixed Grub2 will have a valid certificate for their shim.

[https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities](https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities)

> but to also ensure that any old, vulnerable Linux install media cannot  be used in the future to attack existing systems. This requires a  coordinated approach across the community of Linux distributions, and  also the wider UEFI community including Microsoft and others. 


> These old install media would then always be trusted, even though they  contain this vulnerable version of GRUB2 and hence could be used to  bypass UEFI Secure Boot on any system. Luckily, the UEFI specification  provides a way to distrust either particular certificates or particular  binaries by adding entries into the UEFI forbidden signature database  (DBX).

From now on anyone wishing to install a Linux  distribution on a UEFI/Secure Boot system will only succeed if they are  using the latest published ISO image of the distribution. Any ISO image  downloaded before the end of July 2020 (as a guess) should be blocked by  Secure Boot. We may need to remember this if any Want To Be Users come  on this forum asking why their Ubuntu live image cannot run on a machine  with Windows 10 installed.

One answer would be to advise turning  off Secure Boot. It should not be necessary to do that. In fact it has  not been necessary to do that since from the introduction of Secure Boot  by Microsoft Canonical obtained a certificate to allow Ubuntu to load  on Secure Boot systems.

This forum should be part of the wider community promoting secure computing.

Regards

---

### Post by monkeybrain20122 on 2020-08-12
But this won't affect installing on machines without Windows, correct?

---

### Post by sudodus on 2020-08-12
@grahammechanical,

Is this affecting only live boot and installation?

Or is it also affecting installed Ubuntu family systems? In other words, can a user who wants secure boot turn it on after installing, updating and upgrading the Ubuntu family system?

---

### Post by guiverc on 2020-08-12
My belief/understanding (which is *limited*) is that it'll impact **any** dual-boot system (or second OS, ie. if you have a dual boot like my current *groovy* and 18.04/*bionic* system, upgrading one (fully with all patches **including DBX**) would stop UEFI in recognizing the other un-updated system as safe/UEFI-compliant and thus not boot.  It doesn't matter if the second OS is windows or a GNU/Linux; it'll impact any non-upgraded systems booting in UEFI.  It also impacts live/installation media too, or any system booted by UEFI (why it won't boot older ISOs on fully patched systems)

To learn more detail about it, I'd recommend [https://ubuntusecuritypodcast.org/episode-84/](https://ubuntusecuritypodcast.org/episode-84/)

(or if you just want to download & listen straight away [https://people.canonical.com/~amurray/USP/USP_E084.mp3](https://people.canonical.com/~amurray/USP/USP_E084.mp3) )

See also [https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities](https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities)

---

### Post by sudodus on 2020-08-12
Maybe I don't understand this, but I did some tests:

I have access to a fairly new computer, a [Lenovo V130](https://dustinweb.azureedge.net/media/494085/v130.pdf).

This computer was delivered with Windows 10 installed in UEFI mode with secure boot. It is running three versions of buntu now, Lubuntu 16.04 LTS, Lubuntu 18.04 LTS and Xubuntu 20.04 LTS, still in UEFI mode with secure boot.

Today I updated and upgraded the 20.04 LTS version

```

sudo apt update
sudo apt full-upgrade

```

and it was successful (there were no complaints). I noticed that grub and the kernel were upgraded as well as the firmware.

Then I tried rebooting. It was still possible to boot into the 16.04 LTS and 18.04 LTS versions. OK, maybe this works becasue grub is upgraded.

Then I booted from an installed Ubuntu 20.04 LTS system in an SSD. This system was fully updated and upgraded July 17 (if I understand correctly before the fixes for the boothole bug).  It worked.

Then I booted a USB pendrive with a grub-n-iso (isoboot) system with xubuntu-20.04-core-amd64.iso published in April. It worked.

I double-checked that secure boot is enabled in the UEFI/BIOS menus. I could also verify that secure boot (still) locks out Sparky Linux, [FONT=Courier New]**sparkylinux-5.11-x86_64-lxqt.iso**[/FONT]. This live drive boots in UEFI and BIOS mode, but there is no signature for secure boot.

So it seems to me that this update & upgrade does not really affect the secure boot of the Lenovo V130. Maybe it would be different, if Windows would be [re]installed and allowed to upgrade everything it wants to upgrade.

---

### Post by oldfred on 2020-08-12
With Ubuntu and multiple boots of Ubuntu on the same drive, there is only one - shimx64 (or two, shim & grubx64) Ubuntu boot entries in UEFI. And only one /EFI/ubuntu folder with the UEFI boot files.
Additional versions of grub are then added to grub menu for booting.

I do not think they have yet revoked the old dbx.
[https://lists.gnu.org/archive/html/grub-devel/2020-07/msg00034.html](https://lists.gnu.org/archive/html/grub-devel/2020-07/msg00034.html)
> Updated GRUB2, shim and kernels from all the affected vendors will be made
available when the embargo lifts or shortly thereafter. An updated dbx from
the various affected vendors will also ship, although possibly not at the same
time. The new Microsoft dbx will be provided for download here [4].


I do not have Secure Boot on and have various old versions of Ubuntu installed for testing. But primarily boot main working install now Kubuntu 20.04. But have not booted old main installs, 16.04, 18.04, and Ubuntu 20.04. Plus a few others. I think they have to delay the update to the dbx for users to have updated kernels as well as grub. But then those of us with multiple installs not recently booted and updated will find they do not work. Not sure then, if my installs will work with Secure boot off, or some issue will appear.

---

### Post by mastablasta on 2020-08-13
> **sudodus said:**
> 
Maybe it would be different, if Windows would be [re]installed and allowed to upgrade everything it wants to upgrade.

Secure boot is actually a MS windows feature not UEFI, so it *could *make a difference if you did full update/upgrade on windows.

i turned secure boot off on Laptop and i think it is on on the newer desktop. i don't feel any less secure. :)

---

