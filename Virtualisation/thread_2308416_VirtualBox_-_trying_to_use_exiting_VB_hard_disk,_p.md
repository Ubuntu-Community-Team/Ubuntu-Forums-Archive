---
title: "VirtualBox - trying to use exiting VB hard disk, permission error"
date: 2016-01-02
forum: Virtualisation
---

### Post by idee on 2016-01-02
I have a fresh installation of Lubuntu 15-10.  I have installed VirtualBox.  I am trying to access a previous version of a VB hard disk file saved to a saved drive.  The error seems to be permissions.  The folder permissions from the old distro are root/root.  How do I change that to my current user/users?



```
 Failed to open the disk image file /local/VirtualBox/VirtualBox VMs/XP/XP.vdi.


Permission problem accessing the file for the medium '/local/VirtualBox/VirtualBox VMs/XP/XP.vdi' (VERR_ACCESS_DENIED).
   
[TABLE]
[TR]
[TD] Result Code:[/TD]
[TD] VBOX_E_FILE_ERROR (0x80BB0004)[/TD]
[/TR]
[TR]
[TD] Component:[/TD]
[TD] MediumWrap[/TD]
[/TR]
[TR]
[TD] Interface:[/TD]
[TD] IMedium {4afe423b-43e0-e9d0-82e8-ceb307940dda}[/TD]
[/TR]
[TR]
[TD] Callee:[/TD]
[TD] IVirtualBox {0169423f-46b4-cde9-91af-1e9d5b6cd945}
[/TD]
[/TR]
[TR]
[TD] Callee RC:[/TD]
[TD] VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)
[/TD]
[/TR]
[/TABLE]

```

---

### Post by Elishasmantle on 2016-01-03
Hello,

If possible you can do an export first of the VM: File > Virtual Media Manager > Copy
Then import the vm on the box you are using. I think this is the safer way to do it in case the image is corrupt. Plus when reimporting it lets VB handles all the needed things for importing properly under whatever profile you are logged under.
Or try : 
sudo chown -R username:groupname directory
if you use:
sudo chown -R username directory it will change the ownership to the desired user and change the group name to the default group of that user.

elishasmantle

---

### Post by idee on 2016-01-03
Thanks.  So I open the VMM but it is empty.  How do I direct it to look at the file? 
 Located at /local/VirtualBox/VirtualBox VMs/

Taking another chance, I was able to copy the old files into the .VB folder.  When opening VMM it does not show up in the list.  I would really like to get this running.

Also, did an import of an existing file.  It found it, but with the following errors:

```
Failed to open the disk image file /local/VirtualBox/VirtualBox VMs/XP/XP.vdi.

The medium '/local/VirtualBox/VirtualBox VMs/XP/XP.vdi' can't be used as the requested device type.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MediumWrap
Interface: IMedium {4afe423b-43e0-e9d0-82e8-ceb307940dda}
Callee: IVirtualBox {0169423f-46b4-cde9-91af-1e9d5b6cd945}
Callee RC: VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)
```

---

### Post by SeijiSensei on 2016-01-03
Have you tried adding it from the VirtualBox Manager application with Machine > Add?

---

### Post by idee on 2016-01-03
> **SeijiSensei said:**
> Have you tried adding it from the VirtualBox Manager application with Machine > Add?

Yes, that is what the error message above is from.  thoughts?

---

### Post by SeijiSensei on 2016-01-04
I searched Google for "can't be used as the requested device type" and found a number of postings.  One person's problem was resolved by adding himself to the "vboxusers" and "disks" groups:  [http://ubuntuforums.org/showthread.php?t=1914382&p=12191489&viewfull=1#post12191489](http://ubuntuforums.org/showthread.php?t=1914382&p=12191489&viewfull=1#post12191489)

Have you tried asking at [https://forums.virtualbox.org/](https://forums.virtualbox.org/)

---

