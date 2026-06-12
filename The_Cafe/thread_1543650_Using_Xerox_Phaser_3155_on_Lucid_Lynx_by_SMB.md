---
title: "Using Xerox Phaser 3155 on Lucid Lynx by SMB"
date: 2010-08-01
forum: The Cafe
---

### Post by ddreamer on 2010-08-01
Hi, folks:
        To support Linux, I just bought the printer with Linux support. And it is also inexpensive. I come to share my experience of installation of Xerox Phaser 3155 printer because there was a small problem during installation.
       The printer is connected to a Windows machine by USB, and is shared. The SMB should be set ready. Within the attached CD, the driver is contained. I did as instructed by running

sudo Linux/install.sh 

after mounting the CD. Accordingly, the "Unified Driver Configurator" is installed. The driver I chose was "Xerox Phaser 3140 and 3155". However, the "Test Page" just couldn't be printed out.
        Please go to System/Administration/Print. Right-click on the printer and select "Properties". Select "Settings" in the left column and fill in the correct URL into the field following "Device URl". It is done. The field should have been filled by the "Unified Driver Configurator". It is a bug.

---

### Post by cmuxed on 2010-08-10
I have a Xerox Phaser 3110 and up until a year ago, I required a Samsung ML-1210 driver in order for it to work.  There was a bug logged for this and it fixed my issue: [https://bugs.launchpad.net/ubuntu/+source/foomatic-db/+bug/371737](https://bugs.launchpad.net/ubuntu/+source/foomatic-db/+bug/371737)__

---

### Post by ParkyZA on 2010-09-30
Hey DDreamer, 

Thanks for the info. Solved my problem.  I downloaded the tar.gz driver file from the Xerox website and have been pulling hair out as I could not install it.  Other thing is that the "device Url" was filled on mine and worked first time, 

Thanks

PS. I have the Phaser 3140.

---

