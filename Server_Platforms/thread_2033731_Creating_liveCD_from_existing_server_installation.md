---
title: "Creating liveCD from existing server installation"
date: 2012-07-26
forum: Server Platforms
---

### Post by jickerson on 2012-07-26
I would like to make a bootable live cd that is the exact same  environment as the existing install on the hard drive. I know for Ubuntu  desktop you can use remastersys, but it requires a GUI and won't run on  the server edition. I've also run across a method that involves chroot  and using apt-get to add additional packages that you want to include,  but there are some things that I've done to the install that I wouldn't  know how to do using this method (like installing the enthought  distribution of python from source using an elaborate .sh file). Are there any options, similar to remastersys, that will just take the  existing install and build it into a livecd iso image? If it helps, I  don't need to have the option to install from the cd, just boot into it  so it will start running the processes I have set to run at startup.

---

### Post by Cheesemill on 2012-07-26
It would be much easier to use an external hard drive and use something like Clonezilla to create an image.

---

### Post by BkkBonanza on 2012-07-26
You may find this helpful, though it seems to be for the desktop it could likely help with details of how the live cds are made and be useful for the server version.

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by jickerson on 2012-07-26
Thank you both for your advice. As far as the link in the second reply, that is actually what i was referring to by the "chroot method". I'm not sure how well this would work when i had to install packages using .sh scripts and not just apt-get (i'm not that experienced in linux).

I can't really do the external hard drive option because the end goal is to either boot a cluster of computers to do computations by either booting via a cd or pxe.

---

### Post by BkkBonanza on 2012-07-26
I would think that the PXE boot would be the way to go. Have you looked at the Ubuntu PXE boot HowTo as well. It seems like you could take your existing root filesystem and make a PXE boot server fairly painlessly.

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

I don't think that installing via a shell script would make any difference to the chroot method. It probably has more bearing on how easily you can remove an installed software. The package manager is quite good at cleaning up things when you remove something but it is usually harder with a scripted install as often they don't provide a way to undo everything. Certainly stuff installed via script won't be removable via the package manager but the actual installed files shouldn't break anything about the chroot working or not.

I think if you took your current server root fs and copied it into the suggested nfsroot for PXE booting it would work regardless of how files were originally installed. You probably want to make such a copy before you installed additional server packages & config to do PXE booting though as you likely wouldn't want the clients to boot with PXE components active. ie. replicate the current filesystem, install PXE server stuff, mount that copied filesystem as nfsroot for the clients to boot off.

If I were doing that I'd probably use dd to make an image file of the filesystem you intend clients to use. Then use "mount -t loop"  to mount that fixed image as your nfsroot. Or something like that anyway.

---

