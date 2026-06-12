---
title: "REvisited: Issues Connecting DLP-RFID1 (USB RFID Reader/Writer) in RFDump / RFIDIOt"
date: 2009-05-27
forum: Security
---

### Post by JKX on 2009-05-27
This is referring to this post: (it is now in read only mode)

[http://ubuntuforums.org/showthread.php?t=701402]("http://ubuntuforums.org/showthread.php?t=701402")

I am the original poster. To anyone who replied to the original post, I'm very sorry for the extremely late reply. I've been away from the forums for quite some time due to the RW getting in the way of things.. Regardless, for those that are still interested (or those that are just stumbling upon this post for the first time) in how I was able to get the DLP-RFID1, RFID Reader/Writer to work properly (in Ubuntu 7.10; I don't know if this issue has been acknowledged in previous releases), attached is a .zip file with a PDF guide/howto. It outlines all the steps I took to get the reader/writer to function properly. 

Again, this is late, but I hope it helps you find the light at the end of your tunnel !!

Cheers,

JKX

---

### Post by palisv on 2009-07-11
Hi,

I have followed your instructions and got everything setup as that, with a working kernel and FTDI driver that detects the DLP-RFID1 on ttyUSB0.

But the rfdump wont work anyway, it complains about that i cant find the RFID reader, what is the baud rate? 

The rfdump I use is version 1.6.

---

### Post by coolnumber9 on 2010-03-16
Hi JKX,

First of all, thanks for sharing DLP-RFID1 Linux mapping guidelines.

Have you ever got [DLP-RFID1]("http://www.dlpdesign.com/rf/rfid1.shtml") working in Ubuntu? I was not able to successfully communicate with the device using RFDump and RFIDiot. Since the device uses an [FTDI]("http://www.ftdichip.com/") chip controller, I went ahead and created a simple program using [libftdi]("http://www.intra2net.com/en/developer/libftdi/index.php"). I was able to send and receive data. However, when reading the tag data from the buffer, the UID and the data written in the user memory seems to be erroneous. No problem encountered in Windows.

What seems to be the problem here? Any tips will be highly appreciated.

Thanks!

coolnumber9

---

