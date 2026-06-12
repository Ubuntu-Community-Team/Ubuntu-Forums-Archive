---
title: "Dell Precision 7510 BIOS did not recognize second drive"
date: 2017-01-20
forum: Ubuntu, Linux and OS Chat
---

### Post by sourcelibre on 2017-01-20
I ordered a Precision 7510 with two SSD hard drives (UBUNTU 14.04).  When I received the machine, the BIOS did not recognize the second hard drive. This link shows the BIOS screen for a two-hard drive machine ([http://www.dell.com/support/article/us/en/4/SLN302095](http://www.dell.com/support/article/us/en/4/SLN302095)).  I worked with Dell&#8217;s Pro-Support Team. (A great team and worth the extra cost.)  Pro-Support thought it might be a bad motherboard and sent me a second machine to try.  I had the exact same results - BIOS did not see the second drive.

In addition to BIOS not recognizing the second drive, the machine would not boot from the USB port without the recognized hard drive being disabled.

Dell&#8217;s team concluded that the problem could not be fixed over the phone and had me send the machines back.  They were sending the issue to Engineering.

Anyone have a similar experience?



Btw: I like Dell and think their Pro-Support Team is the best.  Their Pro-Support Team has made them a leader in a very similar product and competitive industry.

---

### Post by oldfred on 2017-01-20
Were these new M2 drives the NVMe type?

Not sure if 14.04 fully supported them. As back then they were still fixing support.
But Dell usually is good about making sure drivers are added back in with its own Sputnik.
And usually those drivers are later included in a newer Ubuntu version.

       gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
Filesystem support
[URL="http://ubuntuforums.org/showthread.php?t=2318570"]http://ubuntuforums.org/showthread.php?t=2318570
[/URL]
 Support for NVMe in grub-mkdevicemap fixed in 2014
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162) 

[URL="http://ubuntuforums.org/showthread.php?t=2318570"]
[/URL] 
 Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)

---

### Post by sourcelibre on 2017-01-21
UBUNTU 14.04 (shipped on Primary SSD hard drive) recognized the second drive. I used gparted to format and partition the second drive, even labeled it.   However, the Phoenix boot BIOS firmware did not recognize the second drive. (Thus, I could not enable or disable the second drive nor would the machine boot from the USB ports with the primary drive enabled.)  

The USB ports would not boot FREEDOS, USB Live Linux OS (Mint, Debian, UBUNTU) or a Windows recovery DVD if the primary drive was enabled. (The primary drive was the only BIOS visible drive.) With the primary drive disabled all the previously mentioned OSes booted from the USB port.

Dell did not think it was a Linux-related problem since it would not even boot from the USB port but was either a BIOS firmware, motherboard, or SSD problem. 

The ProSupport Team was surprised that others have not reported this problem, though, I have noticed more problem reports about the 7510 on the Dell community site since January 1. Dell concluded it was a problem with the 7510 and wanted it back for engineering analysis.

Has anyone else had this problem?

---

### Post by sourcelibre on 2017-01-22
Machine sent to Dell engineering for analysis

---

### Post by wildmanne39 on 2017-01-22
For future reference to mark a thread solved just click on thread tools at the top of the page and click solved.

Never mind threads in this forum can not be marked solved.
Thanks

---

