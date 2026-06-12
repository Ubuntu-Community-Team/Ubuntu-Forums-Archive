---
title: "CUPS-PDF: standard output folder changed"
date: 2016-01-04
forum: Ubuntu/Debian BASED
---

### Post by ulli-basel on 2016-01-04
Hello world, 

I am new to the forum. I have been using Ubuntu (elementary OS; I hope it is o.k. if I show up in this forum) for about a year now and I am very happy with it. The elementary OS distro is great. 

About 3 months ago, from one day to the other, new pdf-files did not show up in the /home/pdf folder. I tried everything even uninstalled CUPS-PDF and reinstalled it. Did not change anything. I finally found the pdf-files in 
/var/spool/cups-pdf/<username>

How can I reset that either to the standard folder or any other folder? 
On my system there is no configuration file
/etc/cups/cups-pdf.conf
Instead there is a file
/etc/cups/printers.conf
with the following section right at the beginning: 

<Printer Generic-CUPS-PDF-Printer>
UUID urn:uuid:a9c6fcaf-f15e-3d95-6ee8-8e4d94d8c658
Info Generic CUPS-PDF Printer
MakeModel Generic CUPS-PDF Printer
DeviceURI cups-pdf:/
State Idle
StateTime 1449653960
Type 8450124
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job

Where do I find the definition of the output folder and how can the be changed?
Thx for any help. I know a lot has been written about CUPS-PDF, the generation of pdf-files in general, etc.. Sorry if this issue has been adressed already. 

Ulrich

---

### Post by howefield on 2016-01-04
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

