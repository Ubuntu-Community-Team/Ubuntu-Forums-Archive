---
title: "Avast and Metasploit"
date: 2009-05-29
forum: Security
---

### Post by ixpl on 2009-05-29
Hey everyone, So I installed the Avast scanner and ran it the other night. All was well with ubuntu not having viruses and such (as usual) until it got to my framework-3.2 directory. It put about 20 exploits in the vault calling most of them trojano. Now I wouldn't be concerned about this as metasploit is basically a database of pre-written malicous script, but when i did the svn update it came back with a invalid certificate. The md5 checked out it was the expiration date that was different. After some online research i decided to take the update. Has anyone had this encounter or have any advice?  Thanks

---

### Post by cariboo on 2009-05-29
You're running into problems, because most virus scanners only search for Windows viruses, unless you are running an email server, there really is no need to run a windows virus scanner. As far as I recall clamav is the only scanner that checks for Linux malware, which is essentially useless, as at this moment there are no Linux malwares in the wild.

---

