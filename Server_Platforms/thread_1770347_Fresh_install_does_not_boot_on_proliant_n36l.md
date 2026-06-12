---
title: "Fresh install does not boot on proliant n36l"
date: 2011-05-29
forum: Server Platforms
---

### Post by Captaincrash on 2011-05-29
Hello folks I am currently trying to gat a copy of ubuntu server 11.04 to run on my new proliant n36l with the std 250gb hdd as boot and 2 2tb in hardware raid 1.  
Steps I have gone though, first attempt at an install I used a full cd variant on usb stick using the universal usb installer this came up with an error nu cd in drive.  So I moved onto using unetbootlin, this presented the same error in std iinstall but moving to expert it worked fine till it came to install grub which it had a fatal error on I tried lilo but on boot it could not find /dev/hdb, 10.  I assumend it was a bad disc image so I moved on to the net version whicih is where I am at now.  The install went fine but the machine now sits with a flashing cursor, I have tried turning off the raid which was suggested on other threads, I was curious that grub could haev been put on the stick even if the installer was told to put it on the hdd, when the stick is present I get a flashing cursor followed by my monitor going to sleep with the machine still runnning.

I am a bit of a specialist install noob so any suggestions will be welcome.

Cheers

---

