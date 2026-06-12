---
title: "No cdrom drive in guest W2KProf"
date: 2008-11-22
forum: Virtualisation
---

### Post by Xkutzy on 2008-11-22
I have a problem with accessing the CDROM drive from my guest OS. My host is Ubuntu Hardy. I am running VMWare 1.0.6. The guest is W2KProf created using VMWare converter.

I have added the CDROM to the virtual machine. The device is present in device manager as VMWare IDE CDR00  but in windows explorer the CDROM drive is missing.

I've tried changing various settings for the guets CDROM but to no avail. Other than that my virtual machine seems to be working fine. The only other issue is the problem about the warning about the wrong GCC version mentioned elsewhere. I'd like to be able to access the CDROM to install some scanner software as the scanner is not compatible with Linux. (Don't buy Canon is my advice).

Does anyone have any thoughts as to what may be causing the CDROM not to appear?

---

### Post by Xkutzy on 2008-11-24
I have done a bit more digging and found that W2K is having problems with the VMWare drivers for the CD ROM. If you disable the device and then try to re-enable it you get the message

"This device is not working properly because Windows cannot load the drivers required for this device. (Code 31)"

I have tried both the IDE and SCSI CD ROM options in VMWare both with the same results.

Does this give anyone any more clues?

---

