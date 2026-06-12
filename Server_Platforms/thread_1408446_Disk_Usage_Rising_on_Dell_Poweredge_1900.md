---
title: "Disk Usage Rising on Dell Poweredge 1900"
date: 2010-02-16
forum: Server Platforms
---

### Post by Trekker6.5 on 2010-02-16
Hi
 
I am running Ubuntu 8.04LTS x64 on a Dell Poweredge 1900 with a Perc 5i RAID Controller. There are 3 500Gb SAS drives in a RAID 5 configuration. The Kernel is Linux dtpfs 2.6.24-27-server #1 SMP Wed Jan 27 23:39:33 UTC 2010 x86_64 GNU/Linux
 
Approximately once every 1 - 2 months I have a problem where the disk usage starts to rise for no apparent reason. When I run df the usage grows steadily over 2-3 days from 26% to 100%. At this point Samba reports that the disks are full.
 
Baobab does not report the additional usage and the tape backup ignores the 'extra' usage and just backs up what was previously there.
 
When I reboot the machine the usage is set back to normal and we can continue.
 
Has anybody else come across this problem?
 
Thanks for any help you can offer.
 
Jon

---

### Post by lukjad on 2010-02-16
Hm... Well, I had something similar happen to me with a much smaller hard drive. Every day the computer would start to slowly fill up to the poitn where nothing would work. When I would reboot, all would be fine for a few hours, then it would start again. When I booted to a live CD the hard drive was not even half full and there was no reported virus or spyware activity. 

What had happened was that I had ticked off a "Log to hard drive" option on a diagnostics program I had been testing and so it logged every action I did ot the hard drive and automatically deleted itself on shutdown. 

Since a little while before this problem started, is it possible you were doing anything similar?

---

### Post by Trekker6.5 on 2010-02-16
Thanks very much for your reply.

The disk usage remains static for quite a while and then will rise rapidly in the space of a day or so. I haven't added any new software or altered any settings.

When I run du on the system there are no suspiciously large files, just an absence of space.

Thanks again for any help you can offer.

---

