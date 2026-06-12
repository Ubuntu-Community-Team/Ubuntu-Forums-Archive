---
title: "Auto VMDK mounting/lock issues"
date: 2008-01-17
forum: Virtualisation
---

### Post by Izza on 2008-01-17
Wondering if it's possible to automount a VMDK without leaving a term window open and running, and to have access to it through nautilus while running off of it in VMware? Right now it seems to be either/or (lock issues).

Also, is there perhaps a graphical utility for mounting VMware drive images under linux? Having to use console commands every time is irritating.

---

### Post by fjgaude on 2008-01-17
VMware Server has a GUI for mounting images. Or do you mean something else?

---

### Post by Izza on 2008-01-18
Basically I'd like access to the root of my virtual machine's drive, through nautilus, while my virtual machine is running. Just wondering how I would go about doing that, in any fashion, though preferably using a GUI utility of some kind or another.

---

### Post by fjgaude on 2008-01-18
Gosh, if you are running VMware Server, the free one, to do what you wish would require going across filesystems, Linux ext3 to Windows NTFS, without the use of Samba (smb). Somehow ntfs-3g would come into play. I've never thought of wishing to do what you want. I do think it is possible.

Maybe others here will respond.

---

### Post by Izza on 2008-01-18
Well, I can mount the vmware drive, and the file becomes locked... I can load the virtual machine... and the file becomes locked.

I *think* it's as simple as preventing one or the other from having exclusive access to the file. Most likely mounting it first without the lock, then loading the VM.

Is it even possible to prevent locking of the file when mounting?

I'm using the method described this guide:
[http://www.ubuntugeek.com/howto-mount-ntfs-vmware-virtual-disk-image-vmdk-readwrite.html]("http://www.ubuntugeek.com/howto-mount-ntfs-vmware-virtual-disk-image-vmdk-readwrite.html")

:(

---

### Post by fjgaude on 2008-01-18
Well, I've looked at where I have my VMware winXP vm. I see that there are lock files for reading and writing.

How do you mount the package that contains the VMDK files and all the other files associated with a vm package?

I load my vm package with the VMware console supplied by VMware, the free kind, and not the Beta 2 kind.

---

### Post by Izza on 2008-01-18
> **Izza said:**
> 
I'm using the method described this guide:
[http://www.ubuntugeek.com/howto-mount-ntfs-vmware-virtual-disk-image-vmdk-readwrite.html]("http://www.ubuntugeek.com/howto-mount-ntfs-vmware-virtual-disk-image-vmdk-readwrite.html")
:(.

---

### Post by fjgaude on 2008-01-18
Sorry, the site you posted shows only a blank white screen. Tried three times with the same results.

Pray tell, what is wrong with using the Console that comes witn VMware?

---

### Post by Izza on 2008-01-18
I'm using the free vmware server.

I can load the virtual machine fine, I can mount the drive image and browse it with nautilus just fine. I cannot, however, do both at once.

---

### Post by fjgaude on 2008-01-18
Gosh, I seem to have trouble understanding what you want to do. Lock or mount but not both at the same time?

Okay, maybe your folder that contains the VMX files are root permission. They can be login user if you wish by the chown command:

```
sudo chown -R login:login /foldername
```

where login is your login name, e.g. Izza.

---

### Post by Izza on 2008-01-19
The VMDK file. When I mount it for viewing under Nautilus, I cannot simultaneously boot that same VMDK file with VMWare. If I am running the VMDK file in VMWare I cannot mount it under Nautilus.

What I need to be able to do is have the VMDK file running in VMWare, and mounted under Nautilus, at the same time.

When I try to do this, regardless of which is done first, I get an error stating a lock cannot be obtained on the file.

---

### Post by fjgaude on 2008-01-19
If you look at the contains of the vmware package that is installed I believe the lock files are auto created when a vmdk is loaded. It's that simple. I don't think you can do what you wish.

---

