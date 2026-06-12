---
title: "Using Clamav via CLI"
date: 2007-09-09
forum: Server Platforms
---

### Post by dynamethod on 2007-09-09
hey there

ive looked and looked, so i apologise if there is information regarding what im about to ask, 

but ive dl and installed clamav succesfully, and updated

the reason i have need for this AV is to scan my windowsxp partition(ive got windowsxp and ubuntu on the same HD)

im finding it hard to get any information about the CLI commands for clamav however, 

i tried clamscan -h

and therefore tried :
sudo clamscan /media/Mothersuperior(my win partition) -i -l Scan_Rep

but the scan is really random :S

sometimes it scans 5 directorys, sometimes 10, sometimes only 1!?

i have 20 gigs of data that needs to be scanned, can someone please tell me what im doing wrong?

im trying to complete a scan and log the results and particularly any infected files that have been discovered, 

so again, if ive failed to "rtfm" im sorry, just finding it hard to find this out :S

*EDIT* ive just tried:
sudo clamscan /media/Mothersuperior -r -i -l Scan_Rep
now it seems to be scanning all subdirectorys, although if someone reads this post and thinks i may using commands that will not achieve what i need, please say so, thanks again

---

### Post by rfruth on 2007-09-09
The Ubuntu Wiki has lots of info about clamav [https://help.ubuntu.com/community/ClamAV]("https://help.ubuntu.com/community/ClamAV")

---

### Post by syadnom on 2007-10-09
your only scanning the directory.  you need to do

clamscan -r /path/to/scan -i -l scanresults.log

the '-r' means recursive, now it should dive into the directories below /path/to/scan

---

