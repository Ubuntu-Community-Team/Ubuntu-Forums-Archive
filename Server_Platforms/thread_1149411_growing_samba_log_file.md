---
title: "growing samba log file"
date: 2009-05-05
forum: Server Platforms
---

### Post by Panos on 2009-05-05
Hello all,

Every few weeks, my server comes to a hault because the disk gets full of a single samba log file, which exceeds several gigabytes.

Before continuing my story, I should mention that in smb.conf I have set the option for the log file size to 1000 (I think this corresponds to 1 MB).

Yesterday, I was lucky to notice this behavior while I was logged in to my server through ssh. I was issuing df -h and indeed the root directory was starting to add several GBs. I thought I could prevent the full disk problem by simply deleting all samba log files, but to my surprise the / directory kept growing in size, although the few log files that appeared in the clean /var/log/samba directory seemed to have zero size. The only solution was to reboot the server. Before rebooting, the / directory was full at 80%, but after rebooting it returned to its normal 26%.

I run Ubuntu 8.04 LTS 64bit, on an Athlon x2 CPU with 8 gigs of RAM.

Any ideas would be very much appreciated.

Thanks.

Panos

---

### Post by Panos on 2009-05-06
A gentle bump :-)

---

### Post by capscrew on 2009-05-06
> **Panos said:**
> Hello all,

Every few weeks, my server comes to a hault because the disk gets full of a single samba log file, which exceeds several gigabytes.


What file specifically are you referring to?  What is in it?
> 

Before continuing my story, I should mention that in smb.conf I have set the option for the log file size to 1000 (I think this corresponds to 1 MB).


Yes 1000 KB is a 1 MB.
> 

Yesterday, I was lucky to notice this behavior while I was logged in to my server through ssh. I was issuing df -h and indeed the root directory was starting to add several GBs. I thought I could prevent the full disk problem by simply deleting all samba log files, but to my surprise the / directory kept growing in size, although the few log files that appeared in the clean /var/log/samba directory seemed to have zero size. 

Must be something else.  Maybe a /tmp file?
> 
The only solution was to reboot the server. Before rebooting, the / directory was full at 80%, but after rebooting it returned to its normal 26%.
This sure sounds like a /tmp file that is not being regularly deleted via a cron script.  All /tmp files are normally deleted on a reboot.   
> 


I run Ubuntu 8.04 LTS 64bit, on an Athlon x2 CPU with 8 gigs of RAM.

Any ideas would be very much appreciated.

Thanks.

Panos

---

### Post by Panos on 2009-05-06
Hi

> **capscrew said:**
> What file specifically are you referring to?  What is in it? 

It's a regular log file from my windows machine (log.pc_name). Under normal circumstances, the file doesn't contain anything suspicious, just normal event logs. However, I haven't managed to examine it when the problem occurs to see what gets logged.


> Yes 1000 KB is a 1 MB.

LOL, I know. I wasn't sure if 1000 refers to bytes or kilobytes and obviously I didn't make it clear :-)

> Must be something else.  Maybe a /tmp file?
This sure sounds like a /tmp file that is not being regularly deleted via a cron script.  All /tmp files are normally deleted on a reboot.

As long as I can remember I was also checking the /tmp directory for growing files when the problem occured, but didn't notice any huge files.

I have had this problem since I set up my server a year ago but couldn't find any solution. I found a few posts in google that were mentioning that this may occur due to a kernel bug but couldn't find further info (but then again, I have upgraded my kernel a few times so I suppose that it would have been fixed).

Anyway, thanks for your reply.

---

