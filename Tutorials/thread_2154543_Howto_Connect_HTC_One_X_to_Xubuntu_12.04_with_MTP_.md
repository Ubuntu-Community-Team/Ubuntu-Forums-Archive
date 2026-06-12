---
title: "Howto Connect HTC One X to Xubuntu 12.04 with MTP &amp; USB"
date: 2013-06-15
forum: Tutorials
---

### Post by Merrattic on 2013-06-15
Although I tend to use airdroid to connect wirelessly, it bugged me that I couldn't browse and exchange files when connected via a USB cable, so I set about finding a solution. Ask Ubuntu was helpful but the real solution came from XDA Developers, so credit where it is due.

1. On your HTC, make sure that Developer Options is turned on

2. Connect HTC with USB to your PC

3. On your PC run lsusb in a terminal to find the VendorID (which should be 0bb4 for an HTC) Hopefully you get back this line:
```
lsusb
Bus 001 Device 009: ID 0bb4:0dfb High Tech Computer Corp.
```
4. Staying in terminal, create a new rules file:
```
sudo nano /etc/udev/rules.d/99-android.rules
``` and paste this into it and save```
# HTC ONE

SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
```

5. Still in terminal, run the following commands:
```
sudo add-apt-repository ppa:langdalepl/gvfs-mtp
sudo apt-get update
sudo apt-get upgrade
sudo mkdir /media/HTC
```

6. Now disconnect your phone and reboot your PC

7. If you are using Xubuntu, the install of a new gvfs will have broken your thunar slow/double opening fix, so you need to repair that:
```
sudo nano /etc/usr/share/gvfs/mounts/network.mount

and change 

Automount=true 

to 

Automount=false
``` and save.

8. Reconnect your phone via USB

9. Run the following commands in a terminal
```
sudo mtpfs -o allow_other /media/HTC
df -h
```

10. Open Thunar (or run cd /media/HTC) and browse /media/HTC and your files should be there

11. Before unplugging the phone run
```
sudo umount /media/HTC
```

It is possible to automate this a bit more, create launchers, and enable the mounting phase for a normal user by editing /etc/fuse.conf

Also, file transfers are very slow this way, so perhaps aidroid is still the way to go?

Hope this helps someone

---

