---
title: "Can't seem to install Ubuntu server 16.04 LTS"
date: 2017-12-14
forum: Server Platforms
---

### Post by eldarele on 2017-12-14
Hi, I'm new to the ubuntu/linux platform, so bear with me please.

I wanted to setup a server on a clean new physical machine to host git on it with ssh. I've tried to install Ubuntu server 16.04 LTS with a bootable usb stick, but it always seems to stop at the same place in the installation and give me an unable to install the selected kernel error for linux-generic. I've tried using a different usb stick, in case something was wrong with it, but it gave me the same error. I've also tried different bootable usb softare to create the installer (rufus and universal USB installer) but both ended up with the same error also. The rest of the installation goes fine, including the partitioning and everything, up until the moment it starts getting the linux-generic kernel. I hope someone can help me, because I'm at a loss. I've taken a picture of the virtual console output.

[ATTACH=CONFIG]277832[/ATTACH][ATTACH=CONFIG]277833[/ATTACH]

The iso I used to install Ubuntu server was: ubuntu-16.04.3-server-amd64.iso

---

### Post by howefield on 2017-12-14
Thread moved to the "*Server Platforms*" forum.

---

### Post by eldarele on 2017-12-20
Bump

---

### Post by mastablasta on 2017-12-20
what kind of hardware is it? BIOS mode or Secure boot with UEFI?

Did you check what the virtual console says about the error?

have you tried with the minimnal.iso?: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by LHammonds on 2017-12-20
It might have an issue with the hardware and doesn't have the drivers to access it.

A possible alternative would be to install VMware ESXi (free) as the base operating system and then install Ubuntu inside a VM.  You can allocate all the CPU, RAM and HD space to the single VM or split it up to share multiple VMs on the same machine.

There is no guarantee ESXi can support the hardware configuration either.  Just something to try before putting the machine in timeout in the corner to collect dust.

LHammonds

---

### Post by eldarele on 2017-12-21
Hi Mastablasta,

This is the hardware in the system:
Intel® Core i5-7500
GIGABYTE GA-H270-HD3, socket 1151 motherboard
Corsair 16 GB DDR4-2800
2x Seagate Archive HDD v2, 8 TB
Corsair CX450, 450 Watt

I tried installing Ubuntu with the link you gave me getting the mini.iso version of Ubuntu 16.04, this gave me the same error again at the same point in the installation. Might it also be a good idea to try to make a bootable usb whichs boots a live Ubuntu from usb to see if that works? What would be a good way to test if the hardware is incompatible?

@LHammonds That might be a good idea to try, I'll try doing that next.

---

### Post by eldarele on 2018-01-30
I've solved the problem by installing Ubuntu on a smaller 160 GB disk on a different PC, and then inserting it back into the original PC and booting from that disk. It seems to be running stable now :)

---

