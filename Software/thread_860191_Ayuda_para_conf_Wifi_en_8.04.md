---
title: "Ayuda para conf Wifi en 8.04"
date: 2008-07-15
forum: Software
---

### Post by Apipote on 2008-07-15
Hola a todos.

Acá, [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) hay un tutorial para que supuestamente la broadcom 4311 rev 2 ( y otras ) funcionen en 8.04 con los drivers linux.

Alguien pudo verificar si funciona? 
No encontre esa info buscando por la red, y no querría partirme la cabeza inutilmente.

Concretamente, esto es lo que teóricamente me funcionaría:

> If you are using the b43 driver from linux-2.6.24, follow these instructions.

Use version 011 of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

Use version 4.80.53.0 of Broadcom's proprietary driver.
Download and extract the firmware from this driver tarball:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

Note that you must adjust the FIRMWARE_IN/lSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place. 


Me da vergüenza admitir que no se en que directorio ( el de mi nombre ? ) bajar el driver para laburarlo, y luego como poner el FIRMWARE_INSTALL_DIR path ( /lib/firmware ?? ).

Slds y muchas gracias.

---

