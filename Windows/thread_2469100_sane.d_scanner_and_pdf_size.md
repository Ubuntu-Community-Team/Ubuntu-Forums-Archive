---
title: "sane.d scanner and pdf size"
date: 2021-11-19
forum: Windows
---

### Post by atux on 2021-11-19
I have an USB multifunction printer at my SoHo and by using CUPS  i manage to print from all PCs/android devices. Also by using SANE.D i have the scanning available from LAN. so far so good. 
The problem is the size of the scanned pdf documents is HUGE. i am using sanewinDS from the Windows machines to get the scanning. 
Any ideas what to do in order to minimise the size of pdf, please? Any other software that i could use from Windows PC to get the scanner, please?

---

### Post by HermanAB on 2021-11-20
Howdy,
You can resample and resize PDFs with Imagemagick “convert”.  For example change it to 300 dpi and BW for small file size. Some googling for examples with convert will get you going.

---

### Post by kurt18947 on 2021-11-20
I have a similar problem which appears to be device related. I had a Brother MFC-6490CW for years which produced good quality small PDFs mostly using Gscan2pdf. I recently replaced that machine with a Brother MFC-J4535. PDFs produced using true gray or even black & white were relatively huge - around 1 Mb compared to perhaps 70Kb. The files produced by scanning at 24 bit color were smaller than true gray or black and white. I also noticed that PDFs produced using the Document Scanner app are smaller than the same page(s) scanned using Gscan2pdf.

---

### Post by coffeecat on 2021-11-20
> **atux said:**
>  i am using sanewinDS from the Windows machines to get the scanning. 
Any ideas what to do in order to minimise the size of pdf, please? Any other software that i could use from Windows PC to get the scanner, please?

This appears to be a Windows question, not Ubuntu, therefore I've moved this thread to the **Windows** sub-forum.

---

