---
title: "Webcam Issues with 3.2 kernel"
date: 2011-12-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TenPlus1 on 2011-12-12
I have a Logitech CS160 usb webcam that works perfectly in Ubuntu 11.10 with the 3.0 and 3.1 kernels but after upgrading to the 3.2 kernel it stopped working even on my test machine running Ubuntu 12.04...  This seems to be a kernel issue...

Bus 001 Device 006: ID 046d:0824 Logitech, Inc. 

Just thought you ought to know incase any other cams are not working as they should...

---

### Post by TenPlus1 on 2011-12-13
Sadly no, it involves using the webcam with  any cam program like cheese, guvcview, skype etc.  Everything works perfectly in 3.0 or 3.1 kernels but in 3.2 a black screen appears or in the case of guvcview a black screen appears then closes...

---

### Post by xyzzyman on 2011-12-14
My notebook's built-in Suyin based Acer CrystalEye webcam does the same thing with the 3.2 kernels, whether in oneiric or precise, compiled by ubuntu or custom compiled w/ubuntu's patch or from kernel.org. The latest build or so was supposed to fix it, but the latest kernel does not like my system to even try. I even tried a fresh precise install, and soon as you install the nvidia binaries driver, whether from nvidia or through jockey, it dies during boot. Don't have time to troubleshoot at the moment though.

---

