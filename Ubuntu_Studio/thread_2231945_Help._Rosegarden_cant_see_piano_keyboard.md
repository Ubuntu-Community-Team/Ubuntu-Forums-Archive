---
title: "Help. Rosegarden cant see piano keyboard"
date: 2014-06-28
forum: Ubuntu Studio
---

### Post by Richard_Hainsworth on 2014-06-28
I bought a soft Dream Cheeky piano keyboard. It connects with USB.

`udevadm monitor` shows that it connects with id "1941:8021", but it is not listed as a midi device.

It is allocated hid-generic driver.

How do I get it to be recognised as midi?

I've spent hours googling. I set a udev rule. I found Dream Cheeky in hwdb, where it is listed as Weather Station / Rocket Launcher.

Please someone give me a clue.

---

### Post by jejeman on 2014-06-29
Plug it. Give
```
lsusb
amidi -l
```

---

### Post by Richard_Hainsworth on 2014-06-29
Jejeman, thanks.

#lsusb
Bus 001 Device 022: ID 13d3:3375 IMC Networks Atheros AR3012 Bluetooth 4.0 Adapter
Bus 001 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 004: ID 064e:f300 Suyin Corp. UVC 0.3M Webcam
Bus 001 Device 020: ID 1941:8021 Dream Link WH1080 Weather Station / USB Missile Launcher
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
# amidi -l
Dir Device    Name
# 

Also FYI tail of dmesg when usb plugged in
[41270.244271] usb 1-1.2: USB disconnect, device number 20
[41271.958227] usb 1-1.2: new low-speed USB device number 23 using ehci-pci
[41272.045026] usb 1-1.2: New USB device found, idVendor=1941, idProduct=8021
[41272.045044] usb 1-1.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[41272.054576] hid-generic 0003:1941:8021.0016: hiddev0,hidraw3: USB HID v1.00 Device [HID 1941:8021] on usb-0000:00:1d.0-1.2/input0

Also FYI the response from udevadm info.
$ udevadm info -a -p /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:1941:8021.0017/hidraw/hidraw3

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:1941:8021.0017/hidraw/hidraw3':
    KERNEL=="hidraw3"
    SUBSYSTEM=="hidraw"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:1941:8021.0017':
    KERNELS=="0003:1941:8021.0017"
    SUBSYSTEMS=="hid"
    DRIVERS=="hid-generic"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0':
    KERNELS=="1-1.2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usbhid"
    ATTRS{bInterfaceClass}=="03"
    ATTRS{bInterfaceSubClass}=="00"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2':
    KERNELS=="1-1.2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="1.2"
    ATTRS{idVendor}=="1941"
    ATTRS{speed}=="1.5"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="24"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="100mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="0"
    ATTRS{bcdDevice}=="0100"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{version}==" 1.10"
    ATTRS{urbnum}=="9"
    ATTRS{ltm_capable}=="no"
    ATTRS{removable}=="removable"
    ATTRS{idProduct}=="8021"
    ATTRS{bDeviceClass}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1':
    KERNELS=="1-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{devpath}=="1"
    ATTRS{idVendor}=="8087"
    ATTRS{speed}=="480"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="2"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="0mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="8"
    ATTRS{bcdDevice}=="0000"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{version}==" 2.00"
    ATTRS{urbnum}=="530"
    ATTRS{ltm_capable}=="no"
    ATTRS{removable}=="fixed"
    ATTRS{idProduct}=="0024"
    ATTRS{bDeviceClass}=="09"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="0"
    ATTRS{idVendor}=="1d6b"
    ATTRS{speed}=="480"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{authorized_default}=="1"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="0mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="2"
    ATTRS{bcdDevice}=="0311"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{version}==" 2.00"
    ATTRS{urbnum}=="38"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="Linux 3.11.0-19-lowlatency ehci_hcd"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="0002"
    ATTRS{bDeviceClass}=="09"
    ATTRS{product}=="EHCI Host Controller"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci-pci"
    ATTRS{irq}=="23"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x0c0320"
    ATTRS{companion}==""
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,0000000f"
    ATTRS{device}=="0x1c26"
    ATTRS{uframe_periodic_max}=="100"
    ATTRS{msi_bus}==""
    ATTRS{local_cpulist}=="0-3"
    ATTRS{vendor}=="0x8086"
    ATTRS{subsystem_device}=="0x1427"
    ATTRS{numa_node}=="-1"
    ATTRS{d3cold_allowed}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

---

### Post by jejeman on 2014-06-30
Obviously keyboard is not class compilant.

---

