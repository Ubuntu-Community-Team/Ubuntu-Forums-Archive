---
title: "Hacker Encrypts Hard Drive"
date: 2016-03-27
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2016-03-27
If one dual boots Windows and Ubuntu using separate partitions (ntfs for windows and ext4 for ubuntu) what happens if a hackers encrypts the hard drive via the windows environment?  Is only the windows partitions locked out/encrypted or the whole disk?

---

### Post by mikewhatever on 2016-03-27
This is too general, but, in case someone has admin access to Windows, it would be possible to encrypt all partitions. Some may say that Windows can't read linux partitions by default, but, there are drivers for that, and a stranger having admin access can alter the defaults anyway.

---

### Post by buzzingrobot on 2016-03-27
It would depend on the intent, skills and interests of the person who wrote the software doing the encryption. The crypto-ransom malware victimizing Windows users is a criminal money making effort.  Linux partitions are not invisible to Windows.  The partition itself is visible.  It's just that Windows isn't equipped to read the Linux file systems used on those partitions. A malware developer could add the capability to read Linux filesystems. Or, perhaps, do the encryption at a "bare metal" level.  But that seems, as usual, a bad investment of time and resources given the small Linux user population. 

Simply deleting a Linux partition wouldn't be difficult. Nor would writing zeros over the partition, given enough time.

---

### Post by coldraven on 2016-03-27
AFAIK A more likely scenario is that a compromised Windows PC is connected to a Linux network. The malware is just searching for file extensions like .doc, it won't see that they are connected by Samba. That is to say the malware will just see folders full of files and not the underlying file system.

---

