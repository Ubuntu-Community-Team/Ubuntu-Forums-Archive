---
title: "Disk Scan Hangs on Boot - RAID Setup"
date: 2009-09-10
forum: Server Platforms
---

### Post by pwebster25 on 2009-09-10
I have a 9.04 server running Apache and php,as a web server.  It has been stable and running well since early summer.  I have the desktop gui installed on it, as I am a bit of a noob with the command line (getting better).

I had to reboot the other day to correct a network connection problem and it started the automatic "routine check of drives" and then it hung up after very little progress.  It said it was scanning /dev/md3

I hard rebooted and had the same results.

If I ESC out of the scan the server works fine but it keeps coming back to this.  

I initially thought I really had a bad hard drive but I have done some routine checks and it appears that all 3 hard drives are functional and part of the RAID, per original setup.

I have my boot and "/" on RAID 1 setup (with 2 drives plus a spare).  These are Md0 and Md1 respectively.

I have my /home and /var on RAID 5 arrays with 3 drives (sda5, sdb5, sdc5, for example)
These are Md2 and Md3 respectively.

Could it be that the drives are fine but the scan is not able to handle the complex RAID arrays?

Could it be that these 3 SATA drives are not activated until after the scan initiates? (I have read references to this).  

Other somewhat pertinent details:  AMD 64 X2 processor; 8 Gig RAM, 3 X 500 Gig HDDs (All equal and SATA), All partitions are EXT3

This is likely the first time that the computer has done this disk scan, as it is rarely rebooted.

Is there a way to run this scan after logging in or from a live CD?  Should this scan work with a RAID array such as I have?

---

