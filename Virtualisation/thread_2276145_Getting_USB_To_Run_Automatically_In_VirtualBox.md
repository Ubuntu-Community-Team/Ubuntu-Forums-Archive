---
title: "Getting USB To Run Automatically In VirtualBox"
date: 2015-04-30
forum: Virtualisation
---

### Post by crutchcorn on 2015-04-30
I want to set up a udev rule to run every time I plug in a USB drive that will connect that USB drive to connect to a VM in VirtualBox. The udev rule works to connect a USB drive to a running VM, but only once per boot. Someone please help me. I have the in /etc/udev/rules.d/10-usbmount.rules:


     ```
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", SUBSYSTEMS=="usb", RUN+="/usr/bin/vbox-automount-usb"
```
And this in /usr/bin/vbox-automount-usb:


```

#!/bin/bash
set `lsusb -d ${ID_VENDOR}:${ID_MODEL}| sed 's/:.*//g'`
while [ ! -z "$1" ]; do
  case $1 in
       Bus) shift
       busdevice="$1"
       ;;
       Device) shift
       busdevice=${busdevice}"/$1"
       ;;
  esac
  shift
done
if [ ! -z "$busdevice" ]; then
  address=$(VBoxManage list usbhost | grep "Address:" | grep $bus device | sed -e 's/Address://' -e 's/^[ \t]*//')
  if [ ! -z "$address" ]; then
       su - guestos -c "VBoxManage controlvm guestos_0001 usbattach $address"
  fi
fi
```


EDIT: 
I can make /etc/udev/rules.d/10-usbmount.rules work also by changing it to:
   
    ```
ACTION=="add", SUBSYSTEM=="block", KERNEL=="sd[a-z]1", RUN+="/usr/bin/vbox-automount-usb"
```
But it still only mounts a USB in VirtualBox for the first time


EDIT: 
The same thing STILL happens when using 
    
    ```
su - guestos -c "VBoxManage controlvm guestos_0001 usbattach `VBoxManage list usbhost | grep "Address:" | grep $bus device | sed -e 's/Address://' -e 's/^[ \t]*//'`"
```
For /usr/bin/vbox-automount-usb

---

