---
title: "Raring Ringtail - Install hangs before disk selection Window"
date: 2012-11-29
forum: Ubuntu Development Version
---

### Post by shanp on 2012-11-29
i downloaded Raring Ringtail from the build page, but no success on install, it always hangs before showing the disk selection window, any suggestion please.

Disk: 250GB SSD and 500GB HDD 

regards
Shan A

---

### Post by rjw1678 on 2012-11-29
I have the same problem. My system board is a ASUS M4A89GTD-PRO/USB3 , CPU is Phenom II 1100T x6 , 16GB Memory,  drive SDA is 120GD SSD for Windows 7, drive SDB is 240GB SSD for Ubuntu 12.04.1 LTS, drive SDC is 115GB SSD for Ubuntu 13.04, video is ATI Radeon HD 4290. Ubuntu 12.10 installs fine on drive SDC - but Ubuntu 13.04 install always hangs before disk selection Window.

This is with the amd64 Ubuntu 13.04.

There is already a bug report in launchpad for this problem it is Bug # 1080701. I added myself as being affected by it.

Thank You,
Bob W.

---

### Post by bird1500 on 2012-11-29
Same issue, I thought it's just me, [here's the bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701").

---

### Post by grahammechanical on 2012-12-01
I get as far as the second purple screen (with the white dots) and it drops to a Busybox command line with the error message: Unable to find a medium containing a live file system. I found this old bug which I added to

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/817145]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/817145")

I have had this bug on the daily ISO images on 26th, 27th, 29th and now 1st December. I only reported it today because I spent a lot of time trying to get useful information to add to the report.

Regards.

---

### Post by howefield on 2012-12-01
> **shanp said:**
> i downloaded Raring Ringtail from the build page, but no success on install, it always hangs before showing the disk selection window, any suggestion please.

Disk: 250GB SSD and 500GB HDD 

Same issue, (only 120GB SSD and 1TB HDD) installing to sdb3 on the SSD but would only proceed if HDD was disconnected.

---

### Post by jerrylamos on 2012-12-01
Had this hang before partition selection menu about a week ago.  Got around it by doing sudo apt-get update, sudo apt-get dist-upgrade on the live session, then install worked O.K.  

Fine on a 2 GB pc, the upgrade crapped out on the 1 GB pc running out of space.  Install worked O.K. anyway.

Of course, even though you've done an update, after install you get to update the install all over again.....

---

### Post by crepito on 2013-03-02
> **jerrylamos said:**
> Had this hang before partition selection menu about a week ago.  Got around it by doing sudo apt-get update, sudo apt-get dist-upgrade on the live session, then install worked O.K.  

Fine on a 2 GB pc, the upgrade crapped out on the 1 GB pc running out of space.  Install worked O.K. anyway.

Of course, even though you've done an update, after install you get to update the install all over again.....


This happened to me today when trying to install 13.04 in my ssd and the tip above solved my issue. I was using the daily build for today. Thank you.

---

### Post by cole.mickens on 2013-03-02
I reported this. Is it the same? [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1120938](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1120938)

---

### Post by crepito on 2013-03-02
Yeah its the same issue. I posted a comment there with my experience in the matter.

---

### Post by P-I H on 2013-03-02
Perhaps this bug relate to the same problem
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

---

### Post by bmarsh on 2013-03-22
Just got stuck with the same problem (tried 3 times) on an i386 machine.   Finally got it to go by using all the options at boot time.  (noapic, etc)

---

### Post by monkeybrain2012 on 2013-03-22
Just encountered the same problem. Jerrylamos' tips in post #6 solve the problem. Now the installer is running.

---

### Post by rjw1678 on 2013-03-24
Tried mounting all partitions except for my 3rd hard drive(which did not have any partitions).
Said 'no' when the installer asked if it wanted me to let it unmount the partitions.
Then the install worked and now I have 13.04 64bit on my 3rd hard drive.
Thanks for all your info everyone.

 Bob W.

---

