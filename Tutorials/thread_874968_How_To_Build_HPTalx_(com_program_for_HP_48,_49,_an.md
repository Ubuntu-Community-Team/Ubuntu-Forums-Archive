---
title: "How To: Build HPTalx (com program for HP 48, 49, and 50 series calculators)"
date: 2008-07-30
forum: Tutorials
---

### Post by picopir8 on 2008-07-30
I recently tried to build this program and ran into a few problems so I thought I would write this brief tutorial to help others avoid the problems that I ran into.

The following procedure has been verified with HPTalx 1.3.1a and Ubuntu 8.04 (both 32 and 64 bit).

1) Download and extract the latest version of HPTalx.  
[http://hptalx.sourceforge.net/download.shtml](http://hptalx.sourceforge.net/download.shtml)

2) Extract the file, then open a terminal window and cd to the extracted directory (hptax-1.3.1a)

3) Get packages needed to build HPTalx
```
sudo apt-get install build-essential libglib2.0-dev libgtk2.0-dev libxml2-dev
```

4) Get packages needed to run HPTalx once compiled
```
sudo apt-get install libsocksd openbsd-inetd ckermit
```

5) Run configure script
```
sudo ./configure
```

6) Build HPTalx
```
sudo make
```

7) Install HPTalx
```
sudo make install
```

8) Load hp4x module
```
modprobe hp4x
```

9) Launch HPTalx
```
hptalx
```

10) Click File-Setup and configure HPTalx for your connection interface

11) Put your calculator in server mode (see calculator manual or HPTalx manual/README)

12) Click Connect-Connect (or Ctrl-B) to connect to your calculator.

---

### Post by tweezak on 2012-05-26
Man, you rock! Thank you for creating this! Here it is 4 years later and I'm trying to connect to my old HP48GX calculator with a funky USB-Serial adapter cable.

Everything you wrote worked except in my version of ubuntu (Natty) I had to use libsocksd0 instead of libsocksd.

Also, the modprobe command returned an error but the process still worked in the end.

Oh...by the way...if someone reading this needs to install a USB-serial adapter there are excellent instructions here:

[http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html](http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html)

Thanks again!

---

