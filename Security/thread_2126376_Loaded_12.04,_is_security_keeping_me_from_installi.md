---
title: "Loaded 12.04, is security keeping me from installing a printing driver?"
date: 2013-03-16
forum: Security
---

### Post by alvinmoneypit on 2013-03-16
I wonder this because Ubuntu offers a driver, when I go to activate it, it fails to download saying "untrusted source".  So why or how could ubuntu offer a driver, then say it is untrusted?  So I tried to install my driver various ways from 3 different [HowTO's]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters"), none were successful, so thinking security settings might be an issue.  I ran the same printer on Ubuntu 10.10, but recalling that install, I had security/permissions problems with it, but not necessarily the print driver in that case.

Any suggestions, insights shared are appreciated.

---

### Post by cariboo on 2013-03-17
The driver is marked untrusted, because it isn't maintained by Ubuntu, you shouldn't have any problems just installing it normally.

---

### Post by alvinmoneypit on 2013-03-17
Yes, but that was the message I got when I tried to download/activate it.  Last night, all of a sudden the OS allowed the download sometime after I loaded Adobe Reader and Flash and AIR.  That driver hasn't worked except to be loaded and allow my OS to see the printer through the GUI and see some settings.  However, it still isn't working, I keep trying to print either through the "Test Page" or through just printing a document.  I was mysteriously able to install my old z600 driver, too.  It doesn't work yet either, still doesn't seem to be communicating with the printer.  I can turn off the printer, buth the GUI says it's "idle".  

Any ideas of what I may be missing?  -I've rebooted several times with the printer off and on, and plugged into a different usb slot, to no apparent effect.

---

### Post by alvinmoneypit on 2013-03-17
What is "Attached devices"?  It's not highlighted so I can't see what it offers, but I would assume my printer should qualify, but it doesn't seem to appear there yet.

---

### Post by cariboo on 2013-03-17
Have you tried accessing the printer via the cups local web page? Open a browser and in the url bar type:

```
http://localhost:631
```

---

### Post by alvinmoneypit on 2013-03-18
no, I hadn't, but I did just now.  It shows my printer and offers the settings, policies, etc.  Has maintenance section for test page, still doesn't print.  Tried a couple different drivers, not working so far, one driver was able to load the paper, but it didn't print anything and eventually ejected the paper properly.

---

### Post by alvinmoneypit on 2013-03-18
I got it working by using[ this HowTo]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters") to locate the [Z600 driver]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.4.deb") and the i386 libstdc++5 I got from Synaptic.  First got libstdc++5, then downloaded the Z600 driver.  Get the ppd file out of the package by simply clicking on the package and extracting the ppd with Archive Manager. 
Then  I installed with the onboard printer installer- 1) select printer, click forward; 2) program searches for driver, click 'cancel' if it finds one, click "forward"; 3 "Choose Driver" screen comes up, click "Provide PPD file" navigate the browser lookup to where you extracted the PPD of Z600 and click forward.  Then your printer is loaded and you can try to print.  Hope this works for other seekers.

---

