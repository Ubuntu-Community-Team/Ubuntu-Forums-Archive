---
title: "simple scan not working properly"
date: 2012-10-27
forum: Ubuntu Studio
---

### Post by oldfogy76 on 2012-10-27
I am using a &quot;try first&quot; bootable ubuntu studio 12-10 DVD.  Simple Scan will scan about 15 percent of the document, and then freeze. If I close the Simple Scan window and try again, it may scan even less before stopping, or it may scan as much as 25 percent and then stop.  I have tried waiting as long as ten minutes with no results.  The scanner appears to be working fine up until it stops, and the partial scan can be saved.  The scanner works OK with Windows XP and Windows 2000 which should rule out any problem with the scanner.  Oldfogy 76

---

### Post by jejeman on 2012-10-28
I didn't saw that you mention which scanner are you using.

Also it may have nothing to do with Simplescan, but with libsane, which are drivers for scanners. Check if/how your scanner is supported on the SANE site.

For example, for my scanner, HP ScanJet 2300c, I have to install an old version of libsane from 10.04 in order to work properly in 300dpi and below. And it gets harder and harder to install such old library.

---

