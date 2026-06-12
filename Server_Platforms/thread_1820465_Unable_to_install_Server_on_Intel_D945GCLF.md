---
title: "Unable to install Server on Intel D945GCLF"
date: 2011-08-07
forum: Server Platforms
---

### Post by steveb7 on 2011-08-07
I recently decided to convert my old NAS gox from Gentoo to Unbuntu Server. For reasons that I do not understand I cannot install 10.04 or 11.04 on it. I've downloaded both the i386 and the AMD64 ISO images to the same machine, burned the the image on the same DVDRW drive onto the same CDRW disc but when I try to install on the D945GCLF board, it consistently fails at the same step - Unable to install base system.

The ISO image all indicate a good MD5 sum and I've burned the ISO image at the slowest possible rate. I've even tried moving the image onto a USB drive and installing from it - same error. 

The D945GCLF has parallel and serial ports disabled; I'm using the SATA drive for the OS and installing from a USB CDROM drive.

Any suggestions on how to resolve this? A google search was inconclusive.

---

### Post by steveb7 on 2011-08-08
I found a reference in the forums that suggested installing from 8.04 an then upgrading to 10.04. That seemed to do work.

---

### Post by Gyokuro on 2011-08-08
It's always good to check intel's support site (for your board): [http://www.intel.com/support/motherboards/desktop/d945gclf/sb/CS-029475.htm](http://www.intel.com/support/motherboards/desktop/d945gclf/sb/CS-029475.htm)

Ubuntu 8.04 is supported so I do not know why you have a problem to install 10.04.3 (Intel is hinting for 8.04 to disable the onboard NIC during install, however for a newer kernel on 8.04, support changed to native).

---

