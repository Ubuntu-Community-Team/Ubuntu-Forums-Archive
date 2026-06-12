---
title: "Is it possible booting a WinPE iso using a PXE server to UEFI based clients"
date: 2019-10-23
forum: Windows
---

### Post by memicon on 2019-10-23
Greetigs,

I am trying to figure this out but cannot find any clear answers.

**my current situation**
I am running a PXE bootfile server on ubuntu 16.04-server that contains windows 7, 8.1 and 10 running both 32 and 64-bit editions.
The installations are loaded a by seperate WinPE iso that is booted via the memdisk kernel over a tftp server to the PXE client.
When the WinPE.iso has booted a script will run in the WinPE enviroment contacting a seperate samba share containing the actual installation files and starting the windows setup.
So far ive been successfull and am able to install all windows editions this way on legacy PXE clients.

[B]Here comes the UEFI part
[/B]Now the next step is to make the PXE server also support UEFI based clients but this is where I hit a brick wall.
The problem is that syslinux does not contain a working EFI bootloader (to my knowledge) and only supports legacy clients with the pxelinux.0 bootloader.
It became aparent that I have to run a second bootloader besides pxelinux.0 for UEFI targets attempting to PXE boot.
I've started with grub and obtained the neccecary bootloaders to run it (grubx64.efi) and configuring it with grub.cfg.

After configuring I managed to get a working bootmenu when booting to the PXE server using a UEFI based system.
However plain booting the iso with the memdisk kernel didn't work as it returned **"Error: The kernel is too old"**, following with [B]"Error: You need to load the kernel first".
[/B]I've tried many different things searching the error, such as changing linux, and initrd variables in grub.cfg to linux16 and initrd16, but this didnt work sadly.
Searching the web I found very few answers on how to do this. I have managed to find this one post identical to this problem but with no answers sadly.

So I decided to make a post here hoping to find some answers on how to pull this off.

---

### Post by coffeecat on 2019-10-23
Not Ubuntu Server.

*Thread moved to **Windows** sub-forum.*

---

### Post by memicon on 2019-10-24
Nevermind, got it working

---

