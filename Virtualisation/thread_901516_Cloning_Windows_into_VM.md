---
title: "Cloning Windows into VM"
date: 2008-08-26
forum: Virtualisation
---

### Post by dudude on 2008-08-26
What I want to do is clone an existing install of Windows from one computer to a virtual machine inside of Virtualbox or VMware on another computer.

My question is what I should do about the cloning of Windows.

I do not know if I need to copy the entire disk, or just the partition that contains Windows. I don't know if the MBR is important to the cloning of Windows or not.

I already know how to deal with the hardware differences between the physical machine and the virtual one, and I am already aware of the legal restrictions of having only one existing install of Windows.

---

### Post by HermanAB on 2008-08-26
VMware has a special tool to do that.  However, some Googling will find howto guides for doing it the hard way yourself.  Basically, you first need to install generic SCSI disk, ethernet and display drivers, then copy the whole physical disk to a virtual disk using dd.

---

### Post by dudude on 2008-08-26
So I'm assuming that by saying clone the entire disk you mean to clone the entire disk:)

Also, should there be any reconfiguration after the the disk is copied? 
(I don't mean hardware reconfiguration, I just mean reconfiguration of partition tables or something.)

Edit: I've read multiple guides on various sites doing things similar to this, but many of them use Norton Ghost, and I don't know exactly how Ghost backs up disks/partitions. It would be nice to use something like Clonezilla to do the same job, but with FOSS programs.

---

### Post by Darendo on 2008-09-02
I cloned my Windows XP Pro machine from an IBM A31 notebook to VMware without issue. First, I removed all hardware-specific drivers (i.e. video, hdd, network, wireless, etc.) Next, I used Ghost to backup my HDD. Then I used a utility (bundled with Ghost if I recall correctly) to convert that backup image to a VMware virtual disk image. Then I just created a VM session and pointed the HDD to the converted image. On first boot, Windows installed the appropriate drivers for everything except video. I installed the VMware tools, restarted and Windows had the correct video drivers.

---

### Post by lazyart on 2008-09-02
[VMware Converter]("http://www.vmware.com/products/converter/").

---

