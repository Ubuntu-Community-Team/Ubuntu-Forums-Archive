---
title: "clamscan -- what to do with all the false positives"
date: 2013-05-16
forum: Security
---

### Post by Rebelli0us on 2013-05-16
I get about 100 Windows system files that show up as Trojans, example:

```
/media/ext4/Backup/Archive/Hardware/Networking/Cisco-Linksys WPC54G Wireless-G Notebook Adapter/WPC54Gv3_V1[1].0.4.4,0/WPC54Gv3_V1.0.4.4/BCMLib/AegisE5.dll: Win.Trojan.Fakesmoke-117 FOUND

```

I could add --exclude=REGEX but the command line would become enormous.

Is there a convenient way to whitelist files?

---

### Post by SeijiSensei on 2013-05-16
Unfortunately these kinds of false positives seem to be par for the course with ClamAV.  I attribute it to the fact that anyone can post virus signatures, and the review process, based on volunteer help, seems less than stringent.  We use SquidClamAV to scan every web object and get false positives from legitimate sites like WindowsUpdate and HP all the time.  I suspect, without any proof, that there are a number of anti-MS types who report as trojans things like bundled installers for other software packages.  In these cases, ClamAV is often the only scanner who reports these items as trojans, which raises my suspicions about the submission and review processes.

For example, in late March the scanner reported that a file from windowsupdate.com contained "Win.Trojan.Rbot-90."  However ClamAV is the only scanner that reports this file's signature as a trojan:  [http://r.virscan.org/311f07b90d67b3fe7778ef9aff0ab807](http://r.virscan.org/311f07b90d67b3fe7778ef9aff0ab807). This is not the only instance of a trojan allegedly being found in a file from WindowsUpdate either.  Obviously if Microsoft were distributing update files with trojans in them, it would have been all over the tech news pages long ago.  

I don't see any solution to this problem, nor, unfortunately, do I see an easy whitelisting method either.  Unlike programs like rsync, clamscan doesn't seem to support using inclusion and exclusion lists stored in a text file.

---

### Post by Rebelli0us on 2013-05-16
Thank you. It looks like they consider Microsoft Internet Explorer to be Trojan as well:

```
/media/w7/Windows/winsxs/wow64_microsoft-windows-i..etexplorer-optional_31bf3856ad364e35_8.0.7600.16385_none_19ba3f8a72d988f3/iexplore.exe: Win.Trojan.Bamital-996 FOUND
```

Is there a better virus scanner for Linux? I think malware in Linux OS is very unlikely, I'm more concerned with Windows and Windows VMs. ClamAV will check VMs as long as they're running if you specify  ~/.gvfs/

---

### Post by SeijiSensei on 2013-05-16
There are commercial scanners available for Linux from places like [Kaspersky]("http://www.kaspersky.com/products/business/applications/endpoint-security-linux").

---

### Post by Rebelli0us on 2013-05-17
I'm trying AVG, no false positives so far. I have Windows VMs running and mounted but I'm getting "permission denied". Any ideas?

```
sudo avgscan ~/.gvfs   
AVG command line Anti-Virus scanner
Copyright (c) 2013 AVG Technologies CZ

Virus database version: 3162/6331
Virus database release date: Fri, 17 May 2013 06:16:00 -0400

/.gvfs  **Object scan failed; Permission denied**
```

---

