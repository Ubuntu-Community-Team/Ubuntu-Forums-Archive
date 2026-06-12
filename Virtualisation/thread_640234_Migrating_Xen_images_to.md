---
title: "Migrating Xen images to ????"
date: 2007-12-14
forum: Virtualisation
---

### Post by xurizaemon on 2007-12-14
We develop and host principally on Xen, and are very happy with it. In particular it offers us a broader range of support from hosting companies.

I'd like to be able to take Xen images "on the road" on an OSX laptop. Xen doesn't run on OSX, so I have to be able to get these images up and running in one of the following:
* Parallels
* Q (Qemu on OSX)
* VirtualBox
* VMWare Fusion

My main priority is ease of migrating an existing image onto the laptop. I've hit a bit of a wall here; can't see how any of these will easily import a Xen file-based image (which I'm sure is my lack of knowledge, because they all are capable of importing SOME existing disk images).

VMWare and Parallels look like they have nicer desktop integration with OSX, but really all I want is decent performance for a VM to run in console mode.

What do I need to do to clone a Xen file-based image to one of these virtualisation softwares?

Here's my install process for a random image (note that it's an old one, though)

```
dd if=/dev/zero of=vm1/swap bs=1024k count=256
dd if=/dev/zero of=vm1/root bs=1024k count=4096
mkswap vm1/swap
mkfs.ext3 vm1/root
mount -o loop /vm1 /media/target
sudo debootstrap --arch i386 dapper /media/target http://nz.archive.ubuntu.com/ubuntu
```

You know the drill. It's just a regular disk file, formatted as ext3. How can it be hard to migrate this to VMWare or Parallels?? Am I missing some obvious tactic?

(In my defense, we've just had a baby. I think I've dropped about 20 IQ points.)

---

### Post by coshx on 2008-01-08
The problem with converting from a Xen image to a virtual machine image is that the Xen image is not bootable (it doesn't contain an MBR or a bootloader).

With this in mind, I believe the basic steps are:
[LIST=1]
[*]create a hard disk image
[*]partition this image, making sure that the partition for the root filesystem is large enough for your xen image
[*]copy the xen-domU kernel into the boot partition, as well as the necessary bootloader files (which you may have to edit)
[*]mount your xen image and edit /etc/fstab according to your new partition scheme
[*]copy the xen image into the root partition
[*]install a bootloader (e.g., grub) onto the image
[*]convert the image into one suitable for the virtual machine, for example
```

  qemu-img convert hda.raw -O qcow2 hda.qcow2

```
[/LIST]

I've been trying to do this for the past couple of days, however, and am having trouble both partitioning an image file correctly, as well as installing grub onto the image.

If you can figure out how to do this, or find an easier way, I'd love to see the howto.

---

### Post by xurizaemon on 2008-01-08
I worked out an alternate approach, but haven't experimented with it too much yet. 

(Because Xen works fine for me, I keep shelving the experiments with VMWare etc.)

[LIST=1]
[*]In the alternate VM tech (eg VMWare), install a basic system. As minimal as possible.
[*]Copy files wholesale from your existing Xen VM over the files on the new image
[I]You could do this by booting them both at once and using rsync -zvra from one to the other, or by mounting both the disk images (if your host system permits mounting both).
[/I][*]Make tweaks, eg adjust bootloader as suggested by coshx.
[/LIST]

---

