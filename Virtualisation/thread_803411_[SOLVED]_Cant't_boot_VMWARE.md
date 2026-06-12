---
title: "[SOLVED] Cant't boot VMWARE"
date: 2008-05-22
forum: Virtualisation
---

### Post by ruialexbarbosa on 2008-05-22
Hi,

I'm running VMWARE Server Console, 1.0.4 build-56528.

I got some problem with screen resolution, so tried pressing that REVERT button (revert to snapshot), and now it's just in SUSPEND mode and will not boot. I try opening it, screen goes black and then reverts to the COMMANDS/DEVICES screen. It shows the option RESUME THIS VIRTUAL MACHINE, but I can't access the system. I need at least to get some files from there...

Help...:confused:

---

### Post by ruialexbarbosa on 2008-05-22
Please... I'm in pain here...

---

### Post by bradmkjr on 2008-05-22
really simple solution:

attach the VMDK hard drive image file to another virtual machine, boot and copy files off.

howto: goto a different virtual machine, choose the virtual machine options, add new hardware, add a hard drive, use a pre existing image, and browse for the image in the problematic vm. If it gives you any issues about the drive inuse, you may need to look into deleteing the temporary files in the broken vm, these are the files which VMware creates to store temp data, and memory backups etc. Be careful deleting files in that directory, as there can be numerous ones, the better idea may be if you have free space, copy just the VMDK files to a new location, away from the vmx and other temp files.


Hope the makes sense,
Bradford Knowlton
[http://x86v.com](http://x86v.com)

---

### Post by ruialexbarbosa on 2008-05-24
thanks,

guess that's what I'll do :guitar:

---

### Post by diablo75 on 2008-05-25
You really should browse to /var/lib/vmware-server (close to that pathname anyway) look inside the Virtual Machines folder contained within, and check to see if there are any files with the word READLOCK or WRITELOCK appended to the filename.  Those files can be deleted if you encounter them...

---

### Post by ruialexbarbosa on 2008-05-26
I have .log .vmsd and .vmx files in that folder.

---

### Post by fjgaude on 2008-05-26
Don't delete the folder, delete the locked files, two or three of them. You likely have to be root to do it.

---

### Post by ruialexbarbosa on 2008-05-26
But I don't think I have locked files in there... Only the ones I wrote above... :confused:

---

### Post by ruialexbarbosa on 2008-05-28
> **bradmkjr said:**
> really simple solution:

attach the VMDK hard drive image file to another virtual machine, boot and copy files off.

howto: goto a different virtual machine, choose the virtual machine options, add new hardware, add a hard drive, use a pre existing image, and browse for the image in the problematic vm. If it gives you any issues about the drive inuse, you may need to look into deleteing the temporary files in the broken vm, these are the files which VMware creates to store temp data, and memory backups etc. Be careful deleting files in that directory, as there can be numerous ones, the better idea may be if you have free space, copy just the VMDK files to a new location, away from the vmx and other temp files.


Hope the makes sense,
Bradford Knowlton
[http://x86v.com](http://x86v.com)

SORTED! Copied the files across to a new virtual machine.

Thanks

---

