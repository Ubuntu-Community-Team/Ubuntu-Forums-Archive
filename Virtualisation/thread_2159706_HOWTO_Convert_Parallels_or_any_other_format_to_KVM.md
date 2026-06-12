---
title: "HOWTO: Convert Parallels or any other format to KVM from inside."
date: 2013-07-04
forum: Virtualisation
---

### Post by 1clue on 2013-07-04
Hi,

I've been having trouble converting Parallels images to KVM.  After having days of email help from Fam Zheng @ RedHat, I came across a simple solution that should work on Parallels, VMware, any other virtualization scheme, and on real hardware.

Note that Fam is much better versed at this sort of thing than I am, and anything stupid in this document is my fault, not his.

There seems to be a problem with my images, or maybe with the Parallels converter in qemu-img is old.  The images were getting some blank space in the file at the beginning, and as such they weren't recognized by KVM.  Fam managed to  use dd to delete the inappropriately blank part and boot it, but the best I got was a grub prompt and a disk with a bunch of missing files.

I'm going straight for the way I got it to work, not going into stuff we tried.

Image references:
[LIST=1]
[*]Source host: The computer which is hosting virtual machines in the old format.
[*]Destination host: The machine which is hosting virtualization new KVM/Qemu format.
[*]Converter: A Linux guest on the source host which is not being converted, which is used to convert the images.  This is described in the next list.
[*]Source target: The VM to be converted as it sits on the source host.
[*]Destination target: The converted VM on the destination host.
[/LIST]

Keep in mind that the hardware is not being converted.  All we really care about is the disks.  Each virtualization scheme has its own hardware implementation.

Converter specs:
[LIST=1]
[*]A Linux installation on the original virtualization scheme (Parallels Mac in my case) which is NOT being converted.
[*]It could contain qemu-utils, or whatever package qemu-img is in for that distro, but this is only needed if you do not prefer 'raw'.
[*]The converter needs access to storage which can hold the destination target disk image.  This can be a local disk or a shared disk.  Note that if you convert to 'raw' from a resizable disk, then the raw image will be the maximum size of the disk.
[*]This example has a root on /dev/sda (which is much too small since it's a reasonable VM) and a second virtual disk formatted as XFS and mounted on /xfs.
[/LIST]

So if you're using real hardware and converting it to KVM, you need a Linux box, and the hard disk of the box to be converted, and the cable(s) to connect it.  OR you need a virtualized Linux box and a way to connect the source target's physical disk to the VM.  This Linux box could be the destination host, and you could just leave the disk attached.

Do this on the guest to be converted:
[LIST=1]
[*]Log into the guest which is to be converted.  We'll call it the **original target**.
[*]Clean it up if you can, empty trash on the target guest, delete all unnecessary files.
[*]Shut the machine down completely, and power it off.
[*]Close the image.  You will be able to power this up again afterward, the image won't be touched.
[/LIST]

Now on the converter:
[LIST=1]
[*]Starting with the converter powered off.
[*]Attach the source target disk to the converter as an existing disk image.  Sorry no details here, it will vary based on your virtualization engine.
[*]Boot the converter image.
[*]When you get logged in, find the disk in question.  If you're using Parallels and your Linux image has one 'normal' disk for / and one extra disk added just for these conversions, then your converted image will probably be something like /dev/sdc.
[*]DO NOT MOUNT THE DISK!
[*]**cd /path/to/big/storage**[*]Type **fdisk -l /dev/sdc** to make sure the partition table looks like you expect it to.
[*]**md5sum /dev/sdc > *computer-name*-sdb.md5sum** where *computer-name* is the hostname of the destination target.
[*]**cp /dev/sdc *computer-name*-root.raw**  -- This is going to take awhile depending on how big your disk image is.
[*]The above command is for raw, you could also use qemu-img to convert from raw to whatever other format you want.  You could also use dd if you like, instead of cp, for the raw format.
[*]**md5sum *computer-name*-root.raw** -- Check the image sum.
[*]Compare the two .md5sum files to verify that the images are identical. (this won't work if you're not using raw)
[*]Copy the *computer-name*-root.raw image to the destination host, in an appropriate directory.  I used **scp**.
[/LIST]

On the destination target:
[LIST=1]
[*]Create a new destination target VM which has hardware specs similar to that of the source target.  I used virt-manager.
[*]Attach the newly transferred raw image.
[*]Boot.
[/LIST]

That should be it.  If it comes up normally, then you did it right.

Make sure you power down the converter and remove the disk so you can use the source host if necessary, and so you don't have to deal with it on the converter box.  You might also want to clear out the disk image from the large storage area, and if you're done with it maybe delete the large storage disk altogether.

---

