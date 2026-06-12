---
title: "How to virtualise real Windows installed?"
date: 2014-02-27
forum: Virtualisation
---

### Post by Ral_Ulises_Mart on 2014-02-27
> Sorry for my bad english.

Hi there, I've been searchinf for information about how to virtualise windows installed in the hard drive with linux and how runs it inside linux and i learnt this code to create the virtual disk from one real

```
sudo VBoxManage internalcommands createrawvmdk -filename windows.vmdk -rawdisk /dev/sda

```

But the problem is that Windows is installed in sda and ubuntu in sdb like this.

```
raul@raul-desktop:~$parted
(parted)print all
Modelo: ATA SanDisk SDSSDP12 (scsi)
Disco /dev/sda: 128GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. gpt

Numero  Inicio  Fin    Tamaño  Sistema de archivos  Nombre                        Flags
 1      1049kB  316MB  315MB   ntfs                 Basic data partition          oculta, diag
 2      316MB   420MB  105MB   fat32                EFI system partition          arranque
 3      420MB   555MB  134MB                        Microsoft reserved partition  msftres
 4      555MB   128GB  127GB   ntfs                 Basic data partition


Modelo: ATA WDC WD10EZRX-00A (scsi)
Disco /dev/sdb: 1000GB
Tamaño de sector (lógico/físico): 512B/4096B
Tabla de particiones. gpt

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Nombre                        Flags
 1      17,4kB  134MB   134MB                        Microsoft reserved partition  msftres
 2      135MB   486GB   486GB   ntfs                 Basic data partition
 6      486GB   486GB   210MB   ext2                                               arranque
 7      486GB   501GB   15,3GB  ext4
 8      501GB   518GB   16,6GB  ext4
 4      518GB   518GB   315MB   ext2                                               arranque
 3      518GB   992GB   473GB   ext4
 5      992GB   1000GB  8590MB  linux-swap(v1)


```

[IMG]http://i.imgur.com/W7gM2yA.png[/IMG]
[IMG]http://i.imgur.com/QTK4RfM.png[/IMG]

Soooo, how do I do that?

That's the error with...


```
sudo VBoxManage internalcommands createrawvmdk -filename windows.vmdk -rawdisk /dev/**sda**

```
[IMG]http://i.imgur.com/3YxO9XK.png[/IMG]
And that's the error with...
```

sudo VBoxManage internalcommands createrawvmdk -filename windows.vmdk -rawdisk /dev/**sdb**
```
[IMG]http://i.imgur.com/1MYVhMJ.png[/IMG]

I think the problem is that a i need bot hard disk in the new virtual disk but how to do it?

   thanks in advance.


SOLVED, but the problem nows is that appears a black screen but the OS goes well and I know it because I listen the sound of skype at the start.

---

### Post by TheFu on 2014-03-06
When MS-Windows is installed, it becomes tied to the physical hardware. Any change in the environment will confuse MS-Windows - and running in a virtual machine with virtual motherboard, south bridge, north bridge, disk controllers, network cards and GPU will confuse MS-Windows.  Microsoft decided that preventing piracy by connecting the installed OS to the hardware was necessary.  Basically, it cannot work from a prior Windows install to a physical machine.

You can install directly to a partition using most of the virtualization tools, but this will be a fresh install, not Windows previously installed. After doing this, the newly installed partition will not be bootable on the non-virtual hardware. Pick 1, be happy.

Of course, with Linux OSes, switching between virtual and real hardware installs is easier - not tied directly to the hardware and UUIDs will mean partitioned HDDs should be available as expected, if written to a normal partition.

Hope that clarifies a little.

---

### Post by newbie2244 on 2014-03-10
Greetings Ral -- I just did this yesterday - somehow. I have an HP Pavilion with Insyde? BIOS which came with WIndows 8. Be patient with my description because I don't fully understand this myself.  -----   I made a bootable USB stick with Ubuntu Linux 12.04LTS.  ___ In BIOS,  I enabled virtualization first. Then in BIOS,  I changed the boot order so that the  USB drive was first.  USB loaded and  Linux finally  loaded (a kind of temporary mount). But I couldn't install it to HD.   I was connected to the net.  I did a boot repair within the loaded Linux. And then ran the installer (universal installer). Still couldn't get an Ubuntu install on HD.  Disabled secure boot.  Same problem. Enabled Legacy Support. Ran the installer -- and finally got Ubuntu installed on the HD. Shutdown and started. Disconnected the USB stick and booted directly into Linux. OK but I needed dual boot. Went back to BIOS and changed boot order again so that the first boot device would be OS Boot Mgr. Shutdown (not restart). Started and got GRUB menu.  --Very long listing.  ----   NOW GET THIS  ------ my default OS was now Ubuntu. In order to boot Windows, I had to select a file named _Windows UEFI bkpbootmgfw.efi_, about halfway down the menu listing. ANd now Windows is embedded in Ubuntu with 207 GB of disk space.

Clarification -- Ubuntu now has 207 GB of disk space available for it.

---

