---
title: "ubuntu virtual installation"
date: 2016-09-07
forum: Virtualisation
---

### Post by jebi on 2016-09-07
hi

is it possible to install ubuntu virtually in windows then copy the os to is another hd?

maybe using virtualbox or vmware?

thx

---

### Post by howefield on 2016-09-07
Thread moved to the "*Virtualisation*" forum, probably a better fit.

---

### Post by 1clue on 2016-09-07
The problem with this is drivers.

VMware and pretty much every other virtualization software doesn't give the VM the same hardware that's on the box. They emulate a common piece of hardware which works well in all target operating systems.

So long story short, you MIGHT be able to install but you will probably have slow screen resolution and possibly no network.  You'd have to fix that, probably offline.

Why not install directly to the other HD?

P.S. I have not tried this, but have installed many Ubuntu Server VMs as well as others.

---

### Post by 1clue on 2016-09-07
IMO it would be easier to just install on the raw hardware, but just to try it out, you'd do something like this after you have your VM up and running.

[LIST=1]
[*]Hook up your target hard drive.
[*]Format it using whatever formatting software you like.
[*]Create partitions on each as appropriate.
[*]Mount the partitions on /mnt
[LIST=1]
[*]sudo mount /dev/sdb2 /mnt
[*]sudo mkdir /mnt/boot
[*]sudo mount /dev/sdb1 /mnt/boot
[*]and so on until your current partition map is represented on your new disk.
[/LIST]

[*]Copy data over to the new drive
[LIST=1]
[*]sudo cp -rax / /mnt
[*]sudo cp -rax /boot /mnt/boot
[*]...
[/LIST]
[/LIST]

Once you've done that you'll have to edit /mnt/etc/fstab to target your new drive's partitions.  Keep in mind that when you try to boot onto the regular hard disk your drive letters will probably change, so /dev/sdb will probably be something like /dev/sda, but it might be something else.

You will not have a boot loader. So you'll need to boot off of the installer CD and follow readily available instructions on how to set one up.

You may also need to rename devices like network cards, that sort of thing in config files.

Once you have it going you'll need to do

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by SeijiSensei on 2016-09-07
I haven't tried to install to a secondary drive in a while, but can't you just boot the CD/DVD, point it at the secondary drive,  tell it to install Ubuntu there, then make that the boot drive?. Won't grub-install find any other existing OS images on both drives and add them to the startup menu during installation?

You might need to edit the BIOS to make the secondary drive the boot device, or open the box and swap the drives' data cables.  Windows might not like that though.  If it works without swapping the cables, I'd go with that configuration.

On multi-boot systems I generally prefer to create a separate 512 MB /boot partition on the system drive that stands outside any of the individual OS images.  So my standard installations have that small boot partition, a swap partition, one or more partitions containing operating systems, and maybe an NTFS-formatted partition shared across Windows and Linux.  On laptops swap should be at least as large as installed memory; twice installed memory or 4 GB, whichever is larger, is a good size.  On older MBR drives (see 1clue's post above :)), create the third partition as "extended" and have it fill the remainder of the drive.  Then you can create multiple partitions within it.

After you have customized the installation to your liking, you can look into tools that can help convert it into a bootable drive like [Respin](https://github.com/ch1x0r/LinuxRespin/raw/master/ubuntu/respin_1.1.0-1_all.deb).

---

### Post by ian-weisser on 2016-09-07
Another method is to simply keep notes on your VM customizations, making your later bare metal installation easy and fast.

---

