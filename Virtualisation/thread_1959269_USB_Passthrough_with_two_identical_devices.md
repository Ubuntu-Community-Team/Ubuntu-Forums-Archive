---
title: "USB Passthrough with two identical devices"
date: 2012-04-15
forum: Virtualisation
---

### Post by henfri on 2012-04-15
Hello,

I'd like to pass throug two identical devices to my VM. (using libvirt, guest is debian). For one device, it works like this:
```
            <hostdev mode='subsystem' type='usb'>
                          <source>
                             <vendor id='0x4fa'/>
                             <product id='0x2490'/>
                           </source>
                          <boot order='2'/>
                       </hostdev>
```But now, I have another device just like this one:
```

Bus 001 Device 007: ID 04fa:2490 Dallas Semiconductor DS1490F 2-in-1 Fob, 1-Wire adapter
Bus 001 Device 005: ID 04fa:2490 Dallas Semiconductor DS1490F 2-in-1 Fob, 1-Wire adapter

```Unfortunately, only one of these two devices appears for the Host.

Now, there's this option to pass devices:
```
 <address bus='0x06' device='0x02''/>
```But the Bus/Slot can/might change...  Maybe this can be overcome by udev (and maybe this is the default in ubuntu? can someone confirm?)

I have tried the latter syntax aswell. Here the log-file:
```
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc -cpu qemu32 -enable-kvm -m 256 -smp 1 -name WG -uuid fd90f0d6-122c-992f-a399-4105ee30d6e3 -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/WG.monitor,server,nowait -monitor chardev:monitor -boot c -drive file=/var/lib/zentyal/machines/WG/WG-Test.qcow2,if=scsi,index=0,boot=on,format=qcow2 -net nic,macaddr=00:16:3e:5d:c7:9e,vlan=0,name=nic.0 -net tap,fd=29,vlan=0,name=tap.0 -serial none -parallel none -usb -usbdevice mouse -vnc 0.0.0.0:0,password -k de -vga cirrus -usbdevice host:04fa:2490 -usbdevice host:04fa:2490
usb_create: no bus specified, using "usb.0" for "usb-host"
husb: open device 1.5
husb: config #1 need -1
husb: 1 interfaces claimed for configuration 1
husb: grabbed usb device 1.5
usb_create: no bus specified, using "usb.0" for "usb-host"

```

What's odd:
```
 -usbdevice host:04fa:2490 -usbdevice host:04fa:2490
``` 
And this, although I had used the bus/device syntax...



So, what would you recommend?

Regards,
Hendrik

---

