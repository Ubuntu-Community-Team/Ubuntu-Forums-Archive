---
title: "Messed up with UEFI dual boot"
date: 2016-01-15
forum: Windows
---

### Post by tropiko-matrox on 2016-01-15
My motherboard has UEFI (asus z87 plus). I have an intel 120gb SSD. 

I installed Windows 7 64 on it using an USB stick by booting into the installer in **NON-UEFI mode**. After a while I decided to install manjaro and the only way to boot into it was through UEFI mode on the USB stick.
I proceeded with the install as follows : from inside windows I shrunk the windows partition, I now have 

[LIST]
[*]100mb system reserved
[*]96gb windows install
[*], and the rest free for linux
[/LIST]


[LIST]
[*]/dev/sdb1            2048    206847    204800  100M  7 HPFS/NTFS/exFAT
[*]/dev/sdb2          206848 185640959 185434112 88.4G  7 HPFS/NTFS/exFAT
[*]/dev/sdb3  *    185640960 187688959   2048000 1000M 83 Linux
[*]/dev/sdb4       187688960 234436544  46747585 22.3G 83 Linux
[/LIST]

3rd partition made /boot/efi, 4th root, and /home on another hard drive.

I've tried using a program, rEFInd, didn't help at all except for annoying me with yet another boot loader gui crap. I've tried adding a windows 7 entry to /etc/grub.d/40_custom or the /boot/grub config. 
I have no idea what I'm doing really, I don't know much about how GRUB nor UEFI works and I think I ****ed up my system. I just want to be done with this efi business, overtly complicated for no reason because of backward (in)compatibility.

Is there any way to recover my windows installation? 


[IMG]https://forum.manjaro.org/Themes/Skyline/images/icons/modify_inline.gif[/IMG]

---

### Post by yancek on 2016-01-15
Take a look at the link below under the section "General Principles" which should apply to any dual boot scenario.  If you had windows installed using MBR, then you must install your other system using MBR and not UEFI.  Doing so gets the results you have.  If you only saw the option to install using UEFI with your Manjaro disk, it was time to stop.  You could try getting the boot repair software from the link below.  Download it and burn the iso to a CD or flash drive, boot it up and select the option to Create BootInfo Summary and post a link to the output here.  It should give enough information for someone to offer suggestions.

Manjaro is unrelated to Ubuntu.  Did you try posting at the Manjaro forums?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tropiko-matrox on 2016-01-16
Thanks for the reply. I learned this the hard way trying to fix the boot loader on a msdos partition (MBR) windows 7 and uefi installed Manjaro.


Thread on manjaro forums investigating my problem : [https://forum.manjaro.org/index.php?topic=30174.0](https://forum.manjaro.org/index.php?topic=30174.0)

For anyone else having this issue, here's how I solved it:
 Partitioning the usb stick in gpt /w msftdata flag makes it uefi bootable, also there's a little hack to make w7x64 bootable in uefi only mode.


I set CSM to UEFI only and formatted my USB stick to GPT, copying all the data from the win7x64.iso to the stick, and copied the **bootmgfw.efi **file from sources\install.wim\Windows\Boot\EFI, renamed it **bootx64.efi **
into the /efi/boot folder of the stick.
I then installed manjaro normally (with a small 100mb fat32 partition as /boot/efi and the rest of my empty space as root) and ran **sudo update-grub** to make the bootloader able to select windows 7 64.

---

### Post by JayKay3OOO on 2016-01-16
My bios has uefi mode and legacy mode. I install Linux, grub loads under legacy mode, I want windows I change the bios setting to uefi and windows loads. It's not elegant, but like you I've not had much experience with uefi.

---

### Post by tropiko-matrox on 2016-01-16
Man, it's so much better to have it all under grub and slightly faster boot times because of GPT. Do try what I just did (from my prev post and the thread on manjaro forums).

---

