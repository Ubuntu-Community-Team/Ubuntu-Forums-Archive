---
title: "bizzaro clamav error"
date: 2018-03-03
forum: Security
---

### Post by espectro2 on 2018-03-03
I came across very strange error using clamav
it  can not read some files from my hd presents error reading my iso can  not be corrupted someone remotely controlling the machine saving some  file inside my hd that clamav can not read?
Before I ask was using the command sudo clamscan -r / I did not enable root I am using sudo.
I already gave apt-get dist-upgrade did not upgrade to version 0.99.4
---------- SCAN SUMMARY -----------
Traditional viruses: 6418260
Engine version: 0.99.3
Scanned directories: 36606
Scanned files: 129603
Infected files: 0
Total errors: 19083
Data scanned: 4443.54 MB
Data read: 5238.83 MB (ratio 0.85: 1)
Time: 1668.546 sec (27 m 48 s)

----------- SCAN SUMMARY -----------
Known viruses: 6418260
Engine version: 0.99.3
Scanned directories: 36346
Scanned files: 129619
Infected files: 0
Total errors: 19109
Data scanned: 5130.32 MB
Data read: 5810.97 MB (ratio 0.88:1)
Time: 1797.831 sec (29 m 57 s)

---

### Post by monkeybrain20122 on 2018-03-04
clamav is notorious for false positive and it scans for Windows viruses. It is pretty much garbage that takes up space and resource. You don't need Anti-virus on Linux.

---

