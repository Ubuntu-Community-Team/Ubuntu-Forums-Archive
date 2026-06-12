---
title: "VMWare 12 and Ubuntu for Gnome"
date: 2017-06-16
forum: Virtualisation
---

### Post by llloyd on 2017-06-16
Trying to install the Gallium 0.4 on SVGA umm, yeah, that, sorry, very new to this. So, anyway, following 

[https://www.mesa3d.org/vmware-guest.html](https://www.mesa3d.org/vmware-guest.html)

Get to the part

vmwgfx kernel module. First make sure that any old version of this kernel module is removed from the system by issuing
  sudo rm /lib/modules/`uname -r`/kernel/drivers/gpu/drm/vmwgfx.ko*
Build and install:
  cd $TOP/vmwgfx
  make
  sudo make install
  sudo depmod -a

When I do the sudo make install command it pukes out

llloyd4@ubuntu:~/vmwgfx$ sudo make install
make -C /lib/modules/4.10.0-19-generic/build  KCPPFLAGS="-DVMWGFX_STANDALONE -DTTM_STANDALONE" SUBDIRS=`/bin/pwd` DRMSRCDIR=`/bin/pwd` modules_install
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-19-generic'
  INSTALL /home/llloyd4/vmwgfx/vmwgfx.ko
At main.c:158:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  DEPMOD  4.10.0-19-generic
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-19-generic'

All I am finding, so far, in Google is it is some UEFI bios. Not sure what bios VMWare emulates so... Could anyone, please, tell me how to fix this so I can get the video drivers installed? I'm running it at 800x600 on an Unknown Display with no 16:9 support so I need to get this running before I can continue on. >.<

---

