---
title: "Using a raw partition as disk image with KVM/QEMU?"
date: 2007-11-20
forum: Virtualisation
---

### Post by Loranga on 2007-11-20
Would there be any performance gains using a real partition (/dev/sda3 on my host) as hard disk device instead of a file image when using QEMU/KVM?

(I made an image with qemu-img and copied with dd to a raw partition (dd if=image.img of=/dev/sda3)).

---

### Post by rmemm on 2007-11-20
One would think so, but I've not tried this.

Rob

---

### Post by pedricus on 2011-09-28
I realize this is old, but for someone else's sake:

I have tried this with winxp using libvirt on a dedicated HDD in Ubuntu 10.10, 

performance is noticeably improved by doing this, but (at the time of this posting) there seems to be some compatibility issues when (if) moving the drive to a real machine, I've had instances where the partition is completely visible and working, and some where it appears as a raw disk never to return to normal.

mounting the volume in Ubuntu also seems to sometimes cause booting issues for the VM afterwards.

but all in all, it works fine as long as the partition/drive is left alone and used only for the VM.

i never bothered to pursue this any further unfortunately,

---

