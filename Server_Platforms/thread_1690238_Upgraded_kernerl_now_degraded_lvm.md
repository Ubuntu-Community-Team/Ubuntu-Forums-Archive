---
title: "Upgraded kernerl now degraded lvm"
date: 2011-02-18
forum: Server Platforms
---

### Post by Zulan on 2011-02-18
Hello guys. I'm a bit of a newbie when it comes to linux and I had to update my kernel to get this one peace of software that I use to work. It however stopped my machine from booting. I'm sure this can fixed but I have no idea how to. 

When I boot machine now it stops with the message:

Mount: Mounting non on /dev failed: So such device
udevd[906]: error initialization netlink socket

libudev: udev_montior_new_from_netlink: error getting socket: Invalid argument
Segmentation fault
There apperas to be on or more degraded LVM volumes, and your root devcie may depend on the LVM volumes being online. One or more of the following LVM volumes are degraded:
read_urandom: /dev/urandom: open failed: No such file or directory.
Gave up waiting for root device: common problems:
- boot args (cat /proc/cmdline)

and it alls ends with 
ALERT! /dev/mapper/websrv-root does not exist. Dropping to shell.

___________

But if I press esc at grub and choose and older version I get to the boot logo screen and it seems to be loading longer then before. But it also ends with:

init: ureadahead main process (2688) terminated with status 5
livudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument

I can then type my root password and it actually finds the file system and I can browse my files. I cant get the network to work, then I migh be able to get to the files and just rebuild the system. 

Any ideas what I can do?

I have tried booting a live cd but it just sais that LVM is not supported and apt-get install doesnt work.

___________

I have tried more stuff and it might be that it fails to mount the /boot. As I understand it, there should be a file called menu.lst in there. But my boot directory is empty.

---

