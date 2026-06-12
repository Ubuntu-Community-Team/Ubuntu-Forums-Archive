---
title: "DVB problem"
date: 2013-12-12
forum: Ubuntu Development Version
---

### Post by P-I H on 2013-12-12
The kernel 3.12.0-7-generic doesn't start my DVB tuner.
This is the dmesg log
```
[    4.966288] em28174 #0: Identified as PCTV nanoStick T2 290e (card=78)
[    4.966291] em28174 #0: v4l2 driver version 0.2.0
[    4.985028] em28174 #0: V4L2 video device registered as video1
[    4.985032] em28174 #0: dvb set to isoc mode.
[    4.985865] usbcore: registered new interface driver em28xx
[    5.010326] r8169 0000:06:00.0 eth0: link down
[    5.010379] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.010403] r8169 0000:06:00.0 eth0: link down
[    5.010642] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.018596] tda18271 1-0060: creating new instance
[    5.040411] usb 1-3.3: new low-speed USB device number 4 using ehci-pci
[    5.045346] tda18271_read_regs: [1-0060|M] ERROR: i2c_transfer returned: -19
[    5.045394] Error reading device ID @ 1-0060, bailing out.
[    5.045396] tda18271_attach: [1-0060|M] error -5 on line 1285
[    5.045439] tda18271 1-0060: destroying instance

```

With 13.10 on the same computer the dmesg log looks like this

```
[    4.597602] em28174 #0: Identified as PCTV nanoStick T2 290e (card=78)
[    4.597606] em28174 #0: v4l2 driver version 0.2.0
[    4.612978] em28174 #0: V4L2 video device registered as video1
[    4.612983] em28174 #0: dvb set to isoc mode.
[    4.613757] usbcore: registered new interface driver em28xx
[    4.629424] tda18271 1-0060: creating new instance
[    4.637247] TDA18271HD/C2 detected @ 1-0060

```

---

### Post by cariboo on 2013-12-12
It looks like there is a problem with the driver, I'd suggest you file a bug report against the kernel, using:

```
apport-bug linux
```

---

### Post by P-I H on 2013-12-13
Reported
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1260749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1260749)

---

