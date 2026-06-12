---
title: "USB device getting disconnected from guest"
date: 2015-12-29
forum: Virtualisation
---

### Post by jordi-auge-cat on 2015-12-29
Hello,  

I am trying to use a physical usb serial converter on a guest virtual machine. 
After a few hours of correct operation, at some point the device gets disconnected from the guest, and gets connected to the host instead. 
Both the host and the guest are Ubuntu Trusty, on x86_64. I am using kvm with libvirt and virt-manager. 

 The relevant part on the libvirt xml file looks like this:
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x10c4'/>
        <product id='0xea60'/>
      </source>
    </hostdev>

              The virtual machine is started fine, and the device can be accessed correctly. After some hours though, the device disappears from the guest, and appears on the host. 

From the Guest's dmesg: 
[dt des 29 20:04:09 2015] cp210x ttyUSB0: usb_serial_generic_read_bulk_callback - urb stopped: -32 
[dt des 29 20:04:09 2015] cp210x ttyUSB0: usb_serial_generic_read_bulk_callback - urb stopped: -32 
[dt des 29 20:04:09 2015] cp210x ttyUSB0: usb_serial_generic_write_bulk_callback - nonzero urb status: -71
 [dt des 29 20:04:09 2015] usb 1-1: USB disconnect, device number 2 
[dt des 29 20:04:09 2015] cp210x ttyUSB0: cp210x converter now disconnected from ttyUSB0 
[dt des 29 20:04:09 2015] cp210x 1-1:1.0: device disconnected 

 From the Host's dmesg: 
[dt des 29 20:04:04 2015] usb 2-1.3: USB disconnect, device number 3 
[dt des 29 20:04:04 2015] usb 2-1.3: new full-speed USB device number 5 using ehci-pci 
[dt des 29 20:04:04 2015] usb 2-1.3: New USB device found, idVendor=10c4, idProduct=ea60 
[dt des 29 20:04:04 2015] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3 
[dt des 29 20:04:04 2015] usb 2-1.3: Product: CP2102 USB to UART Bridge Controller 
[dt des 29 20:04:04 2015] usb 2-1.3: Manufacturer: Silicon Labs 
[dt des 29 20:04:04 2015] usb 2-1.3: SerialNumber: 1201172 
[dt des 29 20:04:04 2015] cp210x 2-1.3:1.0: cp210x converter detected 
[dt des 29 20:04:04 2015] usb 2-1.3: cp210x converter now attached to ttyUSB0  

If I then stop the vm and start it again, the device gets connected to the guest normally, and operation is resumed.

So, I understand that there's been a USB communication error, and the device has momentarily disconnected. USB devices sometimes do that.  
The question is, why is it not automatically reconnected to the guest, and how can I make it automatically reconnect?

---

