---
title: "Disk read error for W7 partition"
date: 2011-05-19
forum: Virtualisation
---

### Post by deesto on 2011-05-19
I've converted a physical Windows 7 partition to an image file using `dd`, and can't get the partition itself or the image to boot virtually, via either virt-manager or kvm.  Both fail on boot with the error: "A disk read error occurred."

Perhaps I've used a bad `dd` command, but I simply did: `sudo dd if=/dev/sdb7 of=my-w7-image.img conv=noerror`

Also tried converting the image to qcow2 format with `qemu-img` and that seemed to work (and the new image checks out without errors, though I suppose that means nothing if the original image is bad). I get the same error what booting this qcow2 image virtually.  

I've tried to fix the boot loader with a W7 boot disc, and it wants an admin password that I don't have.  I've also tried booting with other recovery discs, but they either don't find the disk or partition, or they don't think it's a bootable W7 partition.

---

