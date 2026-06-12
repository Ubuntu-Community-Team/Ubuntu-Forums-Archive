---
title: "How do I specify a format in QEMU?"
date: 2015-12-31
forum: Virtualisation
---

### Post by Michael_Spohr on 2015-12-31
Terminal log: 

pizzadog@PizzaDog-desktop:~$ qemu-system-i386 -hda ubuntu.img -boot d -cdrom /home/pizzadog/Downloads/ubuntu-8.04.4-server-i386.iso -m 300
WARNING: Image format was not specified for 'ubuntu.img' and probing guessed raw.
         Automatically detecting the format is dangerous for raw images, write operations on block 0 will be restricted.
         Specify the 'raw' format explicitly to remove the restrictions.

I've been trying to get qemu to work for a while now, and I think I'm finally in the final stretch. I'm doing this from my raspberry pi with ubuntu-mate installed, and I'm able to boot the ISO, but I can't install anything as qemu wants me to specify that it's a raw format. The problem is that The only think I've learned about Ubuntu has been in the past 5 days. I googled around and couldn't get to work. How do I change the format to raw?

---

### Post by grahammechanical on 2015-12-31
If you open the file manager (called Files or Nautilus) and right click the ISO image and then select properties you will see that it is listed as raw CD image under Type. Other image files might have other designations. Such as Raw disk image.

That is the best I can come up with.

Regards

---

### Post by deadflowr on 2016-01-01
Moved to ***Virtualisation***

---

### Post by J_Me on 2016-01-01
You need to allocate disk space for qemu to use[br]1[/br] [br]1[/br] qemu-img create -f qcow2 theDiskSpace.img 1G[br]1[/br] [br]1[/br] This creates a one gig virtual hard drive

---

### Post by MAFoElffen on 2016-01-01
J_Me +1 ... with more of an an explanation of what he said.

You need to allocate a disk for your guest to install to previous to the install. When you do (as he gave aan excample of), then you can specify what format you want it to be. If not, and you tell it to install to a vDisk that does not exist (this will happen if you mistype where it is also...) it will allocate one in it's default image type, "raw".

From the Qemu Wiki, the valid image types for use with Qemu are:
> 
Image types:

raw - (default) the raw format is a plain binary image of the disc image, and is very portable. On filesystems that support sparse files, images in this format only use the space actually used by the data recorded in them.

cloop - Compressed Loop format, mainly used for reading Knoppix and similar live CD image formats

cow - copy-on-write format, supported for historical reasons only and not available to QEMU on Windows

qcow - the old QEMU copy-on-write format, supported for historical reasons and superseded by qcow2

qcow2 - QEMU copy-on-write format with a range of special features, including the ability to take multiple snapshots, smaller images on filesystems that don't support sparse files, optional AES encryption, and optional zlib compression

vmdk - VMware 3 & 4, or 6 image format, for exchanging images with that product

vdi - VirtualBox 1.1 compatible image format, for exchanging images with VirtualBox.

vhdx - Hyper-V compatible image format, for exchanging images with Hyper-V 2012 or later.

vpc - Hyper-V legacy image format, for exchanging images with Hyper-V 2008 / Virtual PC.


---

