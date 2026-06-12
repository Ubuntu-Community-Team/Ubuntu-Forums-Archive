---
title: "KVM - ISO Booting Issue"
date: 2013-01-05
forum: Virtualisation
---

### Post by OmegaHarvest on 2013-01-05
Hi,

I'm trying to boot an ISO of ubuntu 12.10 in a VM I have made using KVM. I'm trying to do all this through the Virtual Machine Manager. I copied the ISO to /var/lib/libvirt/images/ via a local ftp and have attached this to the virtual CD Rom. However, on startup I just see 'Boot Failed: Could not read from CDROM (code 0004). 

I couldn't find much about this online which was helpful to me. If anyone has any ideas or needs further info, I would be very grateful for your expertise!

Thanks

---

### Post by markbl on 2013-01-05
It's possibly a permissions issue. You should not need to be manually copying files around in system areas etc. Just follow [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) to install qemu-kvm and then follow [https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager) to boot your ISO.

Here's another useful link [http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/).

---

### Post by OmegaHarvest on 2013-01-08
Thanks for the response. I got to the bottom of it. There was some issue with my FTP server (FileZilla running on version 8 of that 'other' operating system ;)) which was corrupting files in some way. I was getting checksum errors when copying files from the same server to my SmoothWall express VM. I used a different FTP server and all was fine. Just for anyone who may stumble across this....

---

