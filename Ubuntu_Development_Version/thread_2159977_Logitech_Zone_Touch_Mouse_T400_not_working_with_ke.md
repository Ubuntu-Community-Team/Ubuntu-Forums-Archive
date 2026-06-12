---
title: "Logitech Zone Touch Mouse T400 not working with kernel 3.10"
date: 2013-07-05
forum: Ubuntu Development Version
---

### Post by galactus66 on 2013-07-05
HI,

I just installed Ubuntu 13.10 ( before I had 13.04, raring ringtail with with kernel 3.9).
Now my mouse is not working at all, but I do see that the usb receiver is detected:

kernel: [ 1803.789083] usb 3-4: USB disconnect, device number 4
Jul  5 11:43:01 galactus kernel: [ 1806.932330] usb 3-4: new full-speed USB device number 5 using xhci_hcd
Jul  5 11:43:01 galactus kernel: [ 1806.950900] usb 3-4: New USB device found, idVendor=046d, idProduct=c52b
Jul  5 11:43:01 galactus kernel: [ 1806.950912] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jul  5 11:43:01 galactus kernel: [ 1806.950916] usb 3-4: Product: USB Receiver
Jul  5 11:43:01 galactus kernel: [ 1806.950919] usb 3-4: Manufacturer: Logitech
Jul  5 11:43:01 galactus mtp-probe: checking bus 3, device 5: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4"
Jul  5 11:43:01 galactus mtp-probe: bus: 3, device: 5 was not an MTP device
Jul  5 11:43:01 galactus kernel: [ 1806.956315] logitech-djreceiver 0003:046D:C52B.0009: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-4/input2

Cfouad@galactus:~uname -a
Linux galactus 3.10.0-2-generic #9-Ubuntu SMP Mon Jul 1 18:36:19 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

lsmod | grep hid_logitech
hid_logitech_dj        18437  0 
hid                   101145  2 usbhid,hid_logitech_dj

locate hid-logitech
/lib/modules/3.10.0-2-generic/kernel/drivers/hid/hid-logitech-dj.ko
/lib/modules/3.10.0-2-generic/kernel/drivers/hid/hid-logitech.ko


Any ideas how to go from here ?

Thanks,

Fouad

---

### Post by dino99 on 2013-07-05
To get my LX5 logitech usb mouse working with 3.10, i need these packages installed: locomo, libgii1, inputattach

---

### Post by galactus66 on 2013-07-05
> **dino99 said:**
> To get my LX5 logitech usb mouse working with 3.10, i need these packages installed: locomo, libgii1, inputattach

Thanks, I st gave it a shot and installed those too, but without success, unfortunatly..

---

### Post by galactus66 on 2013-07-06
Got it working with **Solaar**, a Linux device manager for Logitech’s unifying receiver peripherals!
[http://pwr.github.io/Solaar/](http://pwr.github.io/Solaar/)

After instalation, I just switched the mouse off and on and it "magically" worked!
The added benefit is that I now can monitor also the battery status of the peripherals too.

---

### Post by jamesl-bestweb on 2013-12-29
The problem with the T400 is there is NO way to get the middle button to behave like a proper unix middle-button.  And chording the left-right buttons doesn't work either.  Could be a nice mouse otherwise, but without the middle button it is completely USELESS.

---

### Post by cariboo on 2013-12-30
Seeing as we're in the middle of the Trusty development cycle, there is no need for this thread any more. Closed.

---

