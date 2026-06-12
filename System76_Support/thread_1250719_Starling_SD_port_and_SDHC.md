---
title: "Starling SD port and SDHC"
date: 2009-08-26
forum: System76 Support
---

### Post by paulbary on 2009-08-26
Perhaps someone with more experience could answer ... I bought a new digital camera with an 8GB SDHC card ... when I plug the SDHC card into my Starling it is not recognized. Is the Starlings's SD port unable to deal with the SDHC format?

Paul

---

### Post by thomasaaron on 2009-08-27
Hi, Paul.

Good to see ya. ;)

Hey, what did the sdhc card come from? You may have a filesystem incompatibility issue.

Open a terminal and run...

tail -f /var/log/syslog

..and *then* insert the card and see what output it gives you.

---

### Post by paulbary on 2009-08-27
I'll do that tonite ... the card was formatted by a Canon SD1200
camera and I would suppose that it would be fat32 or ntfs. If I plug the camera into a usb port it pops up as a connected device and the files are available ... pretty cool actually and a nice way to view pictures. I have seen some general postings about SD
reader/ports having problems with sdhc so that might be the case.
Not that big a deal really as you can get a usb sdhc reader for
less than $20 ... Hope you had some fun time off ...

Cheers

---

### Post by paulbary on 2009-08-29
Here's the output that shows the failure ... btw ... a 2GB chip is seen and mounts fine ... also as I previously mentioned if the camera is connected by usb the sdhc works fine ... It appears the reader just has a problem with sdhc ...

Paul


Aug 29 16:06:14 system76-netbook kernel: [  104.067334] sdhci-pci 0000:01:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 29 16:06:14 system76-netbook kernel: [  104.067352] sdhci-pci 0000:01:00.2: Refusing to bind to secondary interface.
Aug 29 16:06:14 system76-netbook kernel: [  104.067366] sdhci-pci 0000:01:00.2: PCI INT A disabled
Aug 29 16:06:14 system76-netbook kernel: [  104.430559] mmc0: error -84 whilst initialising SD card

---

### Post by paulbary on 2009-09-01
Think I have confirmed what I suspected ... bought a 8GB card with USB Reader included and everything works perfectly on my Starling ... so it does appear to be a limitation with SDHC on the built-in card port ... maybe an enhancement on future Starling hardware should be considered ...
BTW ... Amazon has a great deal on this ... $22 for the combine reader with 8GB card ... sizes other than 8GB are available and nicely priced ... the brand is Transcend.

P.

---

