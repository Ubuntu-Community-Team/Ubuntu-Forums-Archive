---
title: "Windows KVM guest network and/or disk problems"
date: 2010-10-06
forum: Virtualisation
---

### Post by OlegVekhov on 2010-10-06
Hello! I have Intel Dual Xeon E3110 8GB RAM Server with ubuntu 10.04 installed with Intel hardware SATA RAID 2x750 gb mirrored

I've installed windows 2003 server R2, then tried Windows 2008 server R2, with the same results:

KVM NIC are bridged.

Trying to copy files from external/to external Windows machine from Windows Server/to Windows Server guest. After 1-5 minutes of file operation windows machine states me that "The specified network resource no longer available".

Also I've noticed that write performance in Windows VM is very poor, about 4-5 MB/s max. Read are 30 MB/s.

Windows Guest has two disks, first is RAW image for windows system, second is RAW LVM Partition, which is used (my plans, never worked fine:))
as file server storage.

I've do these things to test:
1. Disabled RAID and start Ubuntu from one disk
2. Using Virtio for disk and nic, and combinations (virtio disk + e1000 nic, ide disk + rtl8139 nic), etc.
3. Tried to do memory testing from GRUB - all ok
4. Tried to turn off KVM write caching, Virtio SCSI write caching in windows.

Nothing above helps.

Also, there are no errors in dmesg, syslog, daemon.log. And Ubuntu runs fine on disks, and read/write performance is pretty good.

---

### Post by slooksterpsv on 2010-10-08
Did you allocate the files for the disks when you created the VM, cause than can cause performance with network file operations as well as speed of the VM - due to the host having to continually resize whenever new data is sent. If it already is, let me know.

---

### Post by OlegVekhov on 2010-10-12
No, the image was pre-allocated. The other disk is LVM partition, so I don't think it should be pre-allocated.

So, the most annoying problem is samba data transfer disconnects... I can live with slow disk speed - samba is the most wanted! :)

Thanks!

---

