---
title: "[SOLVED] CUPS Print Server"
date: 2008-09-07
forum: Server Platforms
---

### Post by Dr Small on 2008-09-07
I hooked up a HP Photosmart 7350 to my server via USB, installed CUPS by running:
```
sudo apt-get install cupsys
```

I edited /etc/cups/cupsd.conf and added:
```
  Allow 192.168.0.0/24
```

Under /admin; And the same under /

(The Server's IP Address is 192.168.0.70)
I browsed to:
[http://192.168.0.70:631](http://192.168.0.70:631)

I went to Administration, it auto-detected the printer, I installed the printer. I then found that CUPS did not have a driver for my printer, so I searched the web for one. I found one from this page:
[http://linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7350](http://linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7350)

I installed the PPD and added the printer successfully. I went to the Printer tab, started the printer, (also, the printer is physically on, has paper in it.)

I tried to print a test page from the "Print Test Page" button, and I find that the job is stopped. I read through /var/log/cups/error_log and here is the output:
```
E [07/Sep/2008:20:15:57 -0400] Filter "foomatic-rip" for printer "hp_photosmart_7350_USB_1" not available: No such file or directory
E [07/Sep/2008:20:18:13 -0400] Resume-Printer: Unauthorized
E [07/Sep/2008:20:18:54 -0400] PID 20242 (/usr/lib/cups/filter/foomatic-rip) stopped with status 2!
```

I am no printer tech, nor have been very successful at setting up printers before. Can someone please point me in the right direction from here? I've been trying to find some reading to do on CUPS, but documentation is lacking. Most of it is for GUI based stuff, but I don't have X on the server, so I am doing it all through the Web interface and SSH.

I would be very grateful if someone could direct me as to what I should do. I have had this printer hooked up to Ubuntu before, and it works out-of-the-box, so to speak.

Dr Small

---

### Post by Dr Small on 2008-09-08
I got the printer working, after much testing, and was searching through apt-cache for printing stuff and came across foomatic-db-hpijs.

So, here is what I did:
```
sudo apt-get install hpijs-ppds foomatic-db-hpijs
```

Then deleted the printer from the CUPS web-interface, add the printer, used the driver that I downloaded (the print driver that it found from the hpijs-ppds package, didn't want to install...) and got it setup. This time around, it didn't stop the jobs.

From there, I went around and setup all the linux machines to use this printer as the default (and only) printer. So now everything works and I am happy :)

Dr Small

---

