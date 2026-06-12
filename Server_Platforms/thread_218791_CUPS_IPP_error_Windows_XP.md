---
title: "CUPS IPP error Windows XP"
date: 2006-07-19
forum: Server Platforms
---

### Post by -Zoidberg- on 2006-07-19
hey there,

i have installed latest ubuntu server with CUPS,

on the Ubuntu Server there is a HP Colorlaserjet 2550 connected via USB,

i installed the printer via [http://xrsrv1:631/printers/hpclj2550](http://xrsrv1:631/printers/hpclj2550) on my Macbook,
its working perfect.....

but on the other Notebook...Windows XP SP2 i get little problems...

i installed the printer via Network Printer -> Internet Printer -> adress like on the mac.....

i cannot view status of the printer....on the printer settings windows on windows it says connecting...... if there is a local printer installed i can open the print menu from example Openoffice an CAN!!! print on the CUPS Printer...... the only problem is that some programms check the printer status before they allow to submit a printjob.....

i also get these errors in the following logfiles.


access log:

192.168.10.99 - - [19/Jul/2006:08:48:48 +0200] "POST /printers/hpclj2550 HTTP/1.1" 200 75 windows-ext client-error-bad-request


error log:

E [19/Jul/2006:08:48:48 +0200] Missing printer-uri or job-uri attribute!
I [19/Jul/2006:08:48:48 +0200] windows-ext client-error-bad-request: Missing required attributes!

i hope someone could help me.

maybe there is somthing different between installation on mac or windows....

best regards
Bernhard

---

### Post by 666 on 2006-08-01
have same exact problem... strange is the fact that in windows 2000 the printers don't appear offline. I can't see the jobs either, but I can Print, PAUSE and cancel jobs...

---

### Post by zwanzig on 2007-09-08
I had the exact same problem with a HP P2015, workaround for me:
[http://ubuntuforums.org/showthread.php?p=3332506](http://ubuntuforums.org/showthread.php?p=3332506)

---

