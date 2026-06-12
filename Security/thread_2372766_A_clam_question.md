---
title: "A clam question"
date: 2017-09-28
forum: Security
---

### Post by jgw on 2017-09-28
I am running with Ubuntu 16.04.3 LTS \n \l

This is about clamtk. Below is a copy of my settings are the result of my last scan.  I seem to have 6 bad files.  My problem is knowing what I should do with them - and how to do it.  I should also mention that I also have 4 other scans, none of which found anything.  I have installed the clam daemon but have not invoked it. so these results are from clamav/clamtk (hopefully correct).  I suspect I can just delete the problems found in the cache and also, probably, the one found in deja-dup (backup data) as I recently changed that destination to another drive on the system.  I am also not sure how to get the program to move stuff to quarantine.

Thank you................

```
SizeLimit=1
ScanHidden=1
Recursive=1
Clickings=2
DupeDB=1
Thorough=1
Whitelist=
GUICheck=1
Update=shared
TruncateLog=1
Mounted=0
LastInfection=Never
HTTPProxy=0

/home/greg/.cache/mozilla/firefox/gootj2u5.default/cache2/entries/099C83595A0E73187C5052B1DC5BED19CEB4A0E9: PUA.Win.Trojan.Xored-1 FOUND
/home/greg/.cache/mozilla/firefox/gootj2u5.default/cache2/entries/CEA37DD5C606D81650C60BC734FB92D0DED9FC38: PUA.Win.Trojan.Xored-1 FOUND
/home/greg/.cache/mozilla/firefox/gootj2u5.default/cache2/entries/AC1FD878A990587A2F41E38914DAD2E5CFE4F33F: PUA.Win.Trojan.Xored-1 FOUND
/home/greg/Downloads/rpc420_setup.exe: PUA.Win.Trojan.Casino-141 FOUND
/home/greg/.config/libreoffice/4/user/basic/Standard/Module1.xba: PUA.Doc.Tool.LibreOfficeMacro-2 FOUND
/home/greg/deja-dup/duplicity-inc.20170504T101409Z.to.20170511T101450Z.vol488.difftar.gz: PUA.Win.Exploit.CVE_2012_1461-1 FOUND

----------- SCAN SUMMARY -----------
Known viruses: 6309476
Engine version: 0.99.2
Scanned directories: 2309
Scanned files: 209896
Infected files: 6
Total errors: 30
Data scanned: 6895.84 MB
Data read: 77277.45 MB (ratio 0.09:1)
Time: 2969.137 sec (49 m 29 s)
```

---

### Post by SeijiSensei on 2017-09-28
Just delete the files and move along.  You might want to consider the types of sites you're visiting if you've collected all these trojans while browsing.  

```
/home/greg/.config/libreoffice/4/user/basic/Standard/Module1.xba: PUA.Doc.Tool.LibreOfficeMacro-2 FOUND
```

This one might be a false positive.  Clam can be a bit aggressive when it comes to "[Potentially Unwanted Applications](https://www.clamav.net/documents/potentially-unwanted-applications-pua)".

---

### Post by jgw on 2017-10-03
Thank you for the reply.

I am going to just delete the files.  I got these on the 28th of September so I was probably doing something not good.  Thanks again!

---

### Post by Habitual on 2017-10-05
I've been known to  ```
rm -fr ~/.cache/
``` on occasion.

---

