---
title: "Running Devices not supported in linux in WIndows via VM?"
date: 2011-01-19
forum: Virtualisation
---

### Post by MasterNetra on 2011-01-19
I was wondering, I have a jWin Webcam and a Lexmark 2350 printer, neither which runs in Ubuntu...well the webcam kinda sorta does, cheese manages to get some use out of it, barely though as the feed is upside down and of extremely poor quality and doesn't run with skype (in ubuntu) or on the web but meh. The printer not at all as their is no driver for it. So I was wondering could windows in a VM make use of the despite Ubuntu not being able to? Or would Ubuntu have to be able to use them to some degree?

---

### Post by gordintoronto on 2011-01-19
Since the webcam is probably an USB device, you would need to install the version of VirtualBox from the Oracle web site, not the one in the repositories. There's another step involved in using the USB, but I forget the details; Google can find it for you. It should work, though.

Probably the printer, too.

---

### Post by MasterNetra on 2011-01-25
> **gordintoronto said:**
> Since the webcam is probably an USB device, you would need to install the version of VirtualBox from the Oracle web site, not the one in the repositories. There's another step involved in using the USB, but I forget the details; Google can find it for you. It should work, though.

Probably the printer, too.

I hope. The printer is USB too.

---

### Post by HermanAB on 2011-01-26
Yup, that will work, but VMware Player may be less hassle, since it has support for USB built in.  

The main problem with VMware is that their support for new kernels frequently lags the Linux release cycle.  Using Vbox, you can compile from source to get around that problem.

---

