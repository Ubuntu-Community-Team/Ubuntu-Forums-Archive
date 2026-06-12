---
title: "HowTo: Pixart 093a:2468 webcam in 8.04 (work with skype)"
date: 2008-07-26
forum: Ubuntu Studio
---

### Post by eliabramo on 2008-07-26
I was trying to install my pixart webcam. I followed the post:
[http://ubuntuforums.org/showthread.php?t=622351](http://ubuntuforums.org/showthread.php?t=622351)

But it didn't work.

Solution: the gspca-source in ubuntu repo is version 1.00.18. In debian site the version is 1.00.20 , and now it works, even in Skype!

[LIST=1]
[*]download the gspca-source from [http://ftp.de.debian.org/debian/pool/main/g/gspca/gspca_01.00.20-1.tar.gz](http://ftp.de.debian.org/debian/pool/main/g/gspca/gspca_01.00.20-1.tar.gz)

[*]unpack it to /usr/src/modules

[*]install the driver with: m-a i-a gspca or with /usr/src/modules/gspca/gspca_build

[*]load the driver: sudo modprobe gspca
[/LIST]

---

### Post by tgyorgyi on 2008-09-13
I have the same webcam. Doing the above instructions did some improvement: when I hit the "test" button in the Skype video settings, the webcam's led starts to flicker, then the light stays on permanently until I close the settings window. However, no picture, the test screen stays empty.

---

