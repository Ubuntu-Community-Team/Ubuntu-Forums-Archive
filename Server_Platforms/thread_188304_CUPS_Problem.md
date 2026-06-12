---
title: "CUPS Problem"
date: 2006-06-03
forum: Server Platforms
---

### Post by rbrugman on 2006-06-03
Hey Everyone,
I'm having trouble getting my HP Deskjet 932C working under cups.  I'm using the web backend.  With the previous version I was using under breezy, USB showed up on the list under devices, but now it just shows LPT, SCSI, etc.  No USB.  All my usbcore and usbhdi are loaded as modules.  phpsysinfo shows that the deskjet is connected to my server, but I can't get it configured in CUPS.  Does anyone have any suggestions?

Thanks,
Robert

---

### Post by silentb on 2006-06-04
CUPS' usb support seems somewhat broken. I switched back to Breezy just because of this.

---

### Post by rbrugman on 2006-06-04
I will agree that USB seems broken in CUPS, but luckily my laser printer isn't USB.  Now that school's over, the chance of me needing color for a while isn't that great.

I even installed 1.2.1 from source.  No luck there either.


Robert

---

### Post by rbrugman on 2006-06-05
I found a solution to my problem.  I loaded the usblp module and my printer showed up!

modprobe usblp

Just add usblp to your modules file and it will load on startup.


Robert

---

