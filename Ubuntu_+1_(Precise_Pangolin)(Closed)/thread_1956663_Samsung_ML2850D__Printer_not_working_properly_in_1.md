---
title: "Samsung ML2850D  Printer not working properly in 12.04 Beta"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by weiersc on 2012-04-11
Hi,

My Samsung ML2850D printer worked without many hitches in 11.10. When I installed 12.04 the printer started acting erratically. 

The recommended driver would cause the printer to begin printing without going through its usual warm-up routine. Which would cause the printer to just make a buzzing noise and not produce anything untill switched off and on. Then when I tried to print over the network it would push out pages and pages with funny characters at the top of the page in stead of producing an actual document.

I changed the drivers (there seems to be a second one available) and that brought a little bit more stability (a proper warm-up routine), but as soon as I tried something fancy like print double sided pages from the pdf viewer, it would push out pages and pages of funny characters again.

Now I've been an enthusiastic Ubuntu user since the beginning, but I've never figured out how the bug reporting process works. I tried to report a bug, but the apport programme would not allow me to select a printing problem and I am not sure what process I need to identify to provide a process number. (Is the problem with CUPS? Is the problem with the printer driver itself?)

I sense that I should report it somewhere. Perhaps somebody could point me in the right direction.

LOL - and perhaps on the off chance somebody will have a solution.

---

### Post by rtalcott on 2012-04-11
FWIW I have a 2950 that was acting very weird with the 2950 driver...someone here suggested using **Samsung ML-3050, 2.0.0** and that works well...YMMV but maybe it's worth trying...also...my printer goes to sleep and the network won't wake it up...I need to do that manually.
rt

---

### Post by tractor on 2012-04-11
I had a problem with 12.04 Beta and a Samsung ML-1710. Installing a new PPD seemed to solve the problem, at least so far. Go to [www.openprinting.org](www.openprinting.org) and find your Samsung printer model. The recommended driver for me was the spliX driver, but I scrolled on down the page and found a PPD from GDI and installed it, and now the printer seems to be working perfectly. To install a PPD, simply open the printer dialog box, then right click on the printer model and select properties. On the make and model line click on the change button, select provide PPD, and then browse to where you downloaded the PPD to. Very simple. I had to do the same thing for a Konica-Minolta black and white laser for Ubuntu 11.10 to get it to work properly.
Update! No, changing the PPD didn't fix the problem. Sorry folks.

---

### Post by Nick Payne on 2012-04-11
Have you tried the Linux driver from Samsung: [http://www.samsung.com/sg/support/model/ML-2850D/XIP-downloads?isManualDownload=true]("http://www.samsung.com/sg/support/model/ML-2850D/XIP-downloads?isManualDownload=true")

---

