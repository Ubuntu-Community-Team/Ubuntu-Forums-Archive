---
title: "Bare-minimum Ubuntu server in Windows 7 host"
date: 2010-06-11
forum: Virtualisation
---

### Post by Aikon- on 2010-06-11
Hi everyone,

I need some advice, as I am in rather uncharted territory here.

**The situation:**
I have a dual-boot machine with Ubuntu 10.04 and Windows 7, 64-bit editions both, running on a Core i7 860 with 8G RAM.

**The goal:**
I want to have (stable) bi-directional read/write access to all of my partitions from within either OS install.

**What I'm thinking**
Basically, when I'm in Linux, I think the native NTFS read/write support is sufficient (correct me if I'm wrong). However, from within Windows 7, there is currently no working Ext4 driver (that I can find). Ext2Fsd exists, but does not support extents (one of the main reasons I'm using Ext4).

I'm thinking of running a bare-minimum Ubuntu server install in VirtualBox that will access these drives and expose them to the Windows 7 host, either via NFS, Samba, CIFS, or the like. Unfortunately, I've never done anything other than regular desktop installs before, nor have I ever (really) used a virtual machine (other than Windows 7's XP-Mode).

So, I'm looking for advice on how I should go about setting this up, how I can reduce the virtual machine's footprint to a minimum, and how I can get VirtualBox to start the machine automatically on login, and have it run silently in the background. I think I want the virtual machine equivalent of a headless box, i.e. I will just SSH into it when I want to play with it.

Any help would be greatly appreciated =)

Regards,
-Aikon

---

### Post by new_tolinux on 2010-06-11
I don't really get the point of bidirectional access in the first place, since there's no need to mess around on the ubuntu partition from within Windows.
It's really not that difficult to have your Windows drive mounted when booting your Ubuntu system and you can probably replace the default folders like /home/user/Documents etc. with symbolic links to the matching folders on your Windows partition.
:!: at your own risk, I did not try the symbolic linking, so it's possible that it will mess up your Ubuntu system.

As far as I know Virtualbox doesn't have an option to start a virtual machine at boot time, which means that you probably have to use VMware, which is not the most lightweight software around ;)
But as far as I know it's not really possible to mount any hardware partition in a virtual machine, so installing a virtual machine would probably not give you access to the ubuntu-install on your harddrive.

---

### Post by Aikon- on 2010-06-11
> **new_tolinux said:**
> I don't really get the point of bidirectional access in the first place, since there's no need to mess around on the ubuntu partition from within Windows.

Unless, for example, I have a large storage drive (or in this case, several large storage drives) with around 1TB of existing data currently stored in Ext4 that I would like to be able to access from my Windows partition.

> **new_tolinux said:**
> As far as I know Virtualbox doesn't have an option to start a virtual machine at boot time, which means that you probably have to use VMware, which is not the most lightweight software around ;)

The auto-starting feature is probably the least important of the things I asked for; if I can get the Ext4 partitions shared, then I'm OK with starting it manually.

> **new_tolinux said:**
> But as far as I know it's not really possible to mount any hardware partition in a virtual machine, so installing a virtual machine would probably not give you access to the ubuntu-install on your harddrive.

According to the VirtualBox [documentation](http://www.virtualbox.org/manual/ch09.html#id2654934), it sure sounds like it's possible. I was hoping to find someone that has done something similar so that they can point out some of the pitfalls they ran into in advance.

-Aikon

---

### Post by Aikon- on 2010-06-12
For reference, things are coming along OK. I am using a VM with 512 MiB RAM at the moment, running a server install of Ubuntu 10.04. I have gotten file sharing working via Samba.

I figured out that you can run a "headless" VM by using the built-in VirtualBox commands,
```
VBoxHeadless -startvm <vm_name> --vrdp off
```
however this still leaves the terminal window that spawns the process open. As an alternative, I found this handy extension for running a headless VM in the system tray: [http://www.toptensoftware.com/VBoxHeadlessTray/](http://www.toptensoftware.com/VBoxHeadlessTray/)

I have not yet been able to get raw disk access working, however; I keep getting the following error:

```
>>> VBoxHeadless -startvm Frenzy --vrdp off
Oracle VM VirtualBox Headless Interface 3.2.4
(C) 2008-2010 Oracle Corporation
All rights reserved.

Error: failed to start machine. Error message: VD: error VERR_INVALID_FUNCTION opening image file 'C:\Users\sarmitage\.VirtualBox\nix_disk_1.vmdk' (VERR_INVALID_FUNCTION).
Failed to open image 'C:\Users\sarmitage\.VirtualBox\nix_disk_1.vmdk' in read-write mode rc=VERR_INVALID_FUNCTION (VERR_INVALID_FUNCTION).
Failed to attach driver below us! Invalid function. (VERR_INVALID_FUNCTION).
AHCI: Failed to attach drive to Port2 (VERR_INVALID_FUNCTION).
Unknown error creating VM (VERR_INVALID_FUNCTION)
```

I have started a thread at the VirtualBox forums (see [here](http://forums.virtualbox.org/viewtopic.php?f=6&t=31956)) as well looking to get this resolved.

Aikon-

---

### Post by Aikon- on 2010-06-13
As it turns out, for some reason when I create the raw disk access images, using code such as the following
```
VBoxManage internalcommands createrawvmdk -filename C:\Users\sarmitage\.VirtualBox\Physicals\disk-a.vmdk -rawdisk \\.\PhysicalDrive0
```
the image files created are listed as IDE. Whether this is a raw disk access limitation or my bios configuration or what is unclear, but if you add the images to a VM using a SATA controller, you will get the error above. I moved the images over to the IDE controller and it works fine now.

I now have pretty much exactly what I want working, the Ubuntu box reads the RAID arrays, mounts the Ext4 volumes therein, and shares those over the network using samba, which I have mapped on my Windows host. Other computers on my network (such as my laptop) will be able to access the samba shares in the same way, since my VM shows up as just another computer on the network, but my Windows host never has to send data out over the ethernet port (the bridged connection is smart enough to skip that step and just communicate directly).

The only remaining issue is that the VM tries to boot from the IDE controller by default (i.e. the raw disks attached), but their MBR is written for the global system. When booting the VM, I need to have the GUI open and manually specify the boot device to be the regular VDI image on the SATA controller. A [ticket](http://www.virtualbox.org/ticket/6979) has been submitted to allow specifying the boot device in the machine's XML configuration file. Another alternative would be to re-create the raw disk access images with the -mbr command to set an out-of-disk file for storing the virtual MBR information.

Aikon-

---

### Post by TheFu on 2010-06-14
It sounds like you've done a bunch of work ... when perhaps a simpler disk setup would make your life easier.

HostOS (Unknown)
  - Client 1 - Linux
  - Client 2 - Windows-whatever

So, in this situation, I'd strongly recommend partitioning your disk(s) like:
60GB - hostOS
100GB - all VM client OSes
840GB (whatever) - shared data across all VMs and the hostOS.

In this way, you can access the data area from any of the VMs **AND** from the host. If Linux is your host, you'll have great performance with scripting too. Access to a Windows HostOS also works, but UNIX scripts with a find or -R switch will often behave VERY SLOWLY, if at all, IMHO.

You only install program, files inside each OS, so HOME and /user/ directories are placed on the data partition too.  It really makes backing up this data easier.

You can use NFS or Samba if you like, but the built-in Shared-Folders won't have the overhead of a network stack. I find that WinXP clients connecting to a Linux host OS via shared folders gets native drive performance or so close to native it isn't worth haggling.

Good luck.

---

### Post by TheFu on 2010-06-14
Starting a VM at boot is simple. Use the command line vboxmanage tool. I'm pretty certain either autoexec.bat or msconfig or /etc/rc.local can be configured to make a VM start in that way.

---

### Post by Aikon- on 2010-06-14
> **TheFu said:**
> It sounds like you've done a bunch of work ... when perhaps a simpler disk setup would make your life easier.

HostOS (Unknown)
  - Client 1 - Linux
  - Client 2 - Windows-whatever

So, in this situation, I'd strongly recommend partitioning your disk(s) like:
60GB - hostOS
100GB - all VM client OSes
840GB (whatever) - shared data across all VMs and the hostOS.


I think you have misunderstood my goal here. I am not setting up a server, I am simply trying to hack my working desktop to give me access to my pre-existing RAID-5 storage array, running with Ext4 on top. I traditionally use a full-blown Ubuntu installation as my primary OS, and have for the past 6 years or so.

Now I find myself in this strange predicament of also running Windows 7 on the same computer; I haven't bothered with dual-booting in about 4 years or so. The reason for this is primarily Starcraft II, so I have no desire to run Windows in a VM. Similarly, when I'm not playing SC2, I don't want to have the overhead of my primary DE running inside a VM, so dual-boot remains the option of choice here.

Having said that, all of my music, movies, TV shows, documents, pictures, installers, scripts, and downloads are located on the large RAID array. I would like to have access to them when I am running Windows so that, for example, I can put my entire library on shuffle while playing SC2.

So raw performance is not the key factor here; simply being able to access my files during the times I am in Windows is. If there were a working Ext4 driver for Windows, I could use that and plug into my external backup drive, where I have dated backups of most of the things I need. If there were also an mdadm implementation for Windows, I would also be set. Unfortunately, neither of these is the case.

---

