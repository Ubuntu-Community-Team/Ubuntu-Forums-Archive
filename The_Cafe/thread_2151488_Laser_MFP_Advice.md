---
title: "Laser MFP Advice"
date: 2013-06-04
forum: The Cafe
---

### Post by PipeBoss on 2013-06-04
We're replacing our Canon Pixma MP530 because it died. Due to the cost of replacement ink, we've decided on going with a monochrome laser printer. We need it to be an all-in-one fax/scan/copy/print with auto duplexing. And, it needs to be Ubuntu/linux compatible, of course. Our one desktop has Ubuntu 10.04 (planning to upgrade to 12.04, just haven't gotten around to it yet), and we have a Win7 laptop and a LinuxMintKDE 13 mini-laptop.

Currently I have it narrowed down to 3 possibilities:

[Oki MB451w]("http://www.amazon.com/Data-MB451w-Multifunction-Printer-2400x600/dp/B009B1D4IO")

[Canon MF4880dw]("http://www.amazon.com/Canon-imageCLASS-MF4880dw-Wireless-Monochrome/dp/B008YD1V4Y")

[Canon MF4770n]("http://www.amazon.com/Canon-imageCLASS-MF4770n-Monochrome-Printer/dp/B008YD1V6C/ref=pd_sim_sbs_e_3")

I'm also open to other suggestions.

---

### Post by pdc on 2013-06-04
this was a learning thread for me;

[http://ubuntuforums.org/showthread.php?t=2098805&page=4&highlight=Canon+printer](http://ubuntuforums.org/showthread.php?t=2098805&page=4&highlight=Canon+printer)

post #32 was the how-to 

offering advice on getting the MF4450 to work; using the Canon UFR driver

we got it to work well and work well on the network; 

if you can live with 32bit, that is simpler; but 64bit just requires some stuff installed first; 

the essence for the MF series is install the driver: the Canon UFR driver as described above;

and then register the printer with lpadmin; one is tells lapadmin which ppd file to use with which printer; 

I think now it is very straightforward; 

_________________________________________________________________-

the MF series is bidirectional so one uses cnusb instead of usb

sudo /usr/sbin/lpadmin -p [Printer Name] -m [PPD file] -v cnusb:[device file location] -E

______________________________________________________________________________-

you can see in post #40 the printer came alive; as did the poster!

---

### Post by PipeBoss on 2013-06-04
Thanks for the reply and link.  The Oki seems to be a little less involved in setup... leaning towards that now.

---

### Post by mips on 2013-06-05
HP is usually trouble free.

---

