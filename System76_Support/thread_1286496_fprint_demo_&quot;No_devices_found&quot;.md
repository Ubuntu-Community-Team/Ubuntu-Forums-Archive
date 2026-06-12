---
title: "fprint demo &quot;No devices found&quot;"
date: 2009-10-09
forum: System76 Support
---

### Post by HotShotDJ on 2009-10-09
After doing a complete reinstall (Jaunty AMD64) and restore (System76 Driver Restore, reboot, system76 Driver Install), I attempted to enable the fingerprint reader.  I found that the software was not installed, so I installed fprint-demo, libpam-fprint, and libfprint0 (I think that was pulled in from libpam-fprint).  After following the Knowledge76 instructions on enabling it, I fired up fprint project demo, which reports "No devices found."  I also tried installing libusb-1.0-0 to no effect (I forget where I read that it should be installed).

This is with a PanP5.

---

### Post by thomasaaron on 2009-10-09
Try deleting anything you installed and then running the Restore functionality of the System76 Driver. It should install everything you need.

I've got this slated for testing to today.

---

### Post by thomasaaron on 2009-10-09
OK. I just verified that the fingerprint reader tutorial works perfectly on a freshly imaged machine (64-bit Ubuntu).

---

### Post by HotShotDJ on 2009-10-09
> **thomasaaron said:**
> Try deleting anything you installed and then running the Restore functionality of the System76 Driver.
> **thomasaaron said:**
> OK. I just verified that the fingerprint reader tutorial works perfectly on a freshly imaged machine (64-bit Ubuntu).Thank you for checking that for me.  I thought I did everything correctly, but I must have made an error somewhere along the line.  I'll work on it over the weekend.  Thank you for your fast reply!

---

### Post by HotShotDJ on 2009-10-09
I did a complete reinstall to rule out any stupid errors on my part and followed the instructions at [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System) exactly as written.  Still no joy with fprint.

I let the hacker-wannabe in me overrule my better judgment and started poking around in /opt/system76 and found the fprint.py script.  I began testing the commands in that file and discovered that it was failing with this line:```
sudo apt-get install --assume-yes build-essential libtool automake1.9 libssl-dev libgtk2.0-dev libmagick++9-dev libpam0g-dev
[sudo] password for hotshotdj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmagick++9-dev is a virtual package provided by:
  libmagick++-dev 7:6.4.5.4.dfsg1-1ubuntu3.1
You should explicitly select one to install.
E: Package libmagick++9-dev has no installation candidate
```so I changed "libmagick++9-dev" to "libmagick++-dev" and then ran System -> Administration -> System76 Driver to restore again.  SUCCESS!

Now, I just need to practice using the fingerprint reader -- so far, it hates me... I've only gotten it to work with the enrolled finger one time. :)

---

### Post by thomasaaron on 2009-10-12
Excellent sleuthing. I've not seen that happen before.

Yes, the reader software is VERY finicky. Worse than any cat you've ever seen.

---

