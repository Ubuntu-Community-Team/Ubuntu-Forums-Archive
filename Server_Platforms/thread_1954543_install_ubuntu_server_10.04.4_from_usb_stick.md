---
title: "install ubuntu server 10.04.4 from usb stick"
date: 2012-04-08
forum: Server Platforms
---

### Post by rimrim on 2012-04-08
Hi, I was installing ubuntu server 10.04.4 (from usb) today having some problems and here is the result of my working out:
- can't detect cd-room: this can be solved by mounting the iso file into /cdrom, but this won't solve the debootstrap error coming on, so what I did is:
- mounting the usb device:
mount -t vfat /dev/sdc1 /mnt/usb 
(sdc1 varies, to detect it,  ls -l /dev/sd*)

- copying the iso from usb to /root (this solve the deboostrap error later)
cp /mnt/usb/ubuntu-10.04.4-server-amd64.iso /root/

- mount the iso to /cdrom
mount -t iso9600 -o loop /root/ubuntu-10.04.4-server-amd64.iso /cdrom

- go back to the installation, it should find the cd-rom and go on installation
- until the deboostrap error appears, go back and find "load components from an iso image", it works for me, (some suggest to unplug the network, to change the RAM reading speed from BIOS..., but after a long night, those solutions cant do the magic )

---

### Post by kevinthecomputerguy on 2012-04-08
Have you tried unetbootin [http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net) or pendrive

---

