---
title: "Xen guest netboot &quot;No network interfaces detected&quot;"
date: 2014-08-26
forum: Server Platforms
---

### Post by kantersw on 2014-08-26
Hi everyone

I'm having trouble installing a pv guest using the netboot method described in the [Xen community documentation.]("http://help.ubuntu.com/community/Xen#Manually_creating_a_PV_Guest_VM") I did everything exactly as the guide instructed, and a couple of months ago (May 15) everything did work. However when I try it now (I redid everything in the guide, even removed xen and everything, redownloaded the images, etc) the netboot setup claims it cannot find any network interfaces.

If I'm interpreting the system logs correctly (obtained by falling back to the shell, calling cat /var/log/syslog and grabbing the result from my ssh logs) it appears to be missing some package (libc5-udeb) but I'm really just guessing here.

Setup log, starting at the hardware configuration bit:

```

Aug 26 23:28:48 main-menu[213]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Aug 26 23:28:48 main-menu[213]: INFO: Menu item 'console-setup-udeb' selected
Aug 26 23:28:48 main-menu[213]: INFO: Falling back to the package description for console-setup-pc-ekmap
Aug 26 23:28:48 main-menu[213]: INFO: Falling back to the package description for console-setup-pc-ekmap
Aug 26 23:28:49 main-menu[213]: (process:526): cat: can't open '/sys/bus/usb/devices/*:*/bInterfaceClass': No such file or directory
Aug 26 23:28:49 main-menu[213]: (process:526): cat: can't open '/sys/bus/usb/devices/*:*/bInterfaceSubClass': No such file or directory
Aug 26 23:28:49 main-menu[213]: (process:526): cat: can't open '/sys/bus/usb/devices/*:*/bInterfaceProtocol': No such file or directory
Aug 26 23:28:49 main-menu[213]: (process:526): cat: can't open '/sys/bus/usb/devices/*:*/bInterfaceClass': No such file or directory
Aug 26 23:28:49 main-menu[213]: (process:526): cat: can't open '/sys/bus/usb/devices/*:*/bInterfaceSubClass': No such file or directory
Aug 26 23:28:49 main-menu[213]: (process:526): cat: can't open '/sys/bus/usb/devices/*:*/bInterfaceProtocol': No such file or directory
Aug 26 23:28:49 main-menu[213]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Aug 26 23:28:49 main-menu[213]: INFO: Menu item 'ethdetect' selected
Aug 26 23:28:49 net/hw-detect.hotplug: Detected hotpluggable network interface lo
Aug 26 23:28:49 hw-detect: Detected module 'usb-storage' for 'USB storage'
Aug 26 23:28:50 kernel: [   26.283988] usbcore: registered new interface driver usb-storage
Aug 26 23:28:50 hw-detect: insmod /lib/modules/3.13.0-32-generic/kernel/drivers/usb/storage/usb-storage.ko 
Aug 26 23:28:50 apt-install: Queueing package udev for later installation
Aug 26 23:28:50 apt-install: Queueing package pciutils for later installation
Aug 26 23:28:50 apt-install: Queueing package usbutils for later installation
Aug 26 23:28:52 check-missing-firmware: /dev/.udev/firmware-missing does not exist, skipping
Aug 26 23:28:52 check-missing-firmware: /run/udev/firmware-missing does not exist, skipping
Aug 26 23:28:52 check-missing-firmware: no missing firmware in /dev/.udev/firmware-missing /run/udev/firmware-missing
Aug 26 23:28:56 check-missing-firmware: /dev/.udev/firmware-missing does not exist, skipping
Aug 26 23:28:56 check-missing-firmware: /run/udev/firmware-missing does not exist, skipping
Aug 26 23:28:56 check-missing-firmware: no missing firmware in /dev/.udev/firmware-missing /run/udev/firmware-missing
Aug 26 23:28:56 main-menu[213]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Aug 26 23:28:56 main-menu[213]: INFO: Menu item 'netcfg' selected
Aug 26 23:28:56 main-menu[213]: INFO: Falling back to the package description for crypto-modules-3.13.0-32-generic-di
Aug 26 23:28:56 main-menu[213]: INFO: Falling back to the package description for crypto-modules-3.13.0-32-generic-di
Aug 26 23:28:56 netcfg[2506]: INFO: Starting netcfg v.1.116ubuntu1 (built 20140403-1424)
Aug 26 23:28:56 netcfg[2506]: WARNING **: Couldn't read Wpasupplicant pid file, not trying to kill.
Aug 26 23:28:56 netcfg[2506]: INFO: Could not find valid BOOTIF= entry in /proc/cmdline
Aug 26 23:28:58 main-menu[213]: INFO: Menu item 'netcfg' succeeded but requested to be left unconfigured.
Aug 26 23:28:59 main-menu[213]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Aug 26 23:29:00 main-menu[213]: INFO: Menu item 'di-utils-shell' selected
Aug 26 23:29:04 kernel: [   40.618784] random: nonblocking pool is initialized

```

[Complete log at pastebin.]("http://pastebin.com/iAwUKvuq")

So does anyone know how to resolve this issue? (Or has an alternative method of creating a pv ubuntu guest, circumventing the issue described above entirely.)


Thanks

---

### Post by kantersw on 2014-08-27
Fixed it. After mucking about quite a bit with the xen bridge configuration (which I think I improved a bit based on stuff I found, apparently eth0 shouldn't have an IP adress (or at least not the same one as xenbr0)). It didn't work, so I decided to try and get a centos pv guest going, and in their instructions they had the following line in the xen guest cfg file:

```
vif = [ 'bridge=xenbr0', ]
```

Which looks suspiciously like it is supposed to tell xen what bridge needs to be connected to the guest and it's missing from the cfg in the community documentation. So I added this line and now it works.

I think I'll update the community docs.

---

