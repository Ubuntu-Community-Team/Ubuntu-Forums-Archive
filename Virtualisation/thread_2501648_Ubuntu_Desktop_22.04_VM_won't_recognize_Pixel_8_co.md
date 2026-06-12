---
title: "Ubuntu Desktop 22.04 VM won't recognize Pixel 8 connected over USB"
date: 2024-10-16
forum: Virtualisation
---

### Post by vegetta664 on 2024-10-16
I have 1x Ubuntu 22.04 Desktop VM running on my Vsphere 8.X server. I've  connected 1x pixel 8 phone to the server, and assigned it to the Ubuntu  22.X VM (via settings/Add New Device/Add Host USB Device/Google Pixel  8) and a USB controller 3.2 (via settings/Add  New Device/USB Controller).  
     
However, the Ubuntu VM does not recognize the Pixel 8 device. I have  installed ADB drivers on my Ubuntu VM and the latest Android Studio. USB  debugging has been enabled on the Pixel 8 phone and "Default USB  configuration" has been set  to "File Transfer/Android Auto". 

The command "adb devices -l" doesn't show any connected devices. The lsusb command also doesn't show the phone.   

The dmesg logs shows several USB power related issues:        

  [  323.296213] usb 1-4-port1: unable to enumerate USB device
[  326.805265] usb 1-4.1: new high-speed USB device number 42 using xhci_hcd
[  326.889604] usb 1-4.1: device descriptor read/64, error -71
[  327.166404] usb 1-4.1: device descriptor read/64, error -71
[  327.343481] usb 1-4.1: new high-speed USB device number 43 using xhci_hcd
[  330.833247] usb 1-4.1: device descriptor read/all, error -71
[  330.833350] usb 1-4-port1: attempt power cycle
[  334.637667] usb 1-4.1: new high-speed USB device number 44 using xhci_hcd
[  334.650037] usb 1-4.1: device descriptor read/8, error -71
[  334.793019] usb 1-4.1: device descriptor read/8, error -71
[  334.986757] usb 1-4.1: new high-speed USB device number 45 using xhci_hcd
[  340.078126] usb 1-4.1: device descriptor read/8, error -110

---

