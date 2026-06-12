---
title: "unable to access gps under gpsbabble unless root"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dmdelorme on 2012-03-23
I am running Ubuntu 12.04 beta 1 i have a Legend HCx usb GPS.
I have been unable to access the gps except as root as this is a real issue with other software i need to allow users to access the device.
i have changes ect/udev/rules.d as per instructions but no luck.

SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003", MODE="666"

david@solaris:~/Desktop$ sudo gpsbabel -T -i garmin -f usb: -o nmea -F -
[sudo] password for david: 
$GPRMC,154709.000,A,4954.361,N,09707.508,W,0.01,324.77,230312,,*16
$GPGGA,154709.000,4954.361,N,09707.508,W,1,00,0.0,224.803,M,0.0,M,,*73
$GPVTG,324.774,T,0,M,0.010,N,0.019,K*58
$GPGSA,A,3,,,,,,,,,,,,,0.0,0.0,0.0*32
$GPRMC,154710.000,A,4954.361,N,09707.508,W,0.03,324.77,230312,,*1C
$GPGGA,154710.000,4954.361,N,09707.508,W,1,00,0.0,224.808,M,0.0,M,,*70
$GPVTG,324.774,T,0,M,0.032,N,0.060,K*56
$GPGSA,A,3,,,,,,,,,,,,,0.0,0.0,0.0*32
$GPRMC,154711.000,A,4954.361,N,09707.508,W,0.03,324.77,230312,,*1D
$GPGGA,154711.000,4954.361,N,09707.508,W,1,00,0.0,224.809,M,0.0,M,,*70
$GPVTG,324.774,T,0,M,0.033,N,0.062,K*55
$GPGSA,A,3,,,,,,,,,,,,,0.0,0.0,0.0*32
^Cdavid@solaris:~/Desktop$ gpsbabel -T -i garmin -f usb: -o nmea -F -
Claim interfaced failed: could not claim interface 0: Operation not permitted

david@solaris:~/Desktop$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 064e:d20c Suyin Corp. 
Bus 001 Device 004: ID 0489:e033 Foxconn / Hon Hai 
Bus 002 Device 003: ID 091e:0003 Garmin International GPS (various models)

Any ideas folks on how i should proceeded

---

### Post by mtux on 2012-03-24
Try with this entry in /etc/udev/rules.d/51-garmin.rules

#garmin etrex rules
SUBSYSTEM=="usb", ATTR{idVendor}=="091e", ATTR{idProduct}=="0003", MODE="0666"

---

### Post by dmdelorme on 2012-03-24
Thanks a bunch it worked. I will pass this on so other can solve this small but annoying problem.):P

---

### Post by howefield on 2012-03-24
Thread moved to "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by cariboo on 2012-03-24
> **dmdelorme said:**
> I am running Ubuntu 12.04 beta 1 i have a Legend HCx usb GPS.
I have been unable to access the gps except as root as this is a real issue with other software i need to allow users to access the device.
i have changes ect/udev/rules.d as per instructions but no luck.

SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003", MODE="666"

david@solaris:~/Desktop$ sudo gpsbabel -T -i garmin -f usb: -o nmea -F -
[sudo] password for david: 
$GPRMC,154709.000,A,4954.361,N,09707.508,W,0.01,324.77,230312,,*16
$GPGGA,154709.000,4954.361,N,09707.508,W,1,00,0.0,224.803,M,0.0,M,,*73
$GPVTG,324.774,T,0,M,0.010,N,0.019,K*58
$GPGSA,A,3,,,,,,,,,,,,,0.0,0.0,0.0*32
$GPRMC,154710.000,A,4954.361,N,09707.508,W,0.03,324.77,230312,,*1C
$GPGGA,154710.000,4954.361,N,09707.508,W,1,00,0.0,224.808,M,0.0,M,,*70
$GPVTG,324.774,T,0,M,0.032,N,0.060,K*56
$GPGSA,A,3,,,,,,,,,,,,,0.0,0.0,0.0*32
$GPRMC,154711.000,A,4954.361,N,09707.508,W,0.03,324.77,230312,,*1D
$GPGGA,154711.000,4954.361,N,09707.508,W,1,00,0.0,224.809,M,0.0,M,,*70
$GPVTG,324.774,T,0,M,0.033,N,0.062,K*55
$GPGSA,A,3,,,,,,,,,,,,,0.0,0.0,0.0*32
^Cdavid@solaris:~/Desktop$ gpsbabel -T -i garmin -f usb: -o nmea -F -
Claim interfaced failed: could not claim interface 0: Operation not permitted

david@solaris:~/Desktop$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 064e:d20c Suyin Corp. 
Bus 001 Device 004: ID 0489:e033 Foxconn / Hon Hai 
Bus 002 Device 003: ID 091e:0003 Garmin International GPS (various models)

Any ideas folks on how i should proceeded

This seems to be an ongoing problem, every release. Has there been a bug report created?

---

### Post by dmdelorme on 2012-03-25
No I did not report this as a bug. Yes it has been an ongoing problem but I was not sure weather it was related to Ubuntu or other software. I did notice that some of the Issues with mounting and unmounting my usb drives have been fixed. Thanks Feel free to post this fix.
I would like to thank the Ubuntu developers and community for all there hard work. 12.04 looks like it will be a great distribution.
 Thanks a bunch....

---

