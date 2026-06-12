---
title: "lxc unprivileged container and usb device"
date: 2015-08-18
forum: Virtualisation
---

### Post by jean-pierre2 on 2015-08-18
Hello,

I am using lxc unprivileged containers launched by **root**.

I want to pass to the container this usb device :
[FONT=courier new]crw-rw---- 1 root dialout 188, 0 Aug 16 17:07 /dev/ttyUSB0[/FONT]

Once the container started, I run :
[FONT=courier new]lxc-device -n c1 add /dev/ttyUSB0[/FONT]
(same if I just do a touch on [FONT=courier new]/var/lib/lxc/c1/rootfs/dev/ttyUSB0[/FONT])
And it appears this way **inside **the container :
[FONT=courier new]crw-r----- 1 nobody nogroup 188, 0 Aug 16 15:17 /dev/ttyUSB0[/FONT]

I need the device to be writable at least by root inside the container. But if I try to run anyone of those commands :
[FONT=courier new]chmod 777 /dev/ttyUSB0[/FONT]
or [FONT=courier new]chown root /dev/ttyUSBO[/FONT]
I get this error :
[SIZE=2][FONT=courier new]chmod: changing permissions of '/dev/ttyUSB0': Operation not permitted[/FONT][/SIZE]

My container config file includes :
[FONT=courier new]lxc.id_map = u 0 100000 65536
[SIZE=2]lxc.id_map = g 0 100000 65536[/SIZE]
[SIZE=2]lxc.cgroup.devices.allow = c 188:* rwm[/SIZE]
[SIZE=2]lxc.mount.entry = /dev/ttyUSB0  dev/ttyUSB0  none  bind,optional[/SIZE][/FONT]

host+container OS : ubuntu 14.04
lxc : 1.0.7
 
Thanks for any help to better understand how it should be configured.

JP

---

### Post by jean-pierre2 on 2015-08-22
Just figured out that device has to be R/W for all on the host. A simple chmod solve the issue.

---

