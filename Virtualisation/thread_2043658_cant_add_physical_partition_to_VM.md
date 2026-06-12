---
title: "cant add physical partition to VM"
date: 2012-08-17
forum: Virtualisation
---

### Post by palloy on 2012-08-17
Lubuntu 12.04, Virtualbox 4.1.18r78361, Extension Pack 4.1.18r78361

I have Win 7 working in VirtualBox, but it is pretty pointless if I can't access my data, which is on a separate partition. So following instructions at [http://www.sysprobs.com/access-physical-disk-virtualbox-desktop-virtualization-software](http://www.sysprobs.com/access-physical-disk-virtualbox-desktop-virtualization-software) I ran 
```
sudo VBoxManage internalcommands createrawvmdk -filename /media/USB-SystemImages/VM-Win7/SATA-library.vmdk -rawdisk /dev/sda -partitions 7
RAW host disk access VMDK file /media/USB-SystemImages/VM-Win7/SATA-library.vmdk created successfully.
```In fact it gave me two files: SATA-library.vmdk and SATA-library-pt.vmdk
Then VirtualBox > Machine > Settings > Storage > Add Hard Disk > Choose Existing Disk > shows me my main Win7.vdi file and the two .vmdk files.
Selecting SATA-library.vmdk and clicking Open I get the error:[INDENT]Failed to open the hard disk /media/USB-SystemImages/VM-Win7/SATA-library.vmdk.
The medium '/media/USB-SystemImages/VM-Win7/SATA-library.vmdk' can't be used as the requested device type.
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Medium
Interface: IMedium {53f9cc0c-e0fd-40a5-a404-a7a5272082cd}
Callee: IVirtualBox {c28be65f-1a8f-43b4-81f1-eb60cb516e66}
[/INDENT]Being new to this, I have no idea what to do next.

---

### Post by marinara on 2012-08-19
try sharing the folder with windows 7 in the vm.

---

### Post by palloy on 2012-08-19
Not sure what you mean - "share" as in a Samba share?
One folder in SATA-Library (/dev/sda7) is already a Samba share, and Win7 cannot see that, although other PCs on the LAN can, and Win7 can see their shares. Both host and guest have computer-name=desktop . I don't know if that would cause a problem. I'll try renaming the guest to VMdesktop.

update: 
ah, that did make a difference. Now I can see host's shares and guest's shares, and sharing the drive /media/SATA-Library works too.

That seems to be a much better way of doing things. Is that what you are supposed to do?

---

### Post by marinara on 2012-08-19
really i'm not totally sure what you were trying to do, but you can share directories on the host with the guest

---

### Post by mc1100 on 2012-08-23
Add yourself to the disk and vboxusers groups.

```
sudo usermod -a -G disk,vboxusers yourlogin
```

Then logout/login for the changes to take effect.

Hope that helps.

Martin

---

