---
title: "New install only boots to grub"
date: 2016-11-28
forum: Ubuntu/Debian BASED
---

### Post by courtney2 on 2016-11-28
I installed Kubuntu 16.04 on my computer, and the installer went without any issues. However, now when I boot my computer it goes straight ot grub (not grub rescue). My system is a UEFI system with an Asus z97 Pro motherboard. No issues with this computer the past 2 years I have had it except now. I am able to boot to my system from grub and get a GUI, but repairing grub does not fix my issue. It is dual booting with Windows 8.1 (I have to keep my system UEFI because for some reason booting Windows in legacy mode results only in BSOD)

---

### Post by oldfred on 2016-11-28
I have Asus Z97-AR. I was only able to get it to install with Secure boot off (OS type - Other, not Windows) and boot USB with UEFI only. Even the UEFI or BIOS would only boot in BIOS mode. I also changed fast boot in UEFI to off while configuring and then 3 sec delay, so I had time to press a key if needed to make changes.

I do not have Windows, but Windows updates may turn UEFI Secure boot and Windows fast startup back on. Make sure they are off.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by courtney2 on 2016-11-28
I looked to see if secure boot was enabled somehow, and it is not. I have it in the "other OS" mode for UEFI. I had this working before quite a while ago but now it doesn't want to behave. Disabling fast boot doesn't fix my issue either

Here is my boot info: [http://paste2.org/HO2GZWpK](http://paste2.org/HO2GZWpK)

/dev/sda3 is intentionally unmounted right now. It is a partition on an ssd where I put games. I will be putting that in my fstab file once this is cleared up. The bootloader should be on /dev/sda. I have done grub-install /dev/sda a few times already

---

### Post by oldfred on 2016-11-28
Not familar with KDE Neon. That is an unofficial flavor?
Moved to other OS subforum.

I do not see anything particular out of place. But part of ESP entries say neon and one says ubuntu. So did you convert install?

---

### Post by courtney2 on 2016-11-30
It's KDE's official distro based on Ubuntu 16.04. I found out the problem was just an issue with the ISO, I had to do this:

mkdir efi
sudo mount /dev/sda1 efi/
sudo cp efi/EFI/neon/* efi/EFI/ubuntu/

Temporary bug with the way things are created in grub I guess...I think they fringed from the official Ubuntu way of doing EFI boot and it didn't work, so grub was looking for the wrong folder

---

### Post by oldfred on 2016-11-30
Glad you got it working.

I had similar issue as I have have several Ubuntu installs.
I changed DISTRIBUTOR=  in /etc/default/grub to my version of Ubuntu.
And UEFI install did put a new folder in ESP and entry in UEFI.
But somewhere grub & shim are hard coded to find /EFI/Boot/ubuntu, so even with changing name I could not have separate UEFI entries for each install.

---

### Post by courtney2 on 2016-12-07
Definitely a touchy system! It seems that should be a bug that should be fixed more downstream. I wonder why distros will change that info knowing that it would cause problems

---

