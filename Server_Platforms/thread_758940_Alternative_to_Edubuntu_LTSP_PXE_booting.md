---
title: "Alternative to Edubuntu LTSP PXE booting?"
date: 2008-04-18
forum: Server Platforms
---

### Post by bodycoach2 on 2008-04-18
I've installed an Edubuntu server, and successfully booted a few newer computers through PXE. Kudos to the LTSP people.

My problem: I'm trying to set up an Edubuntu classroom for a small school, using older computers. Most are between 350 MHz PII's and 1 GHz machines. Only the newest machines boot with PXE. As I've learned, the older network interface cards don't have a bootprom in them, so no PXE.

I've been able to get one of the computers to boot using Etherboot ( [http://rom-o-matic.net](http://rom-o-matic.net) ), but it's  headache, and the boot process is slower than pouring molasses in Winter -in Norway! I could build and launch my own space shuttle in the same amount of time.

Anyway, most of these machines do have a hard drive -some only 8 GB, but good enough to use. I read this page on MultiBoot:

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPMultiboot](https://help.ubuntu.com/community/UbuntuLTSP/LTSPMultiboot)

...but I can't tell if I need to put the instructions on the server, or the clients. I'd like to install Edubuntu to those hard drives, but give it the option to log into the Edubuntu server.

If there are other alternatives, I'll be glad to try those too.

I'm hoping the Edubuntu team builds an alternative NetBoot CD to go with the LTSP server. Trying to boot older NICs is just a headache.

---

### Post by maybeway36 on 2008-04-18
If the computers are networked, you could probably find the kernel and initrd being used for netbooting (they're probably on the server in /opt/ltsp somewhere, not quite sure) and put those on a bootable CD with ISOLINUX.

---

### Post by maybeway36 on 2008-04-19
Try running this script to build a CD image. Install mkisofs and syslinux first.
```
#!/bin/sh
#mkedcd.sh - Make a boot CD to substitude for PXE booting in the Edubuntu thin client boot process
#Run this script on the server
if [ -f /usr/bin/genisoimage ] || [ -f /usr/bin/mkisofs ];then
 true
else
 sudo apt-get install mkisofs
 echo "Please run the script again."
 exit 2
fi
if [ -f /usr/lib/syslinux/isolinux.bin ];then
 true
else
 sudo apt-get install syslinux
 echo "Please run the script again."
 exit 2
fi
mkdir edcd
cp /var/lib/tftpboot/ltsp/i386/vmlinuz edcd/vmlinuz
cp /var/lib/tftpboot/ltsp/i386/initrd.img edcd/initrd.img
cp /usr/lib/syslinux/isolinux.bin edcd/isolinux.bin
cat > edcd/isolinux.cfg << "EOF"
DEFAULT vmlinuz
APPEND ro initrd=initrd.img quiet splash
EOF
if [ -f /usr/bin/genisoimage ];then
echo "Building CD image..."
genisoimage -o edcd.iso \
-b isolinux.bin -c boot.cat \
-no-emul-boot -boot-load-size 4 -boot-info-table \
-r -J -l -quiet \
-V "EdubuntuBootCD" \
edcd/
rm -r edcd/
else
if [ -f /usr/bin/mkisofs ];then
echo "Building CD image..."
mkisofs -o edcd.iso \
-b isolinux.bin -c boot.cat \
-no-emul-boot -boot-load-size 4 -boot-info-table \
-r -J -l -quiet \
-V "EdubuntuBootCD" \
edcd/
rm -r edcd/
else
echo "Neither genisoimage nor mkisofs was found."
exit 1
fi
fi
```

---

### Post by bodycoach2 on 2008-05-05
Tonight, while trying to get these (12 PII machines) running with and Edubuntu server- I finally found the right [rom-o-matic]("http://rom-o-matic.net") iso image. In the selection of the driver, look for gpxe:all-drivers in the selection. 

I burned an iso to a CD, and used it to netboot to the Edubuntu LTSP server. I was able to get all the machines to boot, and log into the server.

This bootable image should be available, or a link made availabe, on the Edubuntu site.

[http://rom-o-matic.net](http://rom-o-matic.net)

---

