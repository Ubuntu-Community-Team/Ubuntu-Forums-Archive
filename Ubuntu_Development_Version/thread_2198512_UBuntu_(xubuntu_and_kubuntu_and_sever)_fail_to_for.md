---
title: "UBuntu (xubuntu and kubuntu and sever) fail to format to btrfs"
date: 2014-01-09
forum: Ubuntu Development Version
---

### Post by spupazza on 2014-01-09
I tried with several usb sticks (3), and with different snapshots (of the last 3 days) of xubuntu ,kubuntu and server 
the installer fail to format to btrfs.
It happens (not always) with ext4 too, but with btrfs I can't get around this issue.
With Xubuntu image I used gparted (I couldn't do the same with Kubuntu since partitionmanager doesn't recognize correctly my raid 0 configuration), to
format the hard drive with btrfs, so that I don't have to do it with the installer.
This way I can install with no errors, but when I reboot I get initrams prompt, with some complaint about not being aboe to find the root dev.
Before anyone wonders, grub was installed correctly on the raid config (whom name is recognized correctly).
Moreover if it wasn't, I wouldn't get there, but grup would hae complained before getting there.
Images were all 64bit, for what it could matter and kubuntu from today was the freshest (with the 3.13 kernel)

---

