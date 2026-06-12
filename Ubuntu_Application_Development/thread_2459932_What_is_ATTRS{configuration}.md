---
title: "What is ATTRS{configuration}?"
date: 2021-03-29
forum: Ubuntu Application Development
---

### Post by lapaz17 on 2021-03-29
I connected an usb camera to my vmware ubuntu and ran 
```
```
udevadm info -a /sys/bus/usb/devices/3-4.1:1.0

``````
Here is the output:
```
```
looking at device '/devices/pci0000:00/0000:00:15.0/0000:03:00.0/usb3/3-4/3-4.1/3-4.1:1.0':
    KERNEL=="3-4.1:1.0"
    SUBSYSTEM=="usb"
    DRIVER=="uvcvideo"
    ATTR{bInterfaceSubClass}=="01"
    ATTR{iad_bFunctionClass}=="0e"
    ATTR{bInterfaceClass}=="0e"
    ATTR{bAlternateSetting}==" 0"
    ATTR{bInterfaceProtocol}=="00"
    ATTR{iad_bFunctionSubClass}=="03"
    ATTR{iad_bInterfaceCount}=="02"
    ATTR{iad_bFirstInterface}=="00"
    ATTR{supports_autosuspend}=="1"
    ATTR{bNumEndpoints}=="01"
    ATTR{authorized}=="1"
    ATTR{bInterfaceNumber}=="00"
    ATTR{iad_bFunctionProtocol}=="00"


  looking at parent device '/devices/pci0000:00/0000:00:15.0/0000:03:00.0/usb3/3-4/3-4.1':
    KERNELS=="3-4.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{rx_lanes}=="1"
    ATTRS{idVendor}=="0ac8"
    ATTRS{product}=="A4 TECH USB2.0 PC Camera J"
    ATTRS{removable}=="unknown"
    ATTRS{tx_lanes}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{devnum}=="16"
    ATTRS{idProduct}=="c40a"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="0"
    ATTRS{devpath}=="4.1"
    ATTRS{speed}=="480"
    ATTRS{authorized}=="1"
    ATTRS{bDeviceClass}=="ef"
    ATTRS{bNumInterfaces}==" 4"
    ATTRS{ltm_capable}=="no"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{version}==" 2.00"
    ATTRS{busnum}=="3"
    ATTRS{manufacturer}=="A4 TECH"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceSubClass}=="02"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{urbnum}=="5071"
    ATTRS{configuration}==""
    ATTRS{bNumConfigurations}=="1"


  looking at parent device '/devices/pci0000:00/0000:00:15.0/0000:03:00.0/usb3/3-4':
    KERNELS=="3-4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{devpath}=="4"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{maxchild}=="7"
    ATTRS{tx_lanes}=="1"
    ATTRS{speed}=="480"
    ATTRS{bcdDevice}=="0100"
    ATTRS{urbnum}=="177632"
    ATTRS{removable}=="unknown"
    ATTRS{configuration}=="VMware, Inc."
    ATTRS{devnum}=="4"
    ATTRS{bMaxPower}=="0mA"
    ATTRS{rx_lanes}=="1"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{busnum}=="3"
    ATTRS{product}=="VMware Virtual USB Hub"
    ATTRS{version}==" 2.00"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceClass}=="09"
    ATTRS{ltm_capable}=="no"
    ATTRS{idVendor}=="0e0f"
    ATTRS{manufacturer}=="VMware, Inc."
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bmAttributes}=="e0"
    ATTRS{idProduct}=="0002"


  looking at parent device '/devices/pci0000:00/0000:00:15.0/0000:03:00.0/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{idVendor}=="1d6b"
    ATTRS{maxchild}=="4"
    ATTRS{version}==" 2.00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{bcdDevice}=="0508"
    ATTRS{devnum}=="1"
    ATTRS{tx_lanes}=="1"
    ATTRS{devpath}=="0"
    ATTRS{interface_authorized_default}=="1"
    ATTRS{authorized_default}=="1"
    ATTRS{bMaxPower}=="0mA"
    ATTRS{urbnum}=="80989"
    ATTRS{manufacturer}=="Linux 5.8.0-44-generic xhci-hcd"
    ATTRS{bDeviceClass}=="09"
    ATTRS{authorized}=="1"
    ATTRS{idProduct}=="0002"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{removable}=="unknown"
    ATTRS{rx_lanes}=="1"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{ltm_capable}=="no"
    ATTRS{busnum}=="3"
    ATTRS{bmAttributes}=="e0"
    ATTRS{serial}=="0000:03:00.0"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{product}=="xHCI Host Controller"
    ATTRS{bDeviceSubClass}=="00"


  looking at parent device '/devices/pci0000:00/0000:00:15.0/0000:03:00.0':
    KERNELS=="0000:03:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="xhci_hcd"
    ATTRS{subsystem_device}=="0x0779"
    ATTRS{local_cpus}=="00000000,00000000,00000000,0000000f"
    ATTRS{device}=="0x0779"
    ATTRS{current_link_width}=="32"
    ATTRS{vendor}=="0x15ad"
    ATTRS{driver_override}=="(null)"
    ATTRS{ari_enabled}=="0"
    ATTRS{acpi_index}=="16777984"
    ATTRS{broken_parity_status}=="0"
    ATTRS{irq}=="18"
    ATTRS{local_cpulist}=="0-3"
    ATTRS{current_link_speed}=="5.0 GT/s PCIe"
    ATTRS{msi_bus}=="1"
    ATTRS{subsystem_vendor}=="0x15ad"
    ATTRS{numa_node}=="-1"
    ATTRS{max_link_speed}=="5.0 GT/s PCIe"
    ATTRS{label}=="usb_xhci"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{enable}=="1"
    ATTRS{class}=="0x0c0330"
    ATTRS{consistent_dma_mask_bits}=="64"
    ATTRS{revision}=="0x00"
    ATTRS{max_link_width}=="32"
    ATTRS{d3cold_allowed}=="1"


  looking at parent device '/devices/pci0000:00/0000:00:15.0':
    KERNELS=="0000:00:15.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="pcieport"
    ATTRS{max_link_width}=="32"
    ATTRS{max_link_speed}=="5.0 GT/s PCIe"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{current_link_width}=="32"
    ATTRS{subsystem_device}=="0x07a0"
    ATTRS{broken_parity_status}=="0"
    ATTRS{revision}=="0x01"
    ATTRS{subordinate_bus_number}=="3"
    ATTRS{irq}=="24"
    ATTRS{ari_enabled}=="0"
    ATTRS{current_link_speed}=="5.0 GT/s PCIe"
    ATTRS{local_cpulist}=="0-3"
    ATTRS{device}=="0x07a0"
    ATTRS{vendor}=="0x15ad"
    ATTRS{numa_node}=="-1"
    ATTRS{enable}=="2"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{subsystem_vendor}=="0x15ad"
    ATTRS{secondary_bus_number}=="3"
    ATTRS{driver_override}=="(null)"
    ATTRS{class}=="0x060400"
    ATTRS{msi_bus}=="1"
    ATTRS{local_cpus}=="00000000,00000000,00000000,0000000f"
    ATTRS{d3cold_allowed}=="1"


  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""



