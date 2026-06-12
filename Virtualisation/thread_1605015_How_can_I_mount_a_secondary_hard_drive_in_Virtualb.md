---
title: "How can I mount a secondary hard drive in Virtualbox?"
date: 2010-10-24
forum: Virtualisation
---

### Post by diablo75 on 2010-10-24
It's not actually a secondary drive so much as just another NTFS partition that contains Windows.  I don't want to boot the partition, just be able to access from within Virtualbox.  I sustained a horrible file system failure on that partition and I need to use data recovery software (that only runs on a full install of Windows) to scan the partition in an attempt to recover lost data.  Any chance this is possible or will I have to take the drive out and walk it over to a Windows box to do this?

---

### Post by Irregular Joe on 2010-10-25
I have not attempted this, but found an article that may be useful:  [http://www.rajatarya.com/website/taming-windows-virtualbox-vm](http://www.rajatarya.com/website/taming-windows-virtualbox-vm)

Hope this helps!  Post your progress, so others can learn.

---

### Post by tosk on 2010-10-25
It's possible. You need to create a VMDK that points to the physical partition. Then just attach that VMDK to the VM and start it up.

---

### Post by JustinR on 2010-10-25
> **tosk said:**
> It's possible. You need to create a VMDK that points to the physical partition. Then just attach that VMDK to the VM and start it up.

Hi,

go to System > Administration > Users and Groups. Click 'Manage Groups'. Find the group labeled 'Disk' and click 'Properties'. Add yourself to the list and restart your computer.

Then find what device your second HDD is (eg. /dev/sdb - not the partition numbers like /dev/sdb1, just the device as a whole). You can do this with something like Disk Utility in the Administration Menu.

Depending on the VirtualBox software you have the 'OSE' or 'PUEL' the command will be this:
OSE:
```

vboxmanage internalcommands createrawvmdk -filename FILE_PATH -rawdisk DEVICE_NAME
```

PUEL:
```

VBoxManage internalcommands createrawvmdk -filename FILE_PATH -rawdisk DEVICE_NAME
```

Then mount that VMDK file in VirtualBox.

---

