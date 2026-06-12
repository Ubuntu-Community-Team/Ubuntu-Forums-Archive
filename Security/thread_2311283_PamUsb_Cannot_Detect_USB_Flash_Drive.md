---
title: "PamUsb Cannot Detect USB Flash Drive"
date: 2016-01-26
forum: Security
---

### Post by devon11 on 2016-01-26
The result of sudo pamusb-conf --add-device my-usb-stick -v is :
```
Inspecting /org/freedesktop/UDisks/devices/sda1
    Invalid: Not a removable device
Inspecting /org/freedesktop/UDisks/devices/sda2
    Invalid: Not a removable device
Inspecting /org/freedesktop/UDisks/devices/sda3
    Invalid: Not a removable device
Inspecting /org/freedesktop/UDisks/devices/sdb
    Invalid: Not a removable device
Inspecting /org/freedesktop/UDisks/devices/sda
    Invalid: Not a removable device
Inspecting /org/freedesktop/UDisks/devices/sdb1
    Invalid: Not a removable device
```
I also ran: ```
sudo add-apt-repository ppa:garhuy/pamusb 
sudo apt-get update && sudo apt-get install libpam-usb pamusb-common pamusb-tools
```
My USB is recognized as /dev/sdb by GParted.

---