``````
Then I try to connect my phone with MTP mode and equivalent output for it:
```
```
looking at device '/devices/pci0000:00/0000:00:15.0/0000:03:00.0/usb3/3-2/3-2:1.0':
    KERNEL=="3-2:1.0"
    SUBSYSTEM=="usb"
    DRIVER=="usbfs"
    ATTR{bNumEndpoints}=="03"
    ATTR{interface}=="MTP"
    ATTR{bInterfaceProtocol}=="00"
    ATTR{bInterfaceClass}=="ff"
    ATTR{supports_autosuspend}=="1"
    ATTR{bInterfaceSubClass}=="ff"
    ATTR{authorized}=="1"
    ATTR{bAlternateSetting}==" 0"
    ATTR{bInterfaceNumber}=="00"


  looking at parent device '/devices/pci0000:00/0000:00:15.0/0000:03:00.0/usb3/3-2':
    KERNELS=="3-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{devpath}=="2"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{tx_lanes}=="1"
    ATTRS{busnum}=="3"
    ATTRS{manufacturer}=="Vestel"
    ATTRS{product}=="SDM632-MTP _SN:F18D166A"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{configuration}=="mtp"
    ATTRS{quirks}=="0x0"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{idProduct}=="4ee1"
    ATTRS{serial}=="2818452719000003"
    ATTRS{devnum}=="18"
    ATTRS{urbnum}=="1806"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{maxchild}=="0"
    ATTRS{speed}=="480"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{rx_lanes}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{authorized}=="1"
    ATTRS{idVendor}=="18d1"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{bcdDevice}=="0409"
    ATTRS{bDeviceClass}=="00"
    ATTRS{removable}=="unknown"
    ATTRS{ltm_capable}=="no"
    ATTRS{bNumConfigurations}=="1"


  looking at parent device '/devices/pci0000:00/0000:00:15.0/0000:03:00.0/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{idProduct}=="0002"
    ATTRS{bMaxPower}=="0mA"
    ATTRS{product}=="xHCI Host Controller"
    ATTRS{version}==" 2.00"
    ATTRS{tx_lanes}=="1"
    ATTRS{speed}=="480"
    ATTRS{devpath}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{interface_authorized_default}=="1"
    ATTRS{serial}=="0000:03:00.0"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{manufacturer}=="Linux 5.8.0-44-generic xhci-hcd"
    ATTRS{devnum}=="1"
    ATTRS{authorized_default}=="1"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{removable}=="unknown"
    ATTRS{configuration}==""
    ATTRS{maxchild}=="4"
    ATTRS{authorized}=="1"
    ATTRS{rx_lanes}=="1"
    ATTRS{idVendor}=="1d6b"
    ATTRS{ltm_capable}=="no"
    ATTRS{bmAttributes}=="e0"
    ATTRS{urbnum}=="290868"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bcdDevice}=="0508"
    ATTRS{busnum}=="3"
    ATTRS{bNumConfigurations}=="1"


  looking at parent device '/devices/pci0000:00/0000:00:15.0/0000:03:00.0':
    KERNELS=="0000:03:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="xhci_hcd"
    ATTRS{device}=="0x0779"
    ATTRS{current_link_width}=="32"
    ATTRS{consistent_dma_mask_bits}=="64"
    ATTRS{enable}=="1"
    ATTRS{numa_node}=="-1"
    ATTRS{max_link_width}=="32"
    ATTRS{acpi_index}=="16777984"
    ATTRS{msi_bus}=="1"
    ATTRS{local_cpulist}=="0-3"
    ATTRS{revision}=="0x00"
    ATTRS{class}=="0x0c0330"
    ATTRS{label}=="usb_xhci"
    ATTRS{subsystem_vendor}=="0x15ad"
    ATTRS{subsystem_device}=="0x0779"
    ATTRS{vendor}=="0x15ad"
    ATTRS{max_link_speed}=="5.0 GT/s PCIe"
    ATTRS{irq}=="18"
    ATTRS{ari_enabled}=="0"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{broken_parity_status}=="0"
    ATTRS{current_link_speed}=="5.0 GT/s PCIe"
    ATTRS{local_cpus}=="00000000,00000000,00000000,0000000f"
    ATTRS{driver_override}=="(null)"
    ATTRS{d3cold_allowed}=="1"


  looking at parent device '/devices/pci0000:00/0000:00:15.0':
    KERNELS=="0000:00:15.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="pcieport"
    ATTRS{class}=="0x060400"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{local_cpus}=="00000000,00000000,00000000,0000000f"
    ATTRS{vendor}=="0x15ad"
    ATTRS{d3cold_allowed}=="1"
    ATTRS{max_link_width}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{device}=="0x07a0"
    ATTRS{driver_override}=="(null)"
    ATTRS{subsystem_vendor}=="0x15ad"
    ATTRS{msi_bus}=="1"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{irq}=="24"
    ATTRS{enable}=="2"
    ATTRS{current_link_speed}=="5.0 GT/s PCIe"
    ATTRS{subsystem_device}=="0x07a0"
    ATTRS{local_cpulist}=="0-3"
    ATTRS{max_link_speed}=="5.0 GT/s PCIe"
    ATTRS{secondary_bus_number}=="3"
    ATTRS{current_link_width}=="32"
    ATTRS{ari_enabled}=="0"
    ATTRS{subordinate_bus_number}=="3"
    ATTRS{revision}=="0x01"
    ATTRS{numa_node}=="-1"


  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

``````
Phone has 
```
```
 ATTRS{configuration}=="mtp"

``````
attribute but camera does have ""(empty). (Actually standart usb flash disk has empty 'configuration' attribute too) . I could not understand it. What does 'configuration' attribute do? Why is it empty for some but not others? Is it the same thing in Configurations section of [this][1] link? Thanks in advance.




  [1]: [https://www.oreilly.com/library/view/linux-device-drivers/0596005903/ch13.html](https://www.oreilly.com/library/view/linux-device-drivers/0596005903/ch13.html)

---

### Post by CelticWarrior on 2021-03-29
Welcome.
It's empty for any standard mass storage device.
Phones started using MTP/PTP a long time ago. They used to act as a standard mass storage indeed but around the time of Android 4.x or 5.x that changed.

---

