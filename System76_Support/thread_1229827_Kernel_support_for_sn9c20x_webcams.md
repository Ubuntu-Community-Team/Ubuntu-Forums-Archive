---
title: "Kernel support for sn9c20x webcams"
date: 2009-08-02
forum: System76 Support
---

### Post by brijohn on 2009-08-02
Support for the sn9c20x chipset used in the SERP2's webcam will finally be supported with the upcoming 2.6.31 kernel release, it is already in the recent rc5 release. This also means that Karmic will support these webcams since it will be using the 2.6.31 kernel.

The driver included in 2.6.31 is based off of the code from the out of tree microdia driver but using the kernel's gspca webcam framework instead. The driver is also included in the current v4l-dvb ([http://linuxtv.org](http://linuxtv.org)) repository as well.

Regards,
Brian Johnson

---

### Post by viroos on 2009-09-21
Hi i got
Genius slim 1320 with (sn29c202AFG chip). I updated my kernel.

I'm forcing gspca with:
```
echo -n "0x458 0x704a" > /sys/bus/usb/drivers/sn9c20x/new_id
```

But unfortunately got:
```
[ 2681.447806] gspca: probing 0458:704a
[ 2681.465805] sn9c20x: OV9650 sensor initialization failed

```

TIA for help.

regards,
Maciej

---

### Post by brijohn on 2009-09-27
Viros,

In order for your camera to work i need to know what image sensor your camera uses. the easiest way to figure that out will be for you to install the driver on windows and then look in the C:\windows\inf directory for a file called snp2std.inf. Search that file for the following VID_0458 and you should find a line that tells you what sensor is sued in your camera.

Brian Johnson

---

