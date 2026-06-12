---
title: "Install troubles"
date: 2008-10-23
forum: Server Platforms
---

### Post by eden159 on 2008-10-23
Hi,

I need an advise. I have a computer without a CDROM and a Floppy. I want to install the Server version. I tried with an USB following the automated instructions from this guide - [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) but when the installation tries to detect the CDROM it fails and I can't mount the USB drive (it gives me an error "Invalid argument"). So is there any other way to install it? Maybe Minimal CD Image ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) - are these images for the server version?) or...?

---

### Post by bluefrog on 2008-10-23
netboot install.

---

### Post by eden159 on 2008-10-23
> **bluefrog said:**
> netboot install.

How do I do that with the server version? Where do I get the netboot.tar.gz for the server version? Thanks in advance.

---

### Post by lykwydchykyn on 2008-10-23
[netboot.tar.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/20070308ubuntu40.4/images/netboot/netboot.tar.gz)

[Instructions](https://help.ubuntu.com/community/Installation/Netboot)

I have it setup on a server here, works a charm.  It's even better if you pair it with apt-mirror for a local repository.  I can crank out Ubuntu machines in no time flat.

---

### Post by eden159 on 2008-10-24
> **lykwydchykyn said:**
> [netboot.tar.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/20070308ubuntu40.4/images/netboot/netboot.tar.gz)

[Instructions](https://help.ubuntu.com/community/Installation/Netboot)

I have it setup on a server here, works a charm.  It's even better if you pair it with apt-mirror for a local repository.  I can crank out Ubuntu machines in no time flat.

Thanks for the links. Everything works, but there is another issue - it seems that the installation tries to install the desktop verion (when the software install screen show it installs openoffice and other stuff that I don't need for a server). Is there a way to tell the installer to install the server version (maybe some command line arguments when the first boot menu shows?)? This is the first time I try to install the server version and my questions might sound dumb to someone :)

---

### Post by bluefrog on 2008-10-24
you need to use the netboot files from the server cd.

---

