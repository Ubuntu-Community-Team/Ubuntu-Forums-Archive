---
title: "KVM USB Virtualisation"
date: 2009-02-02
forum: Virtualisation
---

### Post by vetch101 on 2009-02-02
Hi everyone,

Does anyone know why when I put host USB devices into the libvirt xml files, running "define" on them seems to strip out the relevant code?

I am running Intrepid, and I used this info as my basis...

 USB and PCI devices

USB and PCI devices attached to the host can be passed through to the guest using the hostdev element. since after 0.4.4 for USB and 0.6.0 for PCI (KVM only):

          ...
	  <hostdev mode='subsystem' type='usb'>
	    <source>
	      <vendor id='0x1234'/>
	      <product id='0xbeef'/>
	    </source>
	  </hostdev>
	  ...

From [http://libvirt.org/formatdomain.html#elementsUSB](http://libvirt.org/formatdomain.html#elementsUSB)

Anyone have any ideas...?

Does the Intrepid build not support them?

If not, how can I use host USB devices?

Cheers,

Jx

---

### Post by gerni on 2009-02-04
hi!
I also use Intrepid and try to connect an usb-device (a printer) to my virtual "kvm-print-server" - i use the same syntax like you but i don't have the problem of "striping out the relevant" code of the xml file. By "define" you mean "virsh define machine.xml" - am i right?
But i also couldn't manage to "see" the usb-device in my guest.

The relevant part of my config is:
```
    
<hostdev mode='subsystem' type='usb'>
   <source>
      <vendor id='0x0482'/>
      <product id='0x0011'/>
   </source>
</hostdev>

```

I examined the vendor and product id with "lsusb" at the host. I get:
Bus 004 Device 003: ID 0482:0011 Kyocera Corp.

When i execute lsusb at the guest i get:
Bus 001 Device 001: ID 0000:0000

...strange

Does anybody know whats wrong here?

---

### Post by vetch101 on 2009-02-04
> **gerni said:**
> hi!
I also use Intrepid and try to connect an usb-device (a printer) to my virtual "kvm-print-server" - i use the same syntax like you but i don't have the problem of "striping out the relevant" code of the xml file. By "define" you mean "virsh define machine.xml" - am i right?
But i also couldn't manage to "see" the usb-device in my guest.

The relevant part of my config is:
```
    
<hostdev mode='subsystem' type='usb'>
   <source>
      <vendor id='0x0482'/>
      <product id='0x0011'/>
   </source>
</hostdev>

```

I examined the vendor and product id with "lsusb" at the host. I get:
Bus 004 Device 003: ID 0482:0011 Kyocera Corp.

When i execute lsusb at the guest i get:
Bus 001 Device 001: ID 0000:0000

...strange

Does anybody know whats wrong here?

Hi,

Sounds like you're doing exactly the same as me...

I'm running an EBox PDC and wanted to use it to do print serving as well through the USB...

If you check the /var/log/libvirt/qemu/VirtualMachineName.log you'll see that it isn't attaching the usb device into the kvm command... It's like it just strips it out...

Is it just that it needs a newer version of libvirt?

Will it be in time for Jaunty?

Jx

---

### Post by gerni on 2009-02-04
> **vetch101 said:**
> Hi,

Sounds like you're doing exactly the same as me...

I'm running an EBox PDC and wanted to use it to do print serving as well through the USB...

If you check the /var/log/libvirt/qemu/VirtualMachineName.log you'll see that it isn't attaching the usb device into the kvm command... It's like it just strips it out...

Is it just that it needs a newer version of libvirt?

Will it be in time for Jaunty?

Jx

Now that i checked the log and noticed that kvm is invoked with the corresponding usbdevice command (-usbdevice host:0482:0011) i remember that i upgraded libvirt some weeks ago to version 0.4.6 via the jaunty repository. So it seems that the problem you described can be resolved with a higher version of libvirt but there is a further persisting problem concerning usb devices since it doesn't work for me also :(

---

### Post by gerni on 2009-02-04
ok, i figured out that i have forgotten to mount usbfs:

```
mount -t usbfs usbfs /proc/bus/usb/
```

or an entry in fstab:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

now i see the attached device with lsusb in my guest, but cups does not recognize the printer and dmesg on the guest tells me:

```

[    4.836592] usb 1-2: device descriptor read/64, error -71
[    5.507890] usb 1-2: device descriptor read/64, error -71
[    5.723666] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   10.256282] usb 1-2: configuration #1 chosen from 1 choice

```

and on the host:
```

[24377.872044] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24377.923037] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24377.973036] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.023037] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.073038] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.121038] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.171040] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.221038] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.271039] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.532041] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.581038] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.631037] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.682038] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.731038] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.781037] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.831038] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.881041] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24378.931037] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110
[24379.302043] usb 4-2: usbfs: USBDEVFS_CONTROL failed cmd kvm rqt 128 rq 6 len 64 ret -110

```


...i've no idea  :-s

---

### Post by gerni on 2009-02-05
finally my virtual printserver works like expected :P
The problem was that the default kernel of ubuntu JEOS doesn't support very much hardware... ;)
I installed linux-image-server and suddenly cups recognizes my usb-printer!

---

