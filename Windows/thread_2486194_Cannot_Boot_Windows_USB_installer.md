---
title: "Cannot Boot Windows USB installer"
date: 2023-04-22
forum: Windows
---

### Post by woodmarc on 2023-04-22
I am having the same problem which I have been trying to solve for weeks.

1- I decided to f**ormat my Lenovo laptop and create 2 partition **and a SWAP space on my HD
2- I i**nstalled Ubuntu 22.04** on one of the partitions
3- I realized that I should have had Windows 10 installed before ubuntu (the opposite would not work)
4- I made a bootable USB stick from a Windows 10 ISO file on a different computer (win OS) to format the computer again and Install Windows 10
5- Started my laptop holding Fn+f12  gives me 4 options [Normal boot, BIOS Setup, Boot menu, System Recovery] selecting ANY of them will bring me to the Boot menu
6- The boot menu only shows me 3 options [Ubuntu, recovery mode, Advanced UEFI setting]


**  I am still unable to boot my Windows 10 bootable USB **(I also tried with an Ubuntu Bootable USB, which also does not show at boot menu) **on my Ubuntu 22.04 system**

_**Does anybody know how to force my computer to boot from USB in order to do a fresh install of a dual OS system**_?

[https://paste.ubuntu.com/p/tzVpPZsPyP/ ]("https://paste.ubuntu.com/p/tzVpPZsPyP/")<-- Boot repair logs

---

### Post by yancek on 2023-04-22
Line 149 of your boot repair shows "Boot0012* USB HDD: Kingston DataTraveler G3".  Is that your bootable USB?  You need to get into the BIOS not the Boot Options so that you can change to set the USB to boot first.  You must have done that to install Ubuntu.

> - I realized that I should have had Windows 10 installed before ubuntu (the opposite would not work)

It will work if you select the Custom installation option in windows.  Since you appear to have had an EFI isntall of windows, after installing windows it would have set itself to first boot priority so you would need to go into the BIOS firmware to set Ubuntu to first boot.

Line 143 of boot repair shows a windows entry in the BIOS firmware but the partition information does not show a windows install so it appears you have deleted the first partition which contained windows EFI files and created a new one with Ubuntu installed there and an EFI partition on the 3rd partition.

>  (I also tried with an Ubuntu Bootable USB, which also does not show at boot menu) **on my Ubuntu 22.04 system**

You won't boot the USB from the Ubuntu Grub menu, you need to access the BIOS firmware boot options to do that.   Generally immediately on boot you will see a message on screen for a few second telling you which key to use to access the BIOS which is what you need not boot options.   I don't know what that key is on a Lenovo but it should be easy enough to find.

---

### Post by oldfred on 2023-04-22
Please do not hijack another users thread.
Boot issues often are unique and unless exactly the same model system & issue where you can contribute to thread, better to start your own thread.

Is system UEFI or BIOS?
And how you boot install media, whether Windows or Ubuntu is then how it installs. Systems since 2012 are UEFI, so installer should be booted in UEFI boot mode. Many new systems after 2020 are now UEFI only, no legacy/BIOS boot mode at all.

From system you created ISO to flash drive does flash drive boot? In UEFI mode?
What model Lenovo?

---

### Post by zebra2 on 2023-04-22
Most Lenovo's use Fn F1 or Fn F2 for Bios and F12 for the Boot Menu.  I have not had any problem using the F12 menu for a Ubuntu USB Installer without out setting USB in the Bios. Don't know anything about current Windows. In addition I have two current Lenovo Ideapads that don't have a legacy mode in Bios.  I still can do a legacy install however if I create a EFI/ESP boot partition (don't need the bios/boot) and format the system partitiion (root and home) with EXT4.  I do have to turn off Fast Boot in the bios but there is no UEFI option in the bios to turn off UEFI.  Ubuntu seems to detect what I want based on the partition type. EXT4 = Legacy,  GPT= UEFI. In addition I personally put a 4G SWAP as SDA2,  It doesn't matter if all of this is right or wrong. It is what I had to do to get 23.04 Lunar to install. The current problems probably don't exist with 22.04. I've done over three dozen desktop/current ISO installs of 23.04 over the past six months and there have been problems. Usually a workaround is needed.

---

