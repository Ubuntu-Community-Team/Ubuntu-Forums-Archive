---
title: "ubuntu-server-upgrade malformed ubuntu-desktop-installation"
date: 2012-06-01
forum: Server Platforms
---

### Post by dschinn1001 on 2012-06-01
Hello Ubuntu-Cracks,

I had Ubuntu 12.04 installed and wanted to upgrade it with ubuntu-server-dvd, because
I wanted to change the desktop-installation into a server-installation.

This did not work entirely.
It seems that usb resp. scsi is malformed in the /dev - files.

brasero is not recognizing my usb-dvd-drive any more.
I can only access and burn via terminal with mkisofs and cdrecord.
But cdrecord -scanbus shows usb-device on 4,0,0
while
wodim -scanbus shows same usb-device on 6,0,0

This is reason why brasero is not working.
How can I fix this malformed usb-recognition of dvd-drive ?

For hints thanks.
Regards.
dschinn1001

---

### Post by dschinn1001 on 2012-06-01
Hello again,

I found out that udev-packages were "removed" ?

I installed them again, but this does not help ...

somehow my usb-dvd-drive cannot read CD's resp. DVD's ?
but it can burn CDs or DVDs without problem (in terminal - not with brasero).

:confused:

---

