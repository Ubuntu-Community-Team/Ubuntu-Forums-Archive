---
title: "Sane scan server - HP Photosmart c4240"
date: 2012-08-09
forum: Server Platforms
---

### Post by kpuz on 2012-08-09
I am having some trouble with getting the scanning functionality of my all-in-one scanner to work using saned daemon.

I have set up the saned server on my home server and am able to connect to the scanner. But after I start scanning, the scanner doesn't do anything.
I had to change the hp4200.conf file in the /etc/sane.d/ folder to match the vendor and product id of the printer.

The scanner works if I connect it directly to my laptop but it may be using HPLIP and not sane.

Has anyone been able to get this scanner to work as a network scanner? Is there something I am missing? would it be better to set up hplip on my server to use the scanner functionality.

---

### Post by ajgreeny on 2012-08-09
Do you have a gui on the server, or is it command line only?

I don't think it will matter as far as your comment about sane is concerned; my understanding is that all servers make use of sane and will not work without it, hplip just gives you the appropriate drivers for your machine, and ifg you have a gui desktop, hplip-gui gives you a great way to control and configure your printer/scanner.

---

### Post by kpuz on 2012-08-10
No I only use command line to set up the server.
I'm going to try setting up hplip using command line to set up a network scanner.

---

