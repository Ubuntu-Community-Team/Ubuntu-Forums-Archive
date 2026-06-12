---
title: "Serial Port Permission"
date: 2010-07-20
forum: Wine
---

### Post by mamoothz on 2010-07-20
Well, hello there!

I'm trying to use a program that will trite stuff on devices using the serial port. The program I'm using it [this one]("www.4shared.com/file/utlf-yYl/S810_AZ-Loader.html").

The steps I was used to do in Windows are:
1. Connect the device to the serial port. The device must be turned off
2. Select a file to upgrade
2. Click Next
3. Turn on the Device

As soon as I turn on the device a "Done" shows up in the screen. I think that means that the serial port is working and recognized the device.
The step would be to write the upgrade file on the device
Then I get the error "Set stb memory error". Looks, from my point of view, like wine doens't have the permition to write on the serial port, only read.

This error already happned in windows, all I had to do was to restart my computer or just deactivate/activate the COM1 Port.

Hope you guys can help me out. Thanks in advance

---

### Post by asdfoo on 2010-07-22
> **mamoothz said:**
> Well, hello there!

I'm trying to use a program that will trite stuff on devices using the serial port. The program I'm using it [this one]("www.4shared.com/file/utlf-yYl/S810_AZ-Loader.html").

The steps I was used to do in Windows are:
1. Connect the device to the serial port. The device must be turned off
2. Select a file to upgrade
2. Click Next
3. Turn on the Device

As soon as I turn on the device a "Done" shows up in the screen. I think that means that the serial port is working and recognized the device.
The step would be to write the upgrade file on the device
Then I get the error "Set stb memory error". Looks, from my point of view, like wine doens't have the permition to write on the serial port, only read.

This error already happned in windows, all I had to do was to restart my computer or just deactivate/activate the COM1 Port.

Hope you guys can help me out. Thanks in advance

depending on which device under /dev is your serial port, you may need to symlink it as the userguide states:

[http://www.winehq.org/docs/wineusr-guide/misc-things-to-configure](http://www.winehq.org/docs/wineusr-guide/misc-things-to-configure)

eg. the default serial port should be /dev/ttys0
if you ls -l /dev/ttys0
it should print out the permissions, user and group ownership

if you have a usb serial port, then it may be a different device name, check the output of dmesg

---

### Post by mamoothz on 2010-07-22
Well, here's the output of ls -l /dev/ttys0

```
crw-rw---- 1 root dialout 4, 64 2010-07-22 12:33 /dev/ttyS0
```


I've tried what's on the [user guide]("http://www.winehq.org/docs/wineusr-guide/misc-things-to-configure"), but no sucess still.

I was trying to get it working with a Virtual Machine, using VirtualBox.
[[IMG]http://img843.imageshack.us/img843/8004/comport.th.png[/IMG]](http://img843.imageshack.us/img843/8004/comport.png)

Looks like there's no COM port on the virtual machine (in the device manager and the program gives an error instantly like there's no com port.

---

### Post by sisco311 on 2010-07-22
Try to add your user to the dialout group:
```
sudo gpasswd -a **username** dialout
```

Log out and log back in.

---

### Post by mamoothz on 2010-07-24
@sisco311	
Didn't work.
Still getting same errors (in wine and virtual box).

I guess I'll see my self going back to XP again.

---

