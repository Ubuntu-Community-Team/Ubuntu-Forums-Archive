---
title: "Booting Ubuntu from within Windows"
date: 2010-09-18
forum: Virtualisation
---

### Post by todlangweilig on 2010-09-18
I've been wondering about this for quite some time, but haven't been able to find an exact solution yet. I would like to be able to boot my physical Ubuntu partition from within Windows, without having to create any virtual machines that are saved in a file. I would like to be able to get to my Ubuntu programs and files from within Widows without having to worry about maintaining a virtual machine Ubuntu and a physical Ubuntu. Any changes made to Ubuntu while being run in Windows would be saved back to the hard drive just as if I was running it natively. I don't want to virtualize Windows, because I'm using USB hardware devices, and I'm having troubles getting them working in a Windows virtual machine. So the next best thing would be to create a physical Windows partition where the hardware will work "out of the box", and then be able to boot Ubuntu within Windows, since I would be using Ubuntu within Windows for non-graphics-intensive software only.

I did some googling and the closest thing I found was QEMU. Would QEMU be able to do this?

---

### Post by uclugLee on 2010-09-18
Without virtualization I don't know if you are going to be able to boot one os while inside another os.  I personally use Wubi at work and it's been great.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by LightningCrash on 2010-09-18
Use VirtualBox

[http://www.virtualbox.org/manual/ch09.html#rawdisk](http://www.virtualbox.org/manual/ch09.html#rawdisk)

---

### Post by wilee-nilee on 2010-09-18
+1 virtualbox ask us about getting the USB setup it is easy once you know how.

You could have a shared ntfs partition, but this doesn't sound like it is what your looking for.

---

### Post by todlangweilig on 2010-09-19
This seems to be exactly what I'm looking for. Since the host OS would be windows, do I need to run the commands such as "VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk -rawdisk \PhysicalDrive0 -partitions 1,5" from the shell in windows? If I understand this correct, this creates a vmdk image file that points to certain partitions on my hard drive?

If someone would like to help debug my USB problems when using Ubuntu as the host and Windows 7 as the guest, I have a thread here, [http://ubuntuforums.org/showthread.php?p=9857500](http://ubuntuforums.org/showthread.php?p=9857500)

I actually have a shared ext3 partition. I previously (back when I had windows 7 physically installed) used ext2 IFS to allow Windows 7 to access the partition. But I hope I'll be able to access my shared files when I create the raw disk thing mentioned above. I'll give it access to the Ubuntu root file system and to my shared partition.

---

### Post by LightningCrash on 2010-09-19
> **todlangweilig said:**
> This seems to be exactly what I'm looking for. Since the host OS would be windows, do I need to run the commands such as "VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk -rawdisk \PhysicalDrive0 -partitions 1,5" from the shell in windows? If I understand this correct, this creates a vmdk image file that points to certain partitions on my hard drive?

yes. Then you'll add the VMDK to a VirtualBox VM and fire it up.

---

