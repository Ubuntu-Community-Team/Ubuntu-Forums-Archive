---
title: "Virtualization Moron with a few questions."
date: 2007-12-14
forum: Virtualisation
---

### Post by Rockman4140 on 2007-12-14
I have been looking for a way to get access to my Linux partition at the same time that I'm using Windows. Since Ubuntu is kludged together by unofficial strategies and has little to no hardware support for my laptop, I've been using Vista more and more.

While Vista works, I have quite a set of files I have on Ubuntu that I need. Instead of writing to and erasing my fileswap partition all the time, I was wondering if I could use a VM of my actual Linux partition to move and gain access to files.

I am running Windows Vista and Ubuntu Gutsy Gibbon. I was wondering what would be the best option in terms of software, or if anyone has successfully done this and any tips you have.

---

### Post by elspiko on 2007-12-14
[http://www.fs-driver.org/download/Ext2IFS_1_10a.exe]("http://www.fs-driver.org/download/Ext2IFS_1_10a.exe")

Not sure if it works with vista, but it would give you full access to your Linux partition from Windows

---

### Post by Rockman4140 on 2007-12-20
Yeep, sorry. I was hoping there is a way to actually run Ubuntu on Vista, seeing as how I'd hate to keep switching after reading something useful online that I could test with Ubuntu and have to save it, switch out, and then turn out I need another page I didn't save.

Right now my Ubuntu is horribly broken and busted. No non-painful resolution, defunct music, and catch-22 internet. I cannot fix it because I do not have the resources at my fingertips to help me, and I cannot get them if I do not have internet.

I was just hoping I could open a window to my Ubuntu partition to work with the config files or atempt to update it through my wireless connection, without downloading and copying files over and over.

---

### Post by lmcfadden on 2007-12-21
> **Rockman4140 said:**
> Yeep, sorry. I was hoping there is a way to actually run Ubuntu on Vista, 

I was just hoping I could open a window to my Ubuntu partition to work with the config files or atempt to update it through my wireless connection, without downloading and copying files over and over.

    I am running VMWare Server on XP Home, with Ubuntu Gutsy and Dreamlinux running as VMs.  I have not tried it with Vista, however I see no reason it will not work the same as in XP.

    I also believe VMWare server will let you create a virtual machine and boot from another Partition as opposed to the VM Virtualized partition, perhaps you could install the Virtual Ubuntu install to your existing partition?  Once setup, you can install the VMWare tools to enable file sharing.

---

### Post by Rockman4140 on 2007-12-22
So you are using it with your Ubuntu partition? Any special ticks I need to know before i try it?

Also, thank you very much for the suggestion, I shall tinker with it at work.

---

### Post by lmcfadden on 2007-12-22
No I am not using it with a Ubuntu partition, I have Ubuntu running as a VM and use a Virtual partition (hard drive).  However I have looked through the help file for VMWare Server, and pasted the section on real hard drive partitions below.

Good luck with this, sounds like it should work.

______________________________________________________

Configuring Physical Disks 
Select: VM > Settings > Hardware > Hard Disk 

You can add a physical (sometimes called raw) disk to your virtual machine. The virtual machine should be powered off before you begin. If it is not, shut down the guest operating system normally, then click Power Off on the console toolbar. 

Caution: Physical disks are an advanced feature and should be configured only by expert users. 

A physical disk directly accesses an existing local disk or partition. You can use physical disks if you want VMware Server to run one or more guest operating systems from existing disk partitions. Physical disks can be set up on both IDE and SCSI devices. At this time, however, booting from an operating system already set up on an existing SCSI disk or partition is not supported. 

The most common use of a physical disk is for converting a dual-boot or multiple-boot machine so one or more of the existing operating systems can be run inside a virtual machine. 

The Disk information section displays the following information, depending upon whether you are using a disk partition or the entire physical disk: 

Using whole disk — The device name, an indication that the whole disk is being used and the capacity of the physical disk are displayed. 
Using partitions — The device name, an indication that partitions are being used and information about each partition (name, file system type and capacity) are displayed. 
Settings displayed in the Disk information section are specified at the time you create the virtual disk and cannot be changed. 

Caution: If you run an operating system natively on the host computer, then switch to running it inside a virtual machine, the change is like pulling the hard drive out of one computer and installing it in a second computer with a different motherboard and other hardware. You need to prepare carefully for such a switch. The specific steps you need to take depend on the operating system you want to use inside the virtual machine. 

Note: After you create a physical disk using one or more partitions on a physical disk, you should never modify the partition tables by running fdisk or a similar utility in the guest operating system. 

Note: If you use fdisk or a similar utility on the host operating system to modify the partition table of the physical disk, you must recreate the virtual machine's physical disk. All files that were on the physical disk are lost when you modify the partition table. 

If you are adding a new physical disk, click Add to install the device. 

To remove an existing physical disk, select that disk, then click Remove. 

Click OK to save the configuration and close the virtual machine settings editor. 

For more information, see Advanced Disk Configuration: Setting the Virtual Device Node and Mode.

---

