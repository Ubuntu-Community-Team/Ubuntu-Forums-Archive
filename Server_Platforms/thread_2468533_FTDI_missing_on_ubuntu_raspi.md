---
title: "FTDI missing on ubuntu raspi"
date: 2021-11-02
forum: Server Platforms
---

### Post by ruman on 2021-11-02
Hello,
I have **Ubuntu server Raspi 5.13.0** installed on **Raspberry Pi 4** and I am willing to connect a device through usb as serial (3D printer).
The device is detected in lsusb but not mounted in /dev.
My understanding is that this is because of FTDI module missing.
I have been searching for a while now on how to get FTDI module activated for Ubuntu Raspi but without success.
Can anyone help me solve this issue?

---

### Post by MAFoElffen on 2021-11-03
I suspect that no-one has answered yet, as from what you have provided, more information is needed.

"5.13.0" is mostly the version of Kernel, not the Release version of Ubuntu
```

lsb_release -sr

```
...would provide that.

What is the Brand model of 3D printer.

---

### Post by ruman on 2021-11-03
I am using version 21.10.

3D printer is Artillery Genius.

When I connect it, I can see it recognized with dmesg but nothing if I grep on FTDI.
```
[125457.502650] usb 1-1.3: new full-speed USB device number 6 using xhci_hcd
[125457.608833] usb 1-1.3: New USB device found, idVendor=1a86, idProduct=7523, bcdDevice= 2.64
[125457.608863] usb 1-1.3: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[125457.608880] usb 1-1.3: Product: USB Serial
[126725.424949] usb 1-1.3: USB disconnect, device number 6
```

No ttyUSB0 created in /dev.

When running modprobe ftdi_sio, I get this.
```
modprobe: FATAL: Module ftdi_sio not found in directory /lib/modules/5.13.0-1009-raspi
```

That's the reason I think that FTDI is the issue.

---

