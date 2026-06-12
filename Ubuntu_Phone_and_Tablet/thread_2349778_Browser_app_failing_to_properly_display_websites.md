---
title: "Browser app failing to properly display websites"
date: 2017-01-18
forum: Ubuntu Phone and Tablet
---

### Post by J-Linux on 2017-01-18
Hi all

As of several days ago, the Browser app on my Meizu Pro 5 cannot properly display Amazon, Gumtree, and several other popular websites.

The app displays text but no graphics or images. This effectively renders the websites unuseable.

The problem arose spontaneously and for no apparent reason. Is anyone else experiencing similar difficulties? And does anyone know what to do?

J-Linux

---

### Post by markusinmunich on 2017-01-18
Hi, I have the same problem. There seems to be an issue with the ssl certificates from Symantec and GeoTrust. If you try to open amazon.com in the web browser you get the message that the certificate could not be validated. I have no solution. The certificates of the sites are OK and they work on other browsers.

---

### Post by wgarcia on 2017-01-18
I confirm this also on a BQ Acquaris E5. Is there a bug report?

---

### Post by J-Linux on 2017-01-19
I haven't lodged a bug report. I didn't know whether there'd be much point given everything that's going on with the move to snaps or whatever they're called.

---

### Post by wildmanne39 on 2017-01-19
You should always file a bug report or the issue has not chance of getting resolved.

---

### Post by wgarcia on 2017-01-19
According to some mails in the ubuntu phone mailing list there is actually going to be a OTA 15, just focused on oxide, that is the web browser. So it maybe very worthy to open a bug report, especially if it is a small bug that can be cherry picked.

---

### Post by J-Linux on 2017-01-19
I've opened a bug report on the Launchpad webpage for the Browser app.

---

### Post by philhughes on 2017-01-19
This happened with the out of date chromium browser on the desktop a few weeks back. As a workaround until it was updated, you could export the certificates from Firefox and import them into Chromium. However, I don't see any means to import certificates into the UT browser. A job for some enterprising individual :)

---

### Post by J-Linux on 2017-01-24
The problem is going to be fixed in OTA15, which is apparently due at the end of this month. You can read more at 

[http://www.omgubuntu.co.uk/2017/01/ubuntu-ota-15-will-let-ubuntu-phone-owners-browse-amazon](http://www.omgubuntu.co.uk/2017/01/ubuntu-ota-15-will-let-ubuntu-phone-owners-browse-amazon)

The release date for OTA15 is mentioned by someone in the comments section.

---

