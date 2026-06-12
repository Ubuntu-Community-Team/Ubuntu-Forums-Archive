---
title: "network-install PXE boot question"
date: 2013-02-11
forum: Server Platforms
---

### Post by mc0001 on 2013-02-11
Hi,
I'm trying my first attept at PXE booting and having the following problem. I'm using an net-boot installation image to iSCSI-backed storage (for Calxeda's highbank ARM architecture), and the installation appears to go fine, i.e. I go through a normal installation process, the iSCSI storage is found and written to, so here's the output of the "file" command for the storage file:

test.img: x86 boot sector; partition 1: ID=0x83, active, starthead 1, startsector 63, 497952 sectors; partition 2: ID=0x83, starthead 0, startsector 498015, 14699475 sectors; partition 3: ID=0x5, starthead 0, startsector 15197490, 787185 sectors, code offset 0xb8
 
To my eye this seems fine, but I'm not sure how to get it to reboot into this installed image. If this was an install using a physical media like a CD or a USB stick then one just removes it at the end of installation and the system would boot into the new image. How do I achieve the same via PXE booting after an install? My default.cfg install file on my TFTP server for the initial install is:

LABEL ubuntu1204-armhf
        kernel /vmlinuz
        MENU LABEL ubuntu1204-armhf
        append initrd=/initrd.gz console=ttyAMA0 locale=en_US priority=critical text

What must this become to now boot into the installed image? 

TIA
m

---

