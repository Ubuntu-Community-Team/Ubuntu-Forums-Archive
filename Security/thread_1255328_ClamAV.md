---
title: "ClamAV"
date: 2009-09-01
forum: Security
---

### Post by OnlyTim on 2009-09-01
Hi all, Still a newbie in the Ubuntu world so bare with me.  I just installed the clam - daemon antivirus to use for emails and such. I can verify that the program is in using the version command, but when I tried to do a manual scan using ( clamdscan) I get the following permission error.

Thanks gang.


/home/tim: lstat() failed: Permission denied. ERROR

----------- SCAN SUMMARY -----------
Infected files: 0
Time: 0.003 sec (0 m 0 s)

---

### Post by Baneblade on 2009-09-01
> **OnlyTim said:**
> Hi all, Still a newbie in the Ubuntu world so bare with me.  I just installed the clam - daemon antivirus to use for emails and such. I can verify that the program is in using the version command, but when I tried to do a manual scan using ( clamdscan) I get the following permission error.

Thanks gang.


/home/tim: lstat() failed: Permission denied. ERROR

----------- SCAN SUMMARY -----------
Infected files: 0
Time: 0.003 sec (0 m 0 s)


Have you tried running it as root?
eg:  " sudo clamdscan "

---

### Post by denver on 2009-09-01
try something allong the lines of:

```
clamscan -r ~/
```

This will scan your entire home folder.

---

### Post by OnlyTim on 2009-09-01
Thanks for the reply all. The Sudo command still gave me the permission error, but the clamscan -r ~/ did the trick! It did an entire system scan. 

My last question is; will it now automatically scan for a mail virus on my email? I'm using Evolution.

Thanks again for the help.

---

### Post by denver on 2009-09-01
ClamAV is an on-demand scanner. It only scans what you tell it to scan. Seeing as there are verry few virii for linux, and even less that actually do something other then existing, your only concern should be not to infect your friends that actualy use windows (for some reason).

There are ways to integrate ClamAv into evolution, if you think its worth the effort. Here are a few examples:

[http://www.theopenstandard.com/blogs/chapeaurouge/?p=70](http://www.theopenstandard.com/blogs/chapeaurouge/?p=70)
[http://tuxtraining.com/2008/11/30/evolution-virus-scanning](http://tuxtraining.com/2008/11/30/evolution-virus-scanning)

Good luck!

---

### Post by OnlyTim on 2009-09-01
I'll give it a go! 

Thanks for the info!

---

