---
title: "help getting TRIM to work on ssd"
date: 2017-12-28
forum: Virtualisation
---

### Post by cnbiz850 on 2017-12-28
I have Xubuntu 16.04 installed with VirtualBox on a MacBook Pro host. I set the hard disk type to be SSD on VirtualBox. But recently I found TRIM doesn't seem to work.  For instance, the following command returns nothing:

```
$ sudo hdparm -I /dev/sda | grep TRIM
```

For the following command, I get an error:

```
$ sudo fstrim -v /
fstrim: /: the discard operation is not supported

```

With fdisk:

```
$ sudo fdisk -l
Disk /dev/sda: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xfffe1e7c

Device     Boot Start      End  Sectors Size Id Type
/dev/sda1  *     2048 41943039 41940992  20G 83 Linux
```

Would anyone shed some light please?

---

### Post by KillerKelvUK on 2017-12-28
Hey, your question intrigued me to have a little google around...

I don't use VirtualBox but I saw this StackExchange thread talking about TRIM in VM's ([https://superuser.com/questions/646559/virtualbox-and-ssds-trim-command-support](https://superuser.com/questions/646559/virtualbox-and-ssds-trim-command-support)).  I use KVM for my guests and am now at a bare minimum as I've switched to containers for linux guests.  However I found an article discussing the same TRIM topic for KVM guests ([https://superuser.com/questions/646559/virtualbox-and-ssds-trim-command-support](https://superuser.com/questions/646559/virtualbox-and-ssds-trim-command-support)) which goes the extra mile of showing you how to validate the guest OS is recognising an SSD supporting TRIM and DISCARD functions which I believe are the additional steps the StackExchange thread doesn't include.

---

### Post by QIII on 2017-12-28
The best way I found to "trim" a guest on an SSD is to initially set it up as a dynamic virtual disk, use the VBox tools to shrink the virtual disk file periodically (it will grow again as you use it later), and then trim the entire SSD from the host.

This makes sure that the host and the SSD's controller are in coordination with regard to which erasure blocks have been trimmed.

---

### Post by cnbiz850 on 2017-12-28
> **KillerKelvUK said:**
> Hey, your question intrigued me to have a little google around...

I don't use VirtualBox but I saw this StackExchange thread talking about TRIM in VM's ([https://superuser.com/questions/646559/virtualbox-and-ssds-trim-command-support](https://superuser.com/questions/646559/virtualbox-and-ssds-trim-command-support)).  I use KVM for my guests and am now at a bare minimum as I've switched to containers for linux guests.  However I found an article discussing the same TRIM topic for KVM guests ([https://superuser.com/questions/646559/virtualbox-and-ssds-trim-command-support](https://superuser.com/questions/646559/virtualbox-and-ssds-trim-command-support)) which goes the extra mile of showing you how to validate the guest OS is recognising an SSD supporting TRIM and DISCARD functions which I believe are the additional steps the StackExchange thread doesn't include.

Thanks for the reference.

Indeed, the following command ensured the guest to trim the ssd.

```
 VBoxManage storageattach "GuestOsMachineName" --storagectl "SATA" --port 1 --device 0 --nonrotational on --discard on --medium "C:\path\to\file.vdi" --type hdd
```

---

### Post by cnbiz850 on 2017-12-28
> **cnbiz850 said:**
> Thanks for the reference.

Indeed, the following command ensured the guest to trim the ssd.

```
 VBoxManage storageattach "GuestOsMachineName" --storagectl "SATA" --port 1 --device 0 --nonrotational on --discard on --medium "C:\path\to\file.vdi" --type hdd
```

But this command used on a Windows 10 guest caused a huge reaction between the guest and the Mac host after optimization was done on the disk in Windows 10. The guest stopped responding, and the host had a "kernel task" process taking about 100% CPU. Running for 20 minutes had no sign of progress. I couldn't even "power off" the VM, so I had to do "kill -9". I guess this is not quite proper for Windows guest. Or maybe the real defrag was taking place and would take long time, which I don't need at all.

But for Xubuntu guest, it worked well.

---

