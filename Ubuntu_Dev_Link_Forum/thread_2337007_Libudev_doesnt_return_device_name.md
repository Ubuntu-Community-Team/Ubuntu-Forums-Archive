---
title: "Libudev doesnt return device name"
date: 2016-09-13
forum: Ubuntu Dev Link Forum
---

### Post by vieiranetoc on 2016-09-13
Hi, currently i'm in a system development that depends on check if some external devices are connected to pc. For example, any camera can be used for image processing, so they have in common the substring 'webcam' or 'camera' in their names in our case. To check this information I'm using libudev, but for some cameras (coincidence or not: the logitechs cams) doesn't return me their usb names. The code bellow should return some parameters from usb devices, but mostly of them are (null), the only parameter that I get with no errors is idVendor/idProduct. I can't understand what is happening once lsusb command on terminal return all needed parameters.
```
udev_list_entry_foreach(dev_list_entry, devices){        const char *path;


        path = udev_list_entry_get_name(dev_list_entry);
        dev = udev_device_new_from_syspath(udev, path);


        std::string path_string(path);




        if (!dev) {
            std::cout << "Unable to find parent " << subsystem
                      << " directory" << std::endl;
            exit(1);
        }
        
        printf("  VID/PID: %s %s\n",
                udev_device_get_sysattr_value(dev,"idVendor"),
                udev_device_get_sysattr_value(dev, "idProduct"));
        printf("  %s\n  %s\n",
                udev_device_get_sysattr_value(dev,"manufacturer"),
                udev_device_get_sysattr_value(dev,"product"));
        printf("  serial: %s\n",
                 udev_device_get_sysattr_value(dev, "serial"));
        udev_device_unref(dev);
    }
```
and it's return:
> VID/PID: 1d6b 0002  Linux 4.4.0-36-generic ehci_hcd
  EHCI Host Controller
  serial: 0000:00:1a.0
VID/PID: 1bcf 2b80
  CKFA156H455010006920
  Laptop_Integrated_Webcam_HD
  serial: (null)
  VID/PID: 1d6b 0002
  Linux 4.4.0-36-generic xhci-hcd
  xHCI Host Controller
  serial: 0000:03:00.0
VID/PID: 046d c52f
  Logitech
  USB Receiver
  serial: (null)
VID/PID: 046d 0821
  (null)
  (null)
  serial: EC1535A0
VID/PID: 1d6b 0003
  Linux 4.4.0-36-generic xhci-hcd
  xHCI Host Controller
  serial: 0000:03:00.0
VID/PID: 1d6b 0002
  Linux 4.4.0-36-generic ehci_hcd
  EHCI Host Controller
  serial: 0000:00:1d.0
VID/PID: 8087 0024
  (null)
  (null)
  serial: (null)
  VID/PID: 0cf3 3005
  (null)
  (null)
  serial: (null)




and lsusb return:
> Bus 002 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 012: ID 046d:0821 Logitech, Inc. HD Webcam C910
Bus 003 Device 014: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2b80 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




---

