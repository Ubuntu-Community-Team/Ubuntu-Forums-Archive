---
title: "Share an NTFS Partition"
date: 2010-01-15
forum: Virtualisation
---

### Post by nerdtron on 2010-01-15
I'm currently using Sun Virtual OSE and I installed Windows XP SP2. Guest additions are also installed and my home folder is already shared to the virtual machine (I can read and write to it with no problems). But how do I share a Windows NTFS partition to the guest XP? I have two NTFS partitions that I want to access inside the virtual machine. Help please. I already installed Samba on Ubuntu but I can't figure out how to start sharing my NTFS partitions..

---

### Post by mk1w86 on 2010-01-15
Can't you mount the NTFS partitions in Ubuntu and share them to the VM the same way you have shared your home folder?  Samba should not be required, just use the Shared Folder option in VirtualBox. :D

---

### Post by kimberlite on 2010-01-15
At VirtualBox OSE you can go to SETTINGS than SHARED FOLDERS than click on + icon (Add new shared folder) and add your mounted NTFS partition that usually mounted at /media/ folder.

---

### Post by John Bean on 2010-01-15
> **mk1w86 said:**
> Can't you mount the NTFS partitions in Ubuntu and share them to the VM the same way you have shared your home folder?  Samba should not be required, just use the Shared Folder option in VirtualBox. :D

Exactly what I was about to write, since that's how I provide physical NTFS access to my XP guest.

---

### Post by nerdtron on 2010-01-15
> **mk1w86 said:**
> Can't you mount the NTFS partitions in Ubuntu and share them to the VM the same way you have shared your home folder?  Samba should not be required, just use the Shared Folder option in VirtualBox. :D

Yes I tried it like how I shared the home folder. But whenever I choose the NTFS partition, the "OK" button is grayed out...I can't click the OK button.

---

### Post by mk1w86 on 2010-01-15
Where is the NTFS partition mounted?

---

### Post by nerdtron on 2010-01-15
> **mk1w86 said:**
> Where is the NTFS partition mounted?

/media/All Stuffs

I installed the NTFS configuration tool to automatically mount it upon startup.

---

### Post by nerdtron on 2010-01-15
Oh...I figured it out. The mount point isn't the problem /media/all stuffs
The OK button is grayed out when I have an invalid folder name for the shared drive (I changed the space to an underscore and it let me choose the OK button).. Thanks to you're replies!:popcorn:

---

### Post by wightghost on 2010-03-24
> **nerdtron said:**
> Oh...I figured it out. The mount point isn't the problem /media/all stuffs
The OK button is grayed out when I have an invalid folder name for the shared drive (I changed the space to an underscore and it let me choose the OK button).. Thanks to you're replies!:popcorn:

I've been trying for a while to get shared folders to work in my XP guest. I had the same problem (OK greyed out). This worked a treat. Thanks!

---

