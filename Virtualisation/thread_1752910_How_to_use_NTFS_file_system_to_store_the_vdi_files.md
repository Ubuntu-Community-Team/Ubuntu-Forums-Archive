---
title: "How to use NTFS file system to store the vdi files"
date: 2011-05-08
forum: Virtualisation
---

### Post by kmkmahesh on 2011-05-08
I am new to Virtual Box

i required some help, i am using ubuntu 10.10, later i will upgrade to 11.04

i just want to know is it possible to store all the vdi files in a NTFS file system, because i have 3 operating systems in my PC

Windows XP, Windows 7 and Ubuntu 10.10

if the vdi files stored in a windows file system i can use them while i am in windows operating system also

i just installed a guest operating system in a NTFS file system, after a restart of the ubuntu i got the following errors
> pdmblkcache#0: The VM is missing a block device. Please make sure the source and target VMs have compatible storage configurations [ver=1 pass=final] (VERR_SSM_LOAD_CONFIG_MISMATCH).
and
> Result Code: NS_ERROR_FAILURE (0x80004005)Component: ConsoleInterface: IConsole {515e8e8d-f932-4d8e-9f32-79a52aead882}
so i deleted the virtual maching

so please suggest me how to use it

---

### Post by An Sanct on 2011-05-08
You shouldn't have deleted the virtual machine ....

There is the VM configuration at this location: 
```
/home/*$username*/.VirtualBox/VirtualBox.xml
```(obviously, change the user name to your)

inside, it says something like this (example from my VM)
```

<MachineEntry uuid="{313c8*.... GUID ....*f3d82}" src="/media/warehouse/VirtualBox/Machines/Maverick trident/Maverick trident.vbox"/>
```and inside this file, you find (example from my VM)
```
<HardDisk uuid="{09ca4*.... GUID ....*5ba8d2}" location="**Maverick trident.vdi**" format="VDI" type="Normal">
```Which tells VirtualBox where to search for the specific VDI file.

Conclusion: Yes, you can have the disk in a location, where Windows and Linux will see it, but be careful about the VirtualBox versions on the host software.

---

### Post by An Sanct on 2011-05-08
The good news is, that you can still recreate that Virtual Machine and assign the drive to it (see screenshot)

Do the same in Windows.

---

