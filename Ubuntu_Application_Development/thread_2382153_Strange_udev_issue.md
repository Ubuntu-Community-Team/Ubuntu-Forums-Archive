---
title: "Strange udev issue"
date: 2018-01-09
forum: Ubuntu Application Development
---

### Post by scheng98 on 2018-01-09
I created a new udev rules to add symbolic link. It did create a new link, however it's kernel name.
10-local.rules: SUBSYSTEM=="usb",ATTRS{serial}=="55639303834351417132",SYMLINK+="encoder",GROUP="dialout"
New matching USB device, 
/dev$ ll encoder
lrwxrwxrwx 1 root root 15 Jan  9 15:27 encoder -> bus/usb/001/027                                     >>>>>>>>>>>>> I'm looking for [COLOR=#ff0000]/dev/ttyACM0[/COLOR]



/dev$ ll /dev/ttyACM0
crw-rw---- 1 root dialout 166, 0 Jan  9 15:27 /dev/ttyACM0

/dev$ lsusb | grep 27
Bus 001 Device 027: ID 2a03:0043 dog hunter AG Arduino Uno Rev3

Could anyone help? Much appreciated!

Steve

---

